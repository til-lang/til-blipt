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
    # (I'm using weird character to show that
    # you don't need to worry about how Tcl
    # is going to interpret the strings:)
    h1 'This is the "title" -- set} in Til'

    h2 "And this is a subtitle"
    p "And this is a simple paragraph"

    h3 "Level 3 title"
    p "Another paragraph"
    p "Another paragraph"

    h4 "A clock:"

    # You can use some Tk things directly, also:
    tk "ttk::label .special_paragraph -text 0 -background LemonChiffon2"
    add_window ".special_paragraph"
    br

    register_command teste {
        extract [exec date "+%H:%M:%S" | collect] 0 | as time
        tk $driver ".special_paragraph configure -text {$time}"
        run_after $driver 1000 teste
    }
    run_after 1000 teste
}

# And run it to show the main window:
run $driver
```

![screenshot of the result](https://user-images.githubusercontent.com/8899756/173213611-a2acdb84-0f38-49dd-997b-9a79173f15f0.png)
