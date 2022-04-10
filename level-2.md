# Start an `init.el`

Running Emacs for the first time **creates** a "dot" Emacs
directory in my `HOME` folder:

```
~/.emacs.d/
```

## The .emacs.d folder

The `.emacs.d` folder contains two folders:

- `auto-save-list`
- `eln-cache`

```
/cygdrive/c/msys64/home/mike/.emacs.d/
├── auto-save-list
└── eln-cache
    └── 28.1-30b185d1
        └── time-date-40951a48-90379058.eln
```

Create `init.el` in this folder.

- `.el` is an **Emacs Lisp** file
- customizations are Lisp expressions
- customizations go in `init.el`
- `init.el` runs every time Emacs starts

## Disable startup message

In `init.el`:

```lisp
(setq inhibit-startup-message t)
```

Start Emacs to see what happens, then quit.

This one-liner `init.el` disables the startup message:

- Emacs opens in the `scratch` buffer
- Emacs does not open the "GNU Emacs" buffer
    - the buffer with the GNU Emacs logo and the links

# Lisp

*A quick intro to Lisp and how to run Lisp expression
inside Emacs.*

## Lisp basics

Lisp expressions come in parentheses. The first symbol in the
parentheses is a **function** (an **operation**). The other
symbols are the arguments to that function (the **operands**).

For example, this is the Lisp way to do `1+2`:

```lisp
(+ 1 2)
```

I can use more than two operands. This is the Lisp way to do
`1+2+3`:

```lisp
(+ 1 2 3)
```

And the parentheses nest. So another Lisp way to do is `1+2+3` is
like this:

```lisp
(+ (+ 1 2) 3)
```


## Evaluate Lisp in the scratch buffer

### Evaluate one expression

Type this in the `scratch` buffer:

```lisp
(+ (+ 1 2) 3)
```

Place the cursor "at the end" of the expression. (Place the
cursor *after* the outermost closing parentheses).

```lisp
             ┌─ PUT CURSOR HERE
             │
             ↓
(+ (+ 1 2) 3)
```

Evaluate the Lisp expression:

```emacs
C-x C-e
```

The result is shown in the `mini-buffer` (the one-line buffer at
the bottom of the Emacs screen):

```
6 (#o6, #x6, ?\C-f)
```

*Try adding some blank lines after the expression and hitting `C-x
C-e` again. Expect the same result.*

```lisp
(+ (+ 1 2) 3)

 ←── PUT CURSOR HERE
```

- `C-x C-e` runs the *last* Lisp expression that comes *before*
  the cursor:
    - Emacs looks backwards from the cursor until it finds a Lisp
      expression
    - the cursor does not have to be immediately after the
      closing parentheses
    - the cursor can even be several lines below the Lisp
      expression

What if the cursor is *inside* an expression?

```lisp
          ┌─ PUT CURSOR HERE
          │
          ↓
(+ (+ 1 2) 3)
```

If the cursor is *inside* an expression, `C-x C-e` does not
evaluate that expression (it only sees what comes *before* the
cursor). This is useful for evaluating only the inner expression.

Evaluate the (inner) Lisp expression `(+ 1 2)`:

```emacs
C-x C-e
```

The result is shown in the `mini-buffer`:

```
3 (#o3, #x3, ?\C-f)
```

### Results shown in mini-buffer

What is all the other stuff shown in the result in the
`mini-buffer`?

The `3` is the expected result. The other stuff in the
parentheses `(#o3, #x3, ?\C-f)` are other number bases:

- `#o3` is `3` in octal (base 8)
- `#x3` is `3` in hexadecimal (base 16)

*And of course `3` is in decimal (base 10).*

Try evaluating a result that yields a bigger number.

```lisp
(* 8 2)
```

The result is:

```
16 (#o20, #x10, ?\C-p)
```

`16` is a better example of different number base representations
because `16` is large enough to be written differently in each
number base:

Notation | Base | Place value interpretation
-------  | ---- | --------------------------
`16`     | 10   | `(1 x 10) + (6 x 1)`
`#o20`   | 8    | `(2 x 8) + (0 x 1)`
`#x10`   | 16   | `(1 x 16) + (0 x 1)`

## Store results in variables

Type this in the `scratch` buffer:

```lisp
(setq bob 5)
(setq bigbob (+ bob 6))
```

*This sets `bob` to the value `5`, then it adds `6` and `bob` and
stores the result in `bigbob`.*

- variable `bob` does not exist until the first expression is evaluated
- variable `bigbob` does not exist until the second expression is
  evaluated

It is annoying to evaluate these expressions one at a time.

- place the cursor "at the end" of the second expression
- evaluate the second expression:

```emacs
C-x C-e
```

This throws an error. Emacs opens the `*Backtrace*` buffer to
show me where the error happened:

```
Debugger entered--Lisp error: (void-variable bob)
  (+ bob 6)
```

- the second expression uses `bob`
- but I have not evaluated the first expression yet
- so Emacs doesn't know what `bob` is

Don't move the cursor around and do `C-x C-e` to
evaluate-one-at-a-time. Evaluate every expression in this buffer.

### Evaluate all expressions

```
M-x eval-buffer
```

*There is no indication anything happened.*

Now evaluate the second expression with `C-x C-e`.

The `mini-buffer` at the bottom of the screen shows:

```
11 (#o13, #xb, ?\C-k)
```

## Evaluate Lisp in `init.el`

*`init.el` runs when Emacs starts, but there are other ways to run
`init.el`.*

First, open `init.el` in Emacs:

```emacs
C-x C-f
```

The cursor moves into the `mini-buffer` and it says:

```
             ┌─ CURSOR IS HERE
             │
             ↓
Find file: ~/
```

Type `.emacs.d/init.el`:

```
Find file: ~/.emacs.d/init.el
```

### Run entire script

*Faster than restarting Emacs*

- with the cursor anywhere in the `init.el` buffer:
    - `M-x eval-buffer`
    - this executes the entire `init.el`

### Run one expression in the script

*Test single Lisp expressions in `init.el` while editing `init.el`*

- put the cursor after any Lisp expression
    - `C-x C-e`
    - this executes the last Lisp expression before the cursor

[[level-3|Go to level-3]]
