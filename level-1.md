# Install on Windows

Two options:

## Download binary

*I have not tried this.*

http://mirror.keystealth.org/gnu/emacs/windows/emacs-27/emacs-27.1-x86_64-installer.exe


## MSYS

*This is how I did it.*

Open `msys` terminal and install the package:

```bash
pacman -S mingw-w64-x86_64-emacs
```

# Start using emacs

Run from a `mingw` terminal (because I installed on `msys`).

## Start and quit emacs

Start:

```bash
emacs
```

Quit:

```
C-x C-c
```

## Escape is C-g

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

# Basic buffer management

Here is the minimal buffer and window management I need to get
started.

## List buffers

List the buffers:

```
C-x C-b
```

There are three buffers: `GNU Emacs`, `scratch`, and `Messages`.

*After disabling the startup message in [[level-2#Disable startup message]], the `GNU Emacs` buffer does not show up in this list.*

## Move between buffers

Switch between the `scratch` and `GNU Emacs` buffers:

```
C-x b <Enter>
```

Switch to the `Messages` buffer:

```
C-x b Messages
```

*Start typing Messages but hit tab to use tab completion.*

Quit and restart emacs. Repeat the above buffer switching, but do
not open the buffer list (skip the `C-x C-b` step). *Note buffer
switching does not require the buffer list to be open*.

Quit:

```
C-x C-c
```

## Move between windows

Start emacs:

```
emacs
```

Switch between windows:

```
C-x o
```

The `mini-buffer` says:

```
No other window to select
```

List the buffers again (just to get two windows for switching
between):

```
C-x C-b
```

And switch between the `*scratch*` and `*Buffer List*` windows:

```
C-x o
```

## Close windows

Switch to the `*Buffer List*` with `C-x o`. Close the `*Buffer
List*` window:

```
C-x 0
```

## More shortcuts in level-4

I have more keyboard shortcuts for buffers and windows in
[[level-4]].

[[level-2|Go to level 2]]
