manskeleton(1) -- build skeleton man paths
==========================================

## SYNOPSIS

`manskeleton` [`-1`] [`-2`] [`-3`] [`-4`] [`-5`] [`-6`] [`-7`] [`-8`] [`-d` _dirname_] [`-e` _extension_]

## DESCRIPTION

Builds a skeleton directory and makefiles for turning `ron`(1)-compatible markdown files into man pages.  Desired sections are given as command line options.  If more sections become necessary later, it is safe to re-run `manskeleton` with more options.

The directory structure build by `manskeleton` will allow gems and other packages installed in non-standard locations to provide man pages by setting `MANPATH`:

    export MANPATH=$(for MAN in /var/lib/gems/1.8/gems/*/man; do echo -n :$MAN; done)

## OPTIONS

* `-1`, `-2`, `-3`, `-4`, `-5`, `-6`, `-7`, `-8`:
  Build a skeleton directory and Makefile for the numbered section.
* `-d` _dirname_:
  Build starting at _dirname_.  Defaults to the current directory.  A directory called _man/_ will be created within this directory.
* `-e` _extension_:
  File extension used for `ron`(1)-compatible markdown files.  Defaults to _md_ because GitHub renders files with this extension.

## AUTHOR

Richard Crowley <r@rcrowley.org>

## SEE ALSO

<http://github.com/rtomayko/ron>
