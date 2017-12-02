---
title: editor-support
---

# Text editors {#text-editors}

Note

If you don't have a favourite text editor, or don't really

:   know what a text editor is, then that's ok! Atom is probably the
    text editor for you.

## Atom {#atom}

[Atom](https://atom.io/) is a cross-platform text editor which runs on
OS X, Linux and Windows. It was originally created by GitHub, but it's
open source a large (and growing) variety of packages for different
languages and tasks and a great community.

This doesn't cover all the basics of Atom here, because the [Atom
documentation](https://atom.io/docs) do that pretty well. Think of this
as a 'cheat sheet', for dipping back into to refresh your memory when
you just can't remember how to do something off the top of your head.

### Installation {#installation}

Installing Atom is a piece of cake---go to the [Atom
homepage](https://atom.io/) and hit the big red "Download" button near
the top of the page. When it's finished downloading, click on the
downloaded file and follow the instructions which show up on the screen.

Once you've got Atom up and running, you need to install the [Atom
Extempore package](https://github.com/benswift/extempore-sublime)---this
tells the Atom editor how to deal with Extempore code. You can do this
through the menu bar:
`Packages > Settings View > Install Packages/Themes`, then search for
"extempore" and click install on the `Extempore-Atom` package.
Alternatively, you can install it at a terminal with
`apm install extempore-atom`. Once that's done, you're ready to go.

If you want to run Extempore in a terminal *inside* Atom, then you can
get the `term` package as well, search for it in the same window as
before.

The main way to do things in Atom is through the "command palette",
which you can bring up with `Ctrl+Shift+P` on Windows/Linux or
`Cmd+Shift+P` on OSX. Type in a few letters, and you'll see the name of
all the commands the system understands starting with those letters.
It's really powerful, and it's a good first place to look when you want
to do something. All of the menu bar commands in this blog post can be
accessed through the command palette, and it's usually quicker than

### Writing Extempore code {#writing-extempore-code}

1.  start Atom
2.  open up a terminal *outside* Atom (e.g. `Terminal` on OS X or
    `cmd.exe` on Windows) or a `term` *inside* Atom (e.g.
    `Packages > Term > New Right Pane Terminal`)
3.  in the terminal, run `extempore` (just type `extempore` and hit
    `return`) and you should see it print out some info about your
    system, then just sit there waiting for input
4.  open (`File > Open`) an existing Extempore file such as
    `examples/core/fmsynth.xtm`, or create and save new file with a
    `.xtm` extension
5.  connect to the running Extempore process with the
    `Extempore connect` command---either with the keyboard shortcut
    `Alt+O` or the menu bar (`Packages > Extempore > Connect`), the
    default `host:port` combination of `localhost:7099` should be fine

Then, to evaluate Extempore code, move your cursor onto (or highlight)
the code you want to evaluate and hit `Alt+S` to evaluate the code.
Change the code and re-evaluate it by hitting `Alt+S` again---the code
is live, so you can change and re-evaluate things without having to
re-start Extempore.

If you *do* want to restart the Extempore process, just `ctrl+c` in the
terminal where `extempore` is running to kill it, then start it up
again.

## Emacs {#emacs}

### Installation {#installation-1}

`extempore-mode` is available from [MELPA](http://melpa.org/) - just
`M-x package-install RET extempore-mode RET` and you're done.

If you don't want to get it from MELPA, just [download the
file](https://github.com/extemporelang/extempore-emacs-mode/blob/master/extempore-mode.el)
and `(package-install-file "/path/to/extempore-mode.el")`

### Writing Extempore code {#writing-extempore-code-1}

1.  start Emacs (if it isn't running already)
2.  open up an Emacs buffer with an Extempore file (`extempore-mode`
    should be loaded automatically when Emacs sees the `.xtm` file
    extension, assuming you added code above to your `.emacs`)
3.  call `M-x switch-to-extempore` (`C-c C-z`), and if Extempore isn't
    already running you'll can add (optional) command line args for
    Extempore here, such as which audio device to use (e.g.
    `./extempore --device 2`)
4.  connect to the running Extempore process: `C-c C-j` (this needs to
    be done for *every* `.xtm` buffer)

Then, to evaluate Extempore code, use either

-   evaluate enclosing s-expression: `C-c C-c` or `C-M-x`
-   evaluate region: `C-c C-r`
-   evaluate whole buffer: `C-c C-b`

To restart the Extempore process, just `C-c C-c` in the `*extempore*`
buffer where `extempore` is running to kill it, then start it up again
with `M-x switch-to-extempore` (`C-c C-z`).

## Sublime Text 2 {#sublime-text-2}

[Sublime Text 2](http://www.sublimetext.com) (ST2) is a cross-platform
text editor which runs on OS X, Linux and Windows. It's the 'spiritual
successor' to Textmate, and it has some cool features, a large variety
of plugins for different languages and tasks, and a great community.

I won't cover all the basics of ST2 here, because the [(unofficial)
documentation](http://docs.sublimetext.info/en/latest/) does that pretty
well. Think of this post as a 'cheat sheet', for dipping back into to
refresh your memory when you just can't remember how to do something off
the top of your head.

### Installing ST2 {#installing-st2}

Installing ST2 is a piece of cake---there are binaries for all platforms
on the [download](http://www.sublimetext.com/2) page.

You'll also need the [ST2 Extempore
plugin](https://github.com/benswift/extempore-sublime), which provides
syntax highlighting and some commands for connecting to and working with
a running Extempore process. To install the plugin, download the [plugin
files](https://github.com/benswift/extempore-sublime/zipball/master) (or
clone the repo) and unzip them into your [ST2 packages
directory](http://docs.sublimetext.info/en/latest/basic_concepts.html#the-packages-directory)
(put it in the top level, not in the `User` subdirectory).

### Writing Extempore code {#writing-extempore-code-2}

1.  start ST2
2.  open up your favourite shell (e.g. Terminal on OS X or cmd.exe on
    Windows)
3.  `cd` into your Extempore directory and run `extempore`, e.g.
    `./extempore`
4.  open up an ST2 buffer with an Extempore file (the Extempore plugin
    should be loaded automatically when ST2 sees the `.xtm` file
    extension)
5.  connect to the running Extempore process with the
    `extempore connect` command, which you can call through the command
    palette (`Ctrl+Shift+P` on Windows/Linux or `Cmd+Shift+P` on OSX) or
    the menu bar (`Tools > Extempore > Connect`)

Then, to evaluate Extempore code, highlight the code you want to
evaluate and hit `evaluate region` (which by default is mapped to
`ctrl+e`).

To restart the Extempore process, just `ctrl+c` in the terminal where
`extempore` is running to kill it, then start it up again.

### Known issues {#known-issues}

The syntax highlighting currently doesn't cover a few edge cases---so if
you end up tinkering with `Extempore.JSON-tmLanguage` to fix anything
then I'd love it if you submitted a patch.

Also, `extempore_evaluate` currently requires **highlighting** the code
to evaluate. It would be nice if it would eval the top-level
s-expression if no region was highlighted. This is hopefully not too
tricky to add if you know a bit about how ST2 works.

## Vim {#vim}

Extempore's [vim plugin](https://github.com/timburgess/extempore.vim) is
maintained by Tim Burgess.

Remember to have your terminal (where Extempore is running) somewhere
you can see it, since Extempore's `stdout` will show up there (and not
in vim).

### Writing Extempore code {#writing-extempore-code-3}

1.  start vim
2.  open up your favourite shell (e.g. Terminal on OS X or cmd.exe on
    Windows)
3.  `cd` into your Extempore directory and run `extempore`, e.g.
    `./extempore --device 2`
4.  in vim, create a new file or open an existing one (e.g. from the
    `examples/` subdirectory) and `:source` the extempore plugin (which
    is located by default in `extras/extempore.vim`)
5.  connect to the running Extempore process with
    `:ExtemporeSendEnclosingBlock` (or the `<Leader>w` keybinding)

Then, to evaluate Extempore code, position the cursor in (or highlight)
the code you want to evaluate and use the `ExtemporeSendEnclosingBlock`
command (which by default is mapped to `<Leader>w`).

To restart the Extempore process, just `ctrl+c` in the shell where
`extempore` is running to kill it, then start it up again (you'll have
to reconnect vim to this new Extempore process).

### Known issues {#known-issues-1}

The vim mode doesn't yet support multiple connections or user-specified
host/port, but pull requests are welcome!

A big thankyou to Tim Mellor and others (including Garett Shulman) who
have contributed to the vim plugin.
