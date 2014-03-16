---
layout: post
title: "Ubuntu-Zero To Deploy"
description: "configure ubuntu from scratch"
series: ubuntu-zero-to-deploy
category: articles
tags: [Ubuntu, Terminator]
image:
  feature: ubuntu.png
comments: true
share: true
---
* * *
{% include series.html %}
* * *

Being a distro hopper i switch distros often and i really enjoy it but the main problems are installing all the required applications,setting up the work environment,configure my editor etc..i have to spend at-least half a day to make it work the way i wanted..

It was fine when i tried to hack around all the distros back in my college days but after starting my own applications or working for other projects i can't really spend half of my productive day in setting up my distro so i decided to document all my configurations, settings and tweaks that would help me when i switch to another distro or probably a new version of Ubuntu itself and at the same time it might help others to make their installations real quick and easy..

#### Terminator
    
The first thing i always install in my fresh Ubuntu is [Terminator](https://launchpad.net/terminator)..
Terminator is a terminal emulator that has so may cool features like multiple session in a single tab..
<figure>
  <img src="/images/terminator.gif">
  <figcaption><a href="http://github.com/rajanand02" title="Terminator the awesome terminal emulator"></a>Terminator the awesome terminal-emulator.</figcaption>
</figure>

You can edit your code, commit your changes in git, run server and execute shell commands inside a single tab..

##### Some useful shortcuts
* `Ctrl+Shift+E` - Split the view Vertically.
* `Ctrl+Shift+O` - Split the view horizontally.
* `Ctrl+Shift+arrows` - Resize the view.
* `Ctrl+Shift+T` - Open new Tab.
* `Ctrl+Shift+W` - Close the current view.
* `Ctrl+Shift+P` - Focus the view on previous pane.
* `Ctrl+Shift+N` - Focus the view on next pane.
* `Ctrl+Shift+Q` - Quit Terminator. 

##### Terminator-Solarized Color Scheme
copy the following code to
  `~/.config/terminator/config`
{% raw %}
    [global_config]
      title_transmit_bg_color = "#d30102"
      focus = system
    [keybindings]
    [profiles]
      [[default]]
        # solarized-dark
        palette = "#073642:#dc322f:#859900:#b58900:#268bd2:#d33682:#2aa198:#eee8d5:#002b36:#cb4b16:#586e75:#657b83:#839496:#6c71c4:#93a1a1:#fdf6e3"
        foreground_color = "#eee8d5"
        background_color = "#002b36"
        cursor_color = "#eee8d5"

    [[solarized-dark]]
       palette = "#073642:#dc322f:#859900:#b58900:#268bd2:#d33682:#2aa198:#eee8d5:#002b36:#cb4b16:#586e75:#657b83:#839496:#6c71c4:#93a1a1:#fdf6e3"
       foreground_color = "#eee8d5"
       background_color = "#002b36"
       cursor_color = "#eee8d5"

    [[solarized-light]]
       #palette = "#073642:#dc322f:#859900:#b58900:#268bd2:#d33682:#2aa198:#eee8d5:#002b36:#cb4b16:#586e75:#657b83:#839496:#6c71c4:#93a1a1:#fdf6e3"
       #background_color = "#eee8d5"
       #foreground_color = "#002b36"
       #cursor_color = "#002b36"

    [layouts]
      [[default]]
       [[[child1]]]
         type = Terminal
         parent = window0
         profile = solarized-dark
       [[[window0]]]
        type = Window
        parent = ""
        size = 800, 600
    [plugins]

{% endraw %}

> refer the code in [github](https://github.com/ghuntley/terminator-solarized)
