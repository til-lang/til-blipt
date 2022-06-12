# Blipt!

**An easy to use, intuitive and opinionated GUI library for Til.**


I have this theory that there's so many terminal (TUI) applications out
there not because everybody loves that much the terminal (although, yes,
there are definitely good reasons to), but mostly because the terminal is
*simple, universal, reliable and enduring*.

The idea of *Blipt!* is to allow developers to create GUIs **quickly**, in
an intuitive way and without fearing things will be too different in the
next few years.


## Dependencies

* https://github.com/til-lang/til-tcl

## Build

1. `make`

## Usage

```tcl
include "source/blipt.til"

# Create your Blipt! driver:
blipt.driver "teste" | autoclose | as driver

# Then you can create your document:
with $driver {
    h1 'This is the "title" -- set} in Til'
    h2 "And this is a subtitle"
    p "And this is a simple paragraph"

    h3 "Level 3 title"
    p "Another paragraph"
    p "Another paragraph"

    h4 "Level 4 title"
    p "Another paragraph"
    p "Another paragraph"
}

# And run it to show the main window:
run $driver
```
