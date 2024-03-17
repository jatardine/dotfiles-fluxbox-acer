# Fluxbox dotfiles (Acer)

![](https://github.com/jatardine/dotfiles-fluxbox-acer/blob/main/styles/fluxbox-acer-prev.png)

This is one of my three different Fluxbox configs and the most bare-bone with little dependencies. This repo acts as a secondary backup for my config but you're free to clone and manually copy all files you desire:

`git clone https://github.com/jatardine/dotfiles-fluxbox-acer.git`

### Dependencies:

- Fluxbox (yeah)
- Isokeva Custom (any [Isokeva font](https://typeof.net/Iosevka/) works but may require some manual editing in some places)
- Network Manager
- scrot (screenshots)
- nm-applet (systray)
- volumeicon (systray)
- cbatticon (systray)
- Feh (background)
- PulseAudio (sorry lmao)
- Polkit & xfce-polkit ("Apps as Root")
- xfce4-notifyd (notification daemon)

**Optional but recommended:**

- menumaker

Menu dependencies (optional – you may change `menu` according to your usecase):
- Alacritty (Terminal) – [CUSTOM THEME](https://github.com/jatardine/dotfiles-alacritty)
- LibreWolf (Web Browser)
- PCManFM (File Manager)
- Leafpad (Text Editor)
- betterlockscreen (Lock & Suspend)
- systemd (Reboot & Shutdown)

## Manual installation for first-time users of Fluxbox (optional)

Once you've cloned this repo and downloaded all dependencies, DO NOT immediatedly run Fluxbox, instead open your terminal and create `.fluxbox` manually:

`$ mkdir ~/.fluxbox`

Now you can copy all Fluxbox files to your new directory:

`$ cp ~/fluxbox-dotfiles-acer ~/.fluxbox`

This will provide you a decent session to get started, as the default only provides menu entries for xterm and Firefox.

### Menu

The menu will require additional tweaks to properly list all your installed software and remove unnecessary entries. You may want to use `menumaker` to automatically create a menu but keep in mind that this will overwrite the separated sections. `[TERMINAL]` needs to be replaced with your preferred Terminal Emulator:

`$ mmaker fluxbox -t [TERMINAL]`

If you want to re-add the original shortcuts, just copy the appropriate sections from your downloaded fluxbox-dotfiles-acer's `menu` file.

### Background

This wallpaper is from my hobbyist observations, hence I ask anyone fetching this configuration to respect the copyright (any non-commercial usage is okay as long as credit is being given). It may not load due to `.fehbg` yet needing to be created.

If you want to use the default background, open your terminal and run feh:

`$ feh --bg-scale ~/.fluxbox/backgrounds/aglaisio.jpg`

Feh will then automatically create the necessary `.fehbg` called by the startup script. Make it executable with `chmod +x`.

If you want to use a different background, you first need to remove the default background from `overlay` to prevent it from overwriting your desired wallpaper. Then simply run the feh command above but replace the path with the one where your desired background is located. Alternatively, you can also copy your background to `backgrounds` and only replace `/algaisio.jpg` with your file's name.

### Keys

Keybinds to navigate Fluxbox. The default automatically generated by Fluxbox upon first run turned out to be completely broken and resulted in very odd behavior, hence this file was written from scratch.

Read it carefully and adjust it to your needs.

### Polkit rules for "Apps as Root"

Not elegant but those files need to be copied individually to `/usr/share/polkit-1/actions` to not accidentally overwrite existing actions folder (requires root). It's up to you whether to use the files from the cloned git or your local copy in ~/.fluxbox (assuming you copied and pasted this git as is):

```
# cp ~/.fluxbox/polkit-1/actions/org.freedesktop.alacritty.policy /usr/share/polkit-1/actions
# cp ~/.fluxbox/polkit-1/actions/org.lxde.pcmanfm.policy /usr/share/polkit-1/actions
# cp ~/.fluxbox/polkit-1/actions/org.xfce.xfce4-terminal /usr/share/polkit-1/actions
```
You can also write your own policies for each program for more granular privileges. Once you're done, feel free to remove the Polkit directory from your ~/.fluxbox.

See: [Arch Wiki: Polkit](https://wiki.archlinux.org/title/Polkit)

## TODO (will be removed soon due to no longer being needed)

- ✓ clean up `keys`
- ✓ include theme for Alacritty
- ✓ sort this repo
