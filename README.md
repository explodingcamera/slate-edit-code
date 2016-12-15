# slate-edit-code

[![NPM version](https://badge.fury.io/js/slate-edit-code.svg)](http://badge.fury.io/js/slate-edit-code)
[![Linux Build Status](https://travis-ci.org/GitbookIO/slate-edit-code.png?branch=master)](https://travis-ci.org/GitbookIO/slate-edit-code)

A Slate plugin to handle edition of code blocks.

### Install

```js
npm install slate-edit-code
```

### Features

- Pressing <kbd>Enter</kbd> insert a new line starting with the right indentation
- Pressing <kbd>Tab</kbd> insert the right indentation if selection is collapsed or indent all lines in selection
- Pressing <kbd>Delete</kbd> remove the indentation before cursor if possible
- Pressing <kbd>Command+Enter</kbd> (<kbd>Ctrl+Enter</kbd> on Windows/Linux) exits the code block
- Pressing <kbd>Command+A</kbd> (<kbd>Ctrl+A</kbd> on Windows/Linux) select all the text in the block

### Structure

This plugin uses the following structure for code blocks:

``` yaml
nodes:
  - kind: block
    type: code_block
    nodes:
      - kind: block
        type: code_line
        nodes:
          - text: "A code block is made of..."
      - kind: block
        type: code_line
        nodes:
          - text: "...several code lines"

```

### Simple Usage

```js
import EditCode from 'slate-edit-code'

const plugins = [
  EditCode()
]
```

#### Options arguments

- ``[containerType: String]`` — The type of the code containers
- ``[lineType: String]`` — The type of the code lines
- ``[shiftEnterBlockType: String]`` — Shift+Enter will exit the code container, into the given block type. Pass `null` to not handle this case.
- ``[selectAll: Boolean]`` — True to select all code inside a code container on <kbd>Command+A</kbd>