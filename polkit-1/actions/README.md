# Polkit policies for "Apps as Roots" menu shortcuts

Those files need to be placed in `/usr/share/polkit-1/actions` in order for the "Apps as Roots" programs to work.

Unlike Archcraft, which pipes sudo authentication through Rofi in its Openbox menu config, this config directly 
calls Polkit (via `pkexec` in menu) to gain root privileges to specific programs, in this case Alacritty, Xfce Terminal 
and PCManFM. Polkit requires rules to process authentication for each program.

[Arch Wiki: Polkit](https://wiki.archlinux.org/title/Polkit)

Those rules provide a somewhat "graphical sudo" to GUI programs which cannot be accomplished by merely telling Fluxbox
to execute any terminal with `sudo [PROGRAM]`. It doesn't work with non-CLI programs and consumes rescources due
to constantly spawning new terminal processes that fail at gaining root privileges.

**Directly executed via menu:**
 Alacritty (`pkexec alacritty`)
 Xfce Terminal (`pkexec xfce4-terminal`)
 PCMANFM (`pkexec pcmanfm`)

Because I always want to open Vim in a privileged Xfce Terminal, I set Fluxbox to open Xfce Terminal to execute 
Vim:

 `pkexec xfce-terminal --command="vim"`
 
