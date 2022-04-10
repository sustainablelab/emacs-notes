# Clean the GUI

## Turn off GUI noise

Turn off the toolbar. But not the menubar, not yet anyway.

Before putting these in `init.el`, try these directly in Emacs.

Start Emacs:

```
emacs
```

*Emacs starts in the `scratch` buffer. I can enter Lisp here and
evaluate it.*

Type the following:

```
(scroll-bar-mode -1)
```

With the cursor *after* the closing parentheses:

```
(scroll-bar-mode -1)
                    ↑
                    └─ MAKE SURE CURSOR IS HERE,
                       AFTER THE CLOSING PARENTHESES
```

Evaluate this Lisp expression by pressing:

```
C-x C-e
```

*The scrollbars on the right-hand side of the screen go away.*

To put them back:

```
(scroll-bar-mode 1)
```

And evaluate again with `C-x C-e`.

Also try these:

```
(tool-bar-mode -1)
(tooltip-mode -1)
(set-fringe-mode 10)
```

*The expression to disable the startup page has no visible effect if
evaluated within Emacs because Emacs is already started up. But
the above Lisp expressions have a visible effect when I
evaluate them while Emacs is running.*

Quit Emacs with `C-x C-c`.

Add those Lisp expressions to `init.el`:

```lisp
(setq inhibit-startup-message t)
(scroll-bar-mode -1)
(tool-bar-mode -1)
(tooltip-mode -1)
(set-fringe-mode 10)
```

*Start Emacs and quit to confirm the expressions typed into
`init.el` are correct. Expect Emacs to open into the `scratch`
buffer with those changes in effect.*

To temporarily "turn off" any of those changes, comment them out
in the `init.el` file.

For example, to remove the menubar, add this line to `init.el`:

```lisp
(menu-bar-mode -1)
```

But leave the menu bar in for now. To comment that line out, put
a `;` at the beginning of the line:

```lisp
; (menu-bar-mode -1)
```

## Use menubar while learning

Leave the menubar visible when first learning:

- use the mouse to click on the menu bar to expand the menu to
  see what the keyboard shortcuts are
- and note that the menubar depends on the *mode*
    - the Emacs *mode* is like the Vim idea of checking the
      filetype when entering a buffer to modify behavior while in
      that buffer

## Add visible bell

Do a little border flash when a keystroke is invalid (like
attempting to move the cursor down when it is already on the last
line in the buffer).

In `init.el` (or try it out first by evaluating this expression
in the `scratch` buffer):

```
(setq visible-bell t)
```

## Change the font

Emacs has access to any system font.

I usually use Consolas.

### Lisp expression to set the font

```lisp
(set-face-attribute 'default nil :font "Consolas" :height 100)
```

Evaluate this Lisp expression to see how it looks. Bold will
automatically show up as bold; there is nothing additional to
set.

Add this expression to the `init.el` to make it a permanent
change.

### Fira Mono

I am following the **System Crafters** tutorial. He uses Fira
Mono. It's a nice looking font. I install Fira Mono on Windows.

### Download and install Fira Mono

- https://fonts.google.com/specimen/Fira+Mono
- Click `Download family`
- extract the `.zip` anywhere
- there are three fonts:

```
/cygdrive/c/msys64/home/mike/fonts/Fira_Mono/
├── FiraMono-Bold.ttf
├── FiraMono-Medium.ttf
├── FiraMono-Regular.ttf
└── OFL.txt
```

On Windows, for each `.ttf` file:

- right-click on the `.ttf`
- select `Install`

Here is the Lisp expression for `Fira Mono`:

```
(set-face-attribute 'default nil :font "Fira Mono" :height 100)
```

## Dark theme

```
(load-theme 'tango-dark)
```

# Add packages

Packages are large amounts of Emacs customization and
functionality created by the Emacs community.

Because of stranger danger, there is the issue of security: how
do I know I can trust these packages do not contain malicious
code?

Emacs uses [gpg (click to open webiste)](https://gnupg.org/), an
open source implementation of PGP. PGP (Pretty Good Privacy) is
an open standard for internet security, [rfc4880 (click to open
this standard)](https://www.ietf.org/rfc/rfc4880.txt).

## Fix gpg path to keyring

The path to the keyring is messed up on MSYS installations of
Emacs. I document here a quick way to detect the problem and how
I fixed it.

Type `M-x` (hold `Alt` key and press `x`) then `list-packages`:

```
M-x list-packages
```

This opens a `Packages` buffer with all the built-in packages.
But it also opens an `Error` buffer:

```
gpg: keyblock resource
'/home/mike/.emacs.d/c:/msys64/home/mike/.emacs.d/elpa/gnupg/pubring.kbx':
No such file or directory
```

This path is obviously messed up. Add this to `init.el`:

```lisp
;; Fix bad path for gnupg homedir
(setq package-gnupghome-dir "/home/mike/.emacs.d/elpa/gnupg")
```

- evaluate the above expression in Emacs (`C-x C-e`)
- or close Emacs (`C-x C-c`) and start Emacs again

Now `gpg` will have a valid path to the keyring:

```emacs
M-x list-packages
```

*This time the `Error` buffer does not open.*

## Install packages

Add this to the `init.el`:

```lisp
;; Initialize package sources
(require 'package)

(setq package-archives '(("melpa" . "https://melpa.org/packages/")
			 ("org" . "https://orgmode.org/elpa/")
			 ("elpa" . "https://elpa.gnu.org/packages/")))

(package-initialize)
(unless package-archive-contents
  (package-refresh-contents))

;; Initialize use-package
(unless (package-installed-p 'use-package)
  (package-install 'use-package))

(require 'use-package)
 (setq use-package-always-ensure t)
```

Try to get help on the variable  `use-package-always-ensure`.

*Put cursor on that word*, then `C-h v`.

Emacs won't recognize that variable.

Now, run the Lisp code in `init.el`:

```
M-x eval-buffer
```

Emacs will download the `package` stuff. Now Emacs recognizes the
`use-package-always-ensure` variable.

[[level-4|Go to level 4]]

