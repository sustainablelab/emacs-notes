# Install on Windows

Two options:

## Download binary

http://mirror.keystealth.org/gnu/emacs/windows/emacs-27/emacs-27.1-x86_64-installer.exe

## MSYS

```bash
pacman -S mingw-w64-x86_64-emacs
```

# Start using emacs

## Start and quit emacs

Start:

```bash
emacs
```

Quit:

```
C-x C-c
```

## Escape

If trying to exit a command or if Emacs seems unresponsive:

```
C-g
```

## Start in vanilla mode

Start Emacs without any configuration:

```bash
emacs -Q
```

- `-Q` prevents *any* initialization files from running.
    - It even blocks the "GNU Emacs" startup page.
- `-Q` gives barebones, vanilla emacs.

Quit:

```
C-x C-c
```

## Start customizing from scratch

I initially installed the **spacemacs** package. But I want to
learn emacs without **spacemacs**. There is a lot going on that
slows the startup and I don't really know where to start.

I simply move the entire `.emacs.d` folder and the `.spacemacs`
files out of my home directory into a folder called `old`. Now I
can start from scratch, but I can move the spacemacs version back
in any time.

Start emacs. Now that I moved out the spacemacs stuff, I can run
emacs without the `-Q`.

```bash
emacs
```

## Move between buffers

List the buffers:

```
C-x C-b
```

There are three buffers: `GNU Emacs`, `scratch`, and `Messages`.

Switch between the `scratch` and `GNU Emacs` buffers:

```
C-x b <Enter>
```

Switch to the `Messages` buffer:

```
C-x b Messages
```

*Start typing Messages but hit tab to use tab completion.*

Quit:

```
C-x C-c
```

[[level-2|Go to level 2]]
