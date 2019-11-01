# My personlized build of st

The [suckless terminal (st)](https://st.suckless.org/) with some additional, very opinionated and personal features (mostly cosmetics):

This build is pretty much based on [Luke's st build](https://github.com/LukeSmithxyz/st), but customized from original st git sources, rather then being a Luke's fork.
## Bindings for

+ **scrollback** with `alt-↑/↓` or `alt-pageup/down` or just mousewheel (without holding shift or any other modifier)
+ OR **vim-bindings**: scroll up/down in history with `alt-k` and `alt-j`. Faster with `alt-u`/`alt-d`.
+ **zoom/change font size**: same bindings as above, but holding down alt as well. `alt-home` returns to default
+ **copy/paste text** is changed to Emacs-ish bindings. **Copy** with `ctrl-w` or `alt-w`, **paste** is `ctrl-y` or `shift-insert`
+ **delete** key will delete one character to the right. You can hold down alt/ctrl to delete form cursor to the end/beginning of the word.
+ **backspace** key will delete one character to the left. Holding down alt/ctrl will delete form cursor to the beginning/end of the word (yes it's **delete** reversed).
+ **Quit st** with `ctrl-q`.

## Pretty stuff

+ No resource files parsing at startup.
+ Default (and only) theme is [Solarized dark](https://ethanschoonover.com/solarized/).
+ Transparency/alpha, which is also adjustable as startup flag.
+ Default font is [Mark Simonsons Anonymous Pro](https://www.marksimonson.com/fonts/view/anonymous-pro)
  I use same font in Emacs, so it matches my setup that way. Size is 18pt, because I am getting old. Yeah! Small terminal
  fonts are kind-a not my thingy any more.
+ Default cursor is set to bar (from box), again because I use same in Emacs, so it matches my setup.

## Other st patches & custom changes

+ Scrollback
+ Scrollback with mouse
+ font2
+ updated to latest version 0.8.2
+ st-no-bold-colors (to get correct Solarized colors)
+ quitst - just some trivia I added for the sake of consistency with other applications.
+ compiled with speed opt flags
+ changed borderpx to 0
+ cursor shaped changed to bar
+ histsize set to 20 000
+ fps is changed to 60, bc my monitor does not support more anyway (59 to be exact).

## Installation for newbs

```
git clone https://github.com/amno1/st
cd st
sudo make install
```

Obviously, `make` is required to build. `fontconfig` is required for the default
build, since it asks `fontconfig` for your system font. It might be
obvious, but `libX11` and `libXft` are required as well. Chances are, you have
all of this installed already.

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the `$LIBS`
before compiling.

Be sure to have a composite manager (`xcompmgr`, `compton`, etc.) running if you
want transparency.

## How to configure dynamically with Xresources

You can't! :-) Xresource patch is removed in this build. I don't switch
themes or care much about terminal colours honestly, so I don't find this very
usefull. I would rather spare my cpu of parsing xrdb settings.

Alpha is set to be completely opaque, but you can easily change this by passing
command line argument, for example: st -A 0.8, or just recompile with desired alpha.
The `alpha` value (for transparency) goes from `0` (transparent) to `1`
(opaque). By default it is 1 (completely opaque). Honestly I don't use alpha,
but I left the path sit there.

## Aditional notes

It is quite easy to add back Luke's removed features if you wish to use those,
I have just commented out patch for external pipe, so if you really need to
copy/paste/open links from st, you can uncomment and recompile, it worked nice
when I tested. Alpha is a little bit more work to remove, so I have left it in
even though I don't use it myself. It works fine here (with compiz), but I just
don't need it.

### Colors

To be clear about the color settings:

- This build uses Solarized dark colors only *by default* and by any other means
  :-). I use same colour scheme for ls-colors, Emacs and Rofi and never switch
  themes either so I prefer to hardcode my theme. For that reason Xresources
  patch is removed.

## Contact

- Arthur Miller <arthur.miller@live.com>
- [https://nextpoint.se](https://nextpoint.se)
