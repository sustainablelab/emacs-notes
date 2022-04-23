# UI

## Control key

`C-x` is like a Vim leader key. Unlike Vim, there are several
such leaders.

*I like the single leader and I will go back to that, but first I
want to understand how Emacs is set up*.

- `C-g` quit command
    - this is perhaps the most important keybinding to know
    - don't hit `Esc`, hit `C-g`
- `C-x`
    - `C-f` find file
    - windows
        - `o` switch between windows
        - `+` balance windows
        - `0` delete this window
        - `1` delete all other windows
        - `2` split window below
        - `3` split window right
    - frames
    - tabs
    - selection
    - undo
    - buffers:
        - `C-b` list all buffers
        - `b` switch to a buffer by name
        - `Left` previous buffer
        - `Right` next buffer
- `C-h`
    - help
        - `C-h ?` lists all help flags
            - cursor is in `Help` buffer
            - `Up/Down` or `PageUp/PageDown` to scroll help and
              see all the help flags
        - `C-h f` is `describe-function`:
            - with cursor on a function
            - `C-h f <Enter` opens the Lisp function
              documentation in the `Help` buffer

# Buffers

## List buffers

Open a window listing the buffers:

```emacs
C-x C-b
```

## Switch buffers

Switch to a buffer:

```emacs
C-x b
```

Then:

- type the name of the buffer
- or hit `<Enter>`
    - `C-x b <Enter>` toggles back and forth between *this* buffer
      and the *previous* buffer

## Types of buffers

A text file buffer is just one type of buffer. 

Buffers are used for creating interfaces. For instance, `Magit`
uses a buffer to create a Git UI.

There is a `Messages` buffer, like the Vim `:messages`.

There is a `mini-buffer` at the bottom of the screen. When I
start a command, it shows up here. For example, find file opens a
prompt in the `mini-buffer`.

I start the find file command:

```emacs
C-x C-f
```

I get this:

```
Find file: ~/
```

And my cursor is at the end of the file path where I can start
doing tab-complete to look through the files.

# Modes

The modeline is at the bottom of the window pane. At the far
right of the modeline is the mode in parentheses. I open a plain
text file and I see `(Fundamental)`.



