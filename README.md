# doqmnt - Auto-documentation in Emacs for programmers.
Doqmnt (pronounced: "document") is a free library for Emacs that assists with source code documentation for programmers.

Currently doqmnt only supports a pre-configured doxygen format. We hope to upate this later to include more documentation standards (e.g., Javadoc), and more flexible formatting of documentation.

## Motivation
It was developed by Joshua T. Guerin, Ph.D. and Kathleen Ericson, Ph.D. at the University of Tennessee at Martin for use in our programming course. Our hope is to aid in the documentation/development process by reducing overall keystrokes and workload of creating documentation.

And you are correct--documentation is not hard, but many students tend to view documentation as something to slap on your code at the end so you don't lose points. By simplifying and standardizing the process we hope to make the documentation process easy enough that students will want to engage in writing proper documentation *as they code*.

Doqmnt is not just meant for students/academic use--we hope to one day have the project mature enough that programmers in the wild may discover it and choose to use it.

## Installation
At the moment doqmnt is only located in this github repository (i.e., not in melpa) due to its immaturity. This may change over time.

There are only three steps to install on most *nix systems, and the process is fairly similar for most free-standing .el files.

**1. Download the .el file, and put it somewhere safe on your system.**

At the moment we are installing doqmnt on a per-user basis, and we are adding it to `~/.emacs.d/include`.

**2. Update your .emacs file to add the directory to your load path, load the doqmnt.el**

The following lines of code added to your .emacs file should do the trick:

```
; Add .emacs.d to load path
(add-to-list 'load-path "~/.emacs.d/include")

; Load doqmnt.el on load of Emacs
(load "doqmnt.el")
```

If you chose to put doqmnt somewhere other than `~/.emacs.d/include` you can change the above to reflect the correct directory.

## Usage
If Emacs loads happily after installation, it is likely that doqmnt will work.

Doqmnt implements the following commands, that are accessible with "M-x command".

`file-doq`
- Should be ran at the top of a source file.
- Adds a pre-configured header comment, scraping what information it can from the system (e.g., user name, date).

`fun-doq`
- Should be ran on the line containing a prototype for a function.
- Generates a pre-configured function/method comment *after* the prototype.
- Should return cursor to the correct starting point in the buffer after execution.
- Does not need to be ran at the start of the line--can be anywhere within the line.
- Currently works only with C/C++/Java style prototypes.
- Parses the line and extracts whatever relevant information exists.
 - E.g., Function identifier, return value, parameter list.

All implemented commands currently work in an interactive mode we are developing. The minbuffer will prompt the user for information that cannot be generated automatically by the system (e.g., descriptions of items). You can type up an entry and simply hit `return` or `enter` to move on to the next. The documentation is generated automatically, in pieces until the function is done running.

