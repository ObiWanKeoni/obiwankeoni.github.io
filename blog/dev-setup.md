---
layout: blog
title: Dev Setup
description: Details on my keyboard-driven setup for software engineering.
image_link: /assets/images/dev-setup.webp
parent: Blog
date: 2023-09-09
time_to_read: 0 min
disclaimer: My setup is just that, mine. It is highly opinionated and I like it that way.
tools:  
 - term: Window Manager (WM)  
   definition: Yabai  
   link: "https://github.com/koekeishiya/yabai"  
 - term: (Current) Editor  
   definition: RubyMine (JetBrains)  
   link: "https://www.jetbrains.com/ruby/"  
 - term: Terminal Emulator  
   definition: iTerm2  
   link: "https://iterm2.com/"  
 - term: Writing App  
   definition: Obsidian  
   link: "https://obsidian.md/"  
 - term: Browser  
   definition: Arc  
   link: "https://arc.net/"  
 - term: Music Player  
   definition: Spotify (Spicetify)  
   link: "https://spotify.com"  
 - term: Colorscheme  
   definition: Catppuccin  
   link: "https://github.com/catppuccin/catppuccin"  
 - term: Keyboard  
   definition: W-Ergolite  
   link: "https://keyclicks.ca/products/w-ergolite-2-4g-wireless-split-keyboard-2"  
 - term: Pointing Device  
   definition: Veikk Creator A15  
   link: "https://veikk.com/route/product/product?path=109_112&product_id=271"
---

I am software engineer passionate about [ergonomic keyboards](/blog/your-keyboard-has-too-many-keys.html) and maximum efficiency for development. That being said, my development setup is evergreen as I consistently find ways to improve upon work that I've done in the past. What you may have seen here before may not be the setup in the near future.

The rest of this post will be a deep dive into the tools I use **and how I use them**. If you have any suggestions for improvements, I will happily [hear them out](mailto:keoni_garner@yahoo.com).

---

# My Tools of Choice

> "**Give me six hours to chop down a tree and I will spend the first four sharpening the axe.**" - Abraham Lincoln

<dl>
	{% for tool in page.tools %}
	<dt>{{ tool.term }}</dt><dd><a href="{{ tool.link }}">{{ tool.definition }}</a></dd>
	{% endfor %}
</dl>

Screenshot:

![[assets/images/dev-setup-screenshot.webp]]
{: .blog-img}

We will be going into greater detail into each of these but this is a high-level overview of my arsenal of tools.

## Yabai
Since I do use MacOS **strictly**, this window manager is a must-have. I used basically every other window manager on the market and none come close to the binary space partitioning that Yabai has built-in. It allows me to organize my windows just where I need them with little fiddling.

That said, I do notice some strange behavior semi-frequently as the built-in window manager battles with Yabai. I do not disable System Integrity Protection so there are features and capabilities that I may be missing.

I utilize [Simple Hotkey Daemon (skhd)](https://github.com/koekeishiya/skhd) to make the whole system keyboard-driven. It allows me to move windows and switch focus without removing my fingers from the keyboard. Here's a peek into my keybindings:

<table>
  <thead>
    <th>COMMAND</th>
    <th>ACTION</th>
  </thead>
  <tbody>
    {% include components/command-row.html command='⌘ + return' description='Toggle center floating Slack window' %}
    {% include components/command-row.html command='⌥ + return' description='Toggle center floating iTerm window' %}
    {% include components/command-row.html command='⌃ + n' description='Move Focus West' %}
    {% include components/command-row.html command='⌃ + e' description='Move Focus South' %}
    {% include components/command-row.html command='⌃ + u' description='Move Focus North' %}
    {% include components/command-row.html command='⌃ + i' description='Move Focus East' %}
    {% include components/command-row.html command='⇧&⌃ + n' description='Move Window West' %}
    {% include components/command-row.html command='⇧&⌃ + e' description='Move Window South' %}
    {% include components/command-row.html command='⇧&⌃ + u' description='Move Window North' %}
    {% include components/command-row.html command='⇧&⌃ + i' description='Move Window East' %}
    {% include components/command-row.html command='⌘&⌥&⌃&⇧ + home' description='Cycle windows counterclockwise' %}
    {% include components/command-row.html command='⌘&⌥&⌃&⇧ + end' description='Cycle windows clockwise' %}
    {% include components/command-row.html command='⌥ + a' description='Toggle padding' %}
    {% include components/command-row.html command='⌥ + d' description='Expand window over split' %}
    {% include components/command-row.html command='⌥ + f' description='Full screen' %}
    {% include components/command-row.html command='⇧&⌥ + f' description='Native full screen' %}
    {% include components/command-row.html command='⇧&⌥ + b' description='Toggle window border' %}
    {% include components/command-row.html command='⌥ + e' description='Toggle split type' %}
    {% include components/command-row.html command='⌥ + t' description='Float and Center/Unfloat Window' %}
    {% include components/command-row.html command='⇧&⌥ + t' description='Float and Center/Unfloat Window (Large)' %}
  </tbody>
</table>

## RubyMine (JetBrains)  
This is my current editor of choice and the main reason is the lack of Ruby support with other editors. I was a VSCode guy for years, slowly being pulled toward (Neo)Vim but that was when I was working with JavaScript and Python mainly. Now that I work with Ruby first and foremost, I needed something that could Just Work™ without needing to fiddle with configurations. While I know other editors may have better support at this point, I have absolutely 0 problems with RubyMine so I'm not willing to change at this point in time. 

I use the VSCode keybindings here along with a few custom ones to allow me to easily switch focus between split editors and to easily run/rerun tests for my active file.

## iTerm2
I have tried other terminal emulators and iTerm2 is just too solid to give up for me. Alacritty is really nice and I love that I can get rid of the traffic lights but I have too much "muscle" memory when it comes to terminals that I can't even think about changing at this point.

## Obsidian
What a complex setup I have here... First thing to call out is that this entire post was written in Obsidian - actually this whole website was written from Obsidian minus the CSS.

{: note}
This site was ~95% written from my mobile device. If this is of interest to folks, I can explain how I managed to do that and not go totally insane.

On top of that, I use [obsidian-git](https://github.com/denolehov/obsidian-git) to manage syncing between my phone and my laptop. There is also a GitHub action in a private repo that forwards any public-facing changes to my public-facing repo which will then build and publish this site again. I can go from pushing to published in ~1 min on average.

## Arc  

## Spotify (Spicetify)
$17 to stream ANY song at ANY time from ANY device (provided a network connection or it's downloaded to your phone) is just too good to pass up! I use the [Catppuccin theme for spicetify](https://github.com/catppuccin/spicetify) for ✨*aesthetics* ✨

## Catppuccin
I just dig it.

## W-Ergolite  
## Veikk Creator A15