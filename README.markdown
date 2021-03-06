# HaRe : The Haskell Refactorer


[![Build Status](https://secure.travis-ci.org/alanz/HaRe.png?branch=master)](http://travis-ci.org/alanz/HaRe)

## Getting Started

    cabal install HaRe

Check that it works from the command line

    $ ghc-hare --version
    0.7.0.0

Running the bare command lists available refactorings and their parameters

### Emacs integration

Currently only emacs integration is offered. Add the following to your ~/.emacs

    (add-to-list 'load-path
        "~/.cabal/share/HaRe-0.7.0.0/elisp")
    (require 'hare)
    (autoload 'hare-init "hare" nil t)

Add an intializer hook to the ghc-mode command

    (add-hook 'haskell-mode-hook (lambda () (ghc-init) (hare-init) (flymake-mode)))

Alternatively, if using haskell-mode, and initializing via a function

    ;; Haskell main editing mode key bindings.
    (defun haskell-hook ()

      ;(lambda nil (ghc-init) (flymake-mode))
      (ghc-init)
      (flymake-mode)
      (hare-init)
      ...
    )

If this is done correctly, there should be an additional `Refactorer`
menu entry when opening a haskell file. The refactorings can be
initiated via the menu, or using the keyboard shortcuts displayed in
the menu.

The installation can be fine-tuned using

    M-x customize-variable

on

    hare-search-paths
    ghc-hare-command


Each refactoring will first ask for any information it requires, e.g.
a new name if renaming, and then attempt the refactoring. If any
precondition is not met this will be reported and the refactoring will
abort.

If it succeeds, you will be given the option to look at an ediff
session to see what changes would be made, and each file can be
individually accepted or declined.

If the refactoring is commited, the original file is renamed to have a
suffix containing the current timestamp.

E.g., after renaming in Foo.hs, there will be two files

    Foo.hs
    Foo.hs.2013-08-22T19:32:31+0200

This allows a sequence of refactorings to be undone manually if
required. In theory.




## Development & Support

Join in at `#haskell-refactorer` on freenode.

### Running test suite

To run the test suite do:

    cabal configure --enable-tests && cabal build && cabal test

See http://hspec.github.com/ for details on hspec

see http://travis-ci.org/#alanz/HaRe for continuous build results

## Coding style

Contributors: please try to follow https://github.com/tibbe/haskell-style-guide
Note:A consistent coding layout style is more important than what specific on is used.

## Contributors

 * Christopher Brown
 * Huiqing Li
 * Alan Zimmerman
 * Many others, ..

