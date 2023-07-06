---
title: Proximity Search for Startup Developers
description: A How-To on the different methods for solving proximity search.
image_link: "https://i.pinimg.com/736x/f1/16/46/f116465b3e01bf36d6d04773a0da8095.jpg"
parent: Blog
date: 2023-06-30
---

![]({{ page.image_link }})

# Proximity Search for Startup Developers

---

{: .info }
I use MacOS and only MacOS so all examples will be for MacOS.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

Hypothetical
> You are a software engineer at a startup with access to your customer’s addresses. You have been asked to evaluate a solution to a product ask: **Searching for other addresses near an address qualifier**. 

I’ll spend some time pulling apart the different levels of product complexity and then providing some instructions on how to solve these with minimal effort - a goal for which all engineers should strive.

---
## The Problem
As with most requests from customers, clients, or product, the scope can be nebulous and expand quickly. What was presumably a single ticket can easily expand to entire feature lanes so it’s important (especially as a startup engineer) to cut scope where possible. 

This ask is no exception. For the intents of this situation though, let’s assume we have a decently-scoped product spec.

>  - Proximity Search: given an address qualifier and a proximity bound, find all customer addresses within the region + the proximity bound
>  - Radius Search: given an address qualifier and a radius, find all customer addresses within the radius from the centroid of the region
>  - Assume US postal codes only
> -  REQUIRED: For regions whose granularity is **greater than or equal to** a 3-digit zip code, use **Radius Search**
>  - NICE TO HAVE: For regions whose granularity is **less than** a 3-digit zip code (e.g.. county or state), use **Proximity Search**.
>  - NICE TO HAVE: Accuracy **97%** or higher
>  - NICE TO HAVE: Proximity search on all address qualifiers:
>    - Full Address
>    - 3-digit zip
>    - 5-digit zip
>    - 9-digit zip
>    - County
>    - State

{: .note }
This is just an example of a simple spec for this feature. YMMV.

With so many Nice-to-Haves, how can we properly descope so we don’t overwhelm the implementing engineer(s)? I like to present different approaches with vastly different timelines and pros/cons and let someone else decide on the approach. In this way, the decider can make an educated decision and keep “realistic” expectations.

---

## The Solution(s)
I’m going to present three solutions in this section. Each will have its own merits and drawbacks in addition to a reasonable time estimate for a single software engineer to complete each solution.

---

### Solution 1: Scrappy Doo
![](https://www.thekingshabazz.com/wp-content/uploads/2020/05/scrappy.gif)

In true startup-fashion, let’s evaluate how we might add this feature with as little infrastructure as possible. 

First thing you should know is that the US government releases the polygons for each of these regions we might need every time they change. It’s completely free and open to use if you know how to use it.

Second is that this solution will assume ONLY radius search since it’s the only required ask.

Third is that we can do a very rudimentary distance calculation between two Cartesian points via the [Haversine equation](https://en.m.wikipedia.org/wiki/Haversine_formula#:~:text=These%20names%20follow%20from%20the,sin2(θ2)).

With these in mind, let’s get into the solution.

*drum roll* 🥁

JSON files!

That’s right! Let’s pre-process the geometry files and create a mapping of `qualifier: centroid` to give us our centroid for the calculation.

#### Step 1: Download the file

[Shapefile Directory By Layer](https://www2.census.gov/geo/tiger/TIGER_RD18/LAYER/)

We will need a file for each “layer” we want to support (e.g. [ZCTA520](https://www2.census.gov/geo/tiger/TIGER_RD18/LAYER/ZCTA520/) for both 3 and 5 digit zip codes)

#### Step 2: Convert Shapefile to GeoJSON

Install the [GDAL](https://gdal.org/download.html) library

```bash
brew install gdal
```

Once that’s complete, you should have the ogr2ogr command and you should be able to do a straightforward conversion to GeoJSON with the following command:

```bash
ogr2ogr -f GeoJSON output.json input.shp
```

This output file will be much larger than you’ll likely want to store. For this reason, we will convert the geometries into centroids for a given layer in the next step.

#### Step 3: Pre-process the file
Discarding accuracy for a moment, a simple centroid calculation can look like:

`(AVG(latitudes), AVG(longitudes))`

If we want to achieve greater accuracy with the centroid, we might want to move toward a richer solution. Again, being scrappy here.

So with that, we would write a script that looks something like this:

Get [ijson](https://github.com/ICRAR/ijson) for efficient parsing of this large file
```bash
pip install ijson
```

```python
import ijson

def centroid(points: List):
    x, y = zip(*points)
    l = len(x)
    return sum(x) / l, sum(y) / l

mapping = {}

with open("./output.json") as f:
  for record in ijson.items(f, "item"):
    mapping[record["zipcode"]] = centroid(record["geometry"])

with open("./zipcode-centroid.json") as f:
  json.dumps(f, mapping)
```

Which should result in a mapping file like:

zipcode-centroid.json
```json
{
  "93301": [35.3843365, -119.0205616],
  "93302": [35.5522, -118.9188],
  …
}
```

{: .info }
Repeat this for each file/layer that you need to support.


And there you have it! A file you can now use to get the centroid from an address qualifier. 

{: .note }
Alternatively, for this step you could also use [Geocoder.ca](http://geocoder.ca/), but the data is crowdsourced and not exactly under your control. Use at your own risk!

#### Step 4: Use the [file] Luke
Assuming you have a `customer_addresses` table with `latitude` and `longitude` columns, a query for the radius search (in kilometers) could look like this:

```sql
SELECT id, (
  3959 * 
  acos(
    cos(
      radians({centroid_latitude})
    ) * 
    cos(
      radians(latitude)
    ) *
    cos(
      radians(longitude) -
      radians({centroid_longitude})
    ) +
    sin(
      radians({centroid_latitude})
    ) *
    sin(
      radians(latitude)
    )
  )
) AS distance 
FROM customer_addresses
HAVING distance < {radius_in_km} 
ORDER BY distance;
```

That’s pretty much it. **Radius Search**  in just a few steps. 

#### Estimate

*Time estimate: 1-2 weeks*

Realistically, this could just be a single sprint’s worth of work considering differing PR processes, testing and validation, etc. I would be surprised if an engineer took longer than 2 weeks to do this but there may be unexpected issues with this approach given all of the variables that could affect this.

#### Evaluation

| Pros                         | Cons                                                    |
| ---------------------------- | ------------------------------------------------------- |
| No/Low Additional Complexity | Limited to Radius Search                                |
| Tiny Timeline                | Non-performant with a large `customer_addresses` table  |
| Easily replaceable           | Doesn’t add additional capabilities for future features |
| “Buys time”                  |                                                         |
| No/Low Cost                  |                                                         |

---

### Solution 2: Scooby Doo
![](https://wallpapercave.com/wp/Kn9s8PL.jpg)


{: .warning }
WIP

---

### Solution 3: Scooby Dooby Doo
![](https://static.wikia.nocookie.net/scoobydoo/images/5/54/Scooby-Dooby-Doo_%28Dumb_Waiter_Caper%29.png/revision/latest?cb=20180902013520)

{: .warning }
WIP