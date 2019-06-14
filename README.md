# undx's build of st - the simple (suckless) terminal

Initially forked from LukeSmithxyz/st repo.

The [suckless terminal (st)](https://st.suckless.org/) with some additional features that make it literally the best terminal emulator ever:


## Useful keybindings

- `M-pageup/down` or `s-wheel` : scrollback
- `M-S-Wheel` : zoom
- `C-=` / `C--` / `C-0` : zoom in, out, reset
- `M-S-ESC` : keyboard_select
- `M-l` : follow urls
- `M-y` : copy urls
- `M-o` : copy the output of commands
- `M-c` / `M-y` : copy / paste text

## my added features

**keyboard_select**

```
When you run "keyboard_select", you have 3 modes available :

move mode : to set the start of the selection;
select mode : to activate and set the end of the selection;
input mode : to enter the search criteria.
Shortcuts for move and select modes :

 h, j, k, l:    move cursor left/down/up/right (also with arrow keys)
 !, _, *:       move cursor to the middle of the line/column/screen
 Backspace, $:  move cursor to the beginning/end of the line
 PgUp, PgDown : move cursor to the beginning/end of the column
 Home, End:     move cursor to the top/bottom left corner of the screen
 /, ?:          activate input mode and search up/down
 n, N:          repeat last search, up/down
 s:             toggle move/selection mode
 t:             toggle regular/rectangular selection type
 Return:        quit keyboard_select, keeping the highlight of the selection
 Escape:        quit keyboard_select
With h,j,k,l (also with arrow keys), you can use a quantifier. Enter a number before hitting the appropriate key.

Shortcuts for input mode :

 Return:       Return to the previous mode
```

To active `keyboard_select`, press `M-S-ESC`.


## Unique features (using dmenu)

+ **follow urls** by pressing `alt-l`
+ **copy urls** in the same way with `alt-y`
+ **copy the output of commands** with `alt-o`

## Bindings for

+ **scrollback** with `alt-↑/↓` or `alt-pageup/down` or `shift` while scrolling the mouse
+ OR **vim-bindings**: scroll up/down in history with `alt-k` and `alt-j`. Faster with `alt-u`/`alt-d`.
+ **zoom/change font size**: same bindings as above, but holding down shift as well. `alt-home` returns to default
+ **copy text** with `alt-c`, **paste** is `alt-v` or `shift-insert`

## Pretty stuff

+ Compatibility with `Xresources` and `pywal` for dynamic colors. The `Xdefaults` file shows a usage example.
+ Default [gruvbox](https://github.com/morhetz/gruvbox) colors otherwise.
+ Transparency/alpha, which is also adjustable from your `Xresources`.
+ Default font is system "mono" at 16pt, meaning the font will match your system font.

## Other st patches

+ Vertcenter
+ Scrollback
+ font2
+ updated to latest version 0.8.2

## Installation for newbs

```
git clone https://github.com/undx/st
cd st
sudo make install
```

Obviously, `make` is required to build. `fontconfig` is required for the default build, since it asks `fontconfig` for your system monospace font.  It might be obvious, but `libX11` and `libXft` are required as well. Chances are, you have all of this installed already.

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the `$LIBS` before compiling.

Be sure to have a composite manager (`xcompmgr`, `compton`, etc.) running if you want transparency.

## How to configure dynamically with Xresources

For many key variables, this build of `st` will look for X settings set in either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these files to load the settings.

For example, you can define your desired fonts, transparency or colors:

```
*.font:	Liberation Mono:pixelsize=12:antialias=true:autohint=true;
*.alpha: 0.9
*.color0: #111
...
```

The `alpha` value (for transparency) goes from `0` (transparent) to `1` (opaque).

### Colors

To be clear about the color settings:

- This build will use gruvbox colors by default and as a fallback.
- If there are Xresources colors defined, those will take priority.
- But if `wal` has run in your session, its colors will take priority.

Note that when you run `wal`, it will negate the transparency of existing windows, but new windows will continue with the previously defined transparency.

## Contact

- undx (@undx on slack)
- [https://www.undx.net](https://www.undx.net)
