# .tmux.conf
My Personal  Tmux Configuration with Emacs prefix key  that just works (imho the best tmux configuration I think) based on gpakosz/.tmux.conf

![Screenshot](https://cloud.githubusercontent.com/assets/553208/19740585/85596a5a-9bbf-11e6-8aa1-7c8d9829c008.gif)


Installation
------------



- cd 
- git clone https://github.com/askDing/.tmux_conf.git
- ln -s -f .tmux/tmux.conf



If you want to `custmize`  your tmux.conf ,just touch a file named `.tmux.conf.local` :

Features
--------

- prefix key is `C-x`,which is the same of Emacs prefix key.
- visual theme inspired by [Powerline]
- [maximize any pane to a new window with `<prefix> +`][maximize-pane]
- SSH aware username and hostname status line information
- mouse mode toggle with `<prefix> m`
- automatic usage of [`reattach-to-user-namespace`][reattach-to-user-namespace]
     if available
- laptop battery status line information
- uptime status line information
- optional highlight of focused pane (tmux `>= 2.1`)
- configurable new windows and panes behavior (optionally retain current path)
- SSH aware split pane (reconnects to remote server, experimental)
- copy to OS clipboard (needs [`reattach-to-user-namespace`][reattach-to-user-namespace]
    on macOS, `xsel` or `xclip` on Linux)
- [Facebook PathPicker][] integration if available
- [Urlview][] integration if available

 [Powerline]: https://github.com/Lokaltog/powerline
 [maximize-pane]: http://pempek.net/articles/2013/04/14/maximizing-tmux-pane-new-window/
 [reattach-to-user-namespace]: https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard
 [Facebook PathPicker]: https://facebook.github.io/PathPicker/
 [Urlview]: https://packages.debian.org/stable/misc/urlview

![Maximize pane](https://cloud.githubusercontent.com/assets/553208/9890858/ee3c0ca6-5c02-11e5-890e-05d825a46c92.gif)

Mouse mode allows you to set the active window, set the active pane, resize
panes and automatically switches to copy-mode to select text.

![Mouse mode](https://cloud.githubusercontent.com/assets/553208/9890797/8dffe542-5c02-11e5-9c06-a25b452e6fcc.gif)



Common key-bindings:
--------------------

 - `<prefix> e` opens `~/.tmux.conf.local` with the editor defined by the
   `$EDITOR` environment variable (defaults to `vim` when empty)
 - `<prefix> r` reloads the configuration
 - `C-l` clears both the screen and the tmux history

 - `<prefix> C-c` creates a new session
 - `<prefix> c` creates a new panel
 - `<prefix> o` exchange panels
 - `<prefix> C-f` lets you switch to another session by name

 - `<prefix> C-h` and `<prefix> C-l` let you navigate windows (default
   `<prefix> n` and `<prefix> p` are unbound)
 - `<prefix> Tab` brings you to the last active window

 - `<prefix> /` splits the current pane vertically
 - `<prefix> -` splits the current pane horizontally
 - `<prefix> h`, `<prefix> j`, `<prefix> k` and `<prefix> l` let you navigate
   panes ala Vim
 - `<prefix> H`, `<prefix> J`, `<prefix> K`, `<prefix> L` let you resize panes
 - `<prefix> <` and `<prefix> >` let you swap panes
 - `<prefix> +` maximizes the current pane to a new window

 - `<prefix> m` toggles mouse mode on or off

 - `<prefix> U` launches Urlview (if available)
 - `<prefix> F` launches Facebook PathPicker (if available)

 - `<prefix> Enter` enters copy-mode
 - `<prefix> b` lists the paste-buffers
 - `<prefix> p` pastes from the top paste-buffer
 - `<prefix> P` lets you choose the paste-buffer to paste from

### Enabling the Powerline look

Powerline originated as a status-line plugin for Vim. Its popular eye-catching
look is based on the use of special symbols: <img width="80" alt="Powerline Symbols" style="vertical-align: middle;" src="https://cloud.githubusercontent.com/assets/553208/10687156/1b76dda6-796b-11e5-83a1-1634337c4571.png" />

To make use of these symbols, there are several options:

- use a font that already bundles those: this is e.g. the case of the
  [2.030R-ro/1.050R-it version][source code pro] of the Source Code Pro font
- use a [pre-patched font][powerline patched fonts]
- use your preferred font along with the [Powerline font][powerline font] (that
  only contains the Powerline symbols): [this highly depends on your operating
  system and your terminal emulator][terminal support]
- [patch your preferred font][powerline font patcher] by adding the missing
  Powerline symbols: this is the most difficult way and is no more documented in
  the [Powerline manual]

[source code pro]: https://github.com/adobe-fonts/source-code-pro/releases/tag/2.030R-ro/1.050R-it
[powerline patched fonts]: https://github.com/powerline/fonts
[powerline font]: https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
[powerline font patcher]: https://github.com/powerline/fontpatcher
[terminal support]: http://powerline.readthedocs.io/en/master/usage.html#usage-terminal-emulators
[Powerline manual]: http://powerline.readthedocs.org/en/latest/installation.html#fonts-installation

Please see the [Powerline manual] for further details.

Then edit the `~/.tmux.conf.local` file (`<prefix> e`) and adjust the following
variables:

```
tmux_conf_theme_left_separator_main=''
tmux_conf_theme_left_separator_sub=''
tmux_conf_theme_right_separator_main=''
tmux_conf_theme_right_separator_sub=''
```
### Configuring the status line

Contrary to the first iterations of this configuration, by now you have total
control on the content and order of `status-left` and `status-right`.

Edit the `~/.tmux.conf.local` file (`<prefix> e`) and adjust the
`tmux_conf_theme_status_left` and `tmux_conf_theme_status_right` variables to
your own preferences.

This configuration supports the following builtin variables:

 - `#{battery_bar}`: horizontal battery charge bar
 - `#{battery_percentage}`: battery percentage
 - `#{battery_status}`: is battery charging or discharging?
 - `#{battery_vbar}`: vertical battery charge bar
 - `#{circled_session_name}`: circled session number, up to 20
 - `#{hostname}`: SSH aware hostname information
 - `#{hostname_ssh}`: SSH aware hostname information, blank when no SSH
   connection detected
 - `#{loadavg}`: load average
 - `#{pairing}`: is session attached to more than one client?
 - `#{prefix}`: is prefix being depressed?
 - `#{root}`: is current user root?
 - `#{uptime_d}`: uptime days
 - `#{uptime_h}`: uptime hours
 - `#{uptime_m}`: uptime minutes
 - `#{uptime_s}`: uptime seconds
 - `#{username}`: SSH aware username information
 - `#{username_ssh}`: SSH aware username information, blank when no SSH
   connection detected












































