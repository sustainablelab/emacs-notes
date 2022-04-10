# Screen

Split screen into three panes:

```screen
┌──────────┬─────────┐
│ MARKDOWN │  GRAPH  │
│ FILE     │  VIEW   │
│          │         │
│          │         │
│          ├─────────┤
│          │ OUTLINE │
│          │         │
└──────────┴─────────┘
```

## Pin GRAPH VIEW

- GRAPH VIEW remains open:
    - click on a node
    - the file opens in the MARKDOWN FILE pane

## Link OUTLINE to MARKDOWN FILE

- OUTLINE is tied to the MARKDOWN FILE pane:
    - OUTLINE continues to show the outline of the MARKDOWN FILE,
      even when MARKDOWN FILE is not the active pane

## JSON

The screen layout is defined in `.obsidian/workspace`.

Here is a summary of `workspace`:

```json
{
+ "main": {---------------- split into three panes:
                            "markdown" ("file": "bob.md"),
                            "outline" ("file": "bob.md"),
                            "graph" ("pinned")
+ "left": {---------------- "collapsed" and split into two tabs:
                            "file-explorer" and "search"
+ "right": {--------------- "collapsed" and split into two tabs:
                            "backlinks" and "tags"
  "active": "ID-of-active-pane in main"
+ "lastOpenFiles": [----------------
  ]
}
```

This says the Obsidian GUI is split into three areas: `main`, `left`, and
`right`.

*Users further separate the `main` area into panes.*

- I split the `main` area into three panes
    - `Alt` + Arrow key to select which `main` pane is "active"
- I leave the `left` and `right` areas collapsed:
    - `Ctrl`+`Alt`+`Left`
        - toggle `left` collapsed/opened
        - *file-explorer* and *search*
    - `Ctrl`+`Alt`+`Right`
        - toggle `right` collapsed/opened
        - *backlinks* and *tags*

