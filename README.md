# Fluxbox dotfiles (Acer)

![](https://github.com/jatardine/dotfiles-fluxbox-acer/blob/main/styles/fluxbox-acer-prev.png)

This is one of my three different Fluxbox configs and the most bare-bone with little dependencies. This repo acts as a secondary backup for my config but you're free to clone and manually copy all files you desire:

`git clone https://github.com/jatardine/dotfiles-fluxbox-acer.git`

### Dependencies:

- fluxbox
- Isokeva Custom (font)
- dunst (notifications)
- Network Manager (dmenu)
- scrot (screenshots)
- nm-applet (systray)
- volumeicon (systray)
- cbatticon (systray)
- xfce4-settings
- feh (background)
- PulseAudio (sorry but my laptop refuses to call amixer)

Optional but recommended:

- menumaker

Menu dependencies (optional – you may change `menu` according to your usecase):
- alacritty (terminal)
- librewolf (web browser)
- leafpad (text editor)
- betterlockscreen (lock & suspend)
- systemd (for menu shortcuts calling "Reboot" and "Shutdown")

### Manual installation for first-time users of Fluxbox (recommended)

Once you've cloned this repo and downloaded all dependencies, DO NOT immediatedly run Fluxbox, instead open your terminal and create `.fluxbox` manually:

`mkdir ~/.fluxbox`

Now you can copy all Fluxbox files to your new directory:

`cp ~/fluxbox-dotfiles-acer ~/.fluxbox`

This will provide you a decent session to get started, as the default only provides menu entries for xterm and Firefox.

### Menu

The menu will require additional tweaks to properly list all your installed software and remove unnecessary entries. You may want to use `menumaker` to automatically create a menu but keep in mind that this will overwrite the separated sections. `[TERMINAL]` needs to be replaced with your preferred Terminal Emulator:

`mmaker fluxbox -t [TERMINAL]`

If you want to re-add the original shortcuts, just copy the appropriate sections from your downloaded fluxbox-dotfiles-acer's `menu` file.

### Background

This wallpaper is from my hobbyist observations, hence I ask anyone fetching this configuration to respect the copyright (any non-commercial usage is okay as long as credit is being given). It may not load due to `.fehbg` yet needing to be created.

If you want to use the default background, open your terminal and run feh:

`feh --bg-scale ~/.fluxbox/backgrounds/aglaisio.jpg`

Feh will then automatically create the necessary `.fehbg` called by the startup script.

If you want to use a different background, you first need to remove the default background from `overlay` to prevent it from overwriting your desired wallpaper. Then simply run the feh command above but replace the path with the one where your desired background is located. Alternatively, you can also copy your background to `backgrounds` and only replace `/algaisio.jpg` with your file's name.

### Keys

Those still largely rely on the defaults provided by Fluxbox itself. Some changes include:

```
# open a terminal
Mod4 Return :Exec alacritty

# volume settings, using common keycodes
# if these don't work, use xev to find out your real keycodes
XF86AudioRaiseVolume :Exec pactl set-sink-volume @DEFAULT_SINK@ +5%
XF86AudioLowerVolume :Exec pactl set-sink-volume @DEFAULT_SINK@ -5%
XF86AudioMute :Exec pactl set-sink-mute 0 toggle

# take a screenshot (full)
Print :Exec scrot 'Screenshot_%Y-%m-%d-%I-%M-%S_$wx$h.png' -e 'mv $f $$(xdg-user-dir PICTURES) ; viewnior $$(xdg-user-dir PICTURES)/$f'
```

At this time, `scrot` refuses to capture anything but the entire screen, so you want to select an area or only capture the active window, you may have to set an approriate keybind yourself. I'm still working on fixing that, though.

## TODO

- clean up `keys`
- include theme for Alacritty
✓ sort this repo
