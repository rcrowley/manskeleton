manskeleton(1) -- build skeleton man paths
==========================================

## SYNOPSIS

`manskeleton` [`-1`] [`-2`] [`-3`] [`-4`] [`-5`] [`-6`] [`-7`] [`-8`] [`-d` _dirname_] [`-e` _extension_]

## DESCRIPTION

Builds a skeleton directory and makefiles for turning `ronn`(1)-compatible markdown files into man pages.  Desired sections are given as command line options.  If more sections become necessary later, it is safe to re-run `manskeleton` with more options.

## OPTIONS

* `-1`, `-2`, `-3`, `-4`, `-5`, `-6`, `-7`, `-8`:
  Build a skeleton directory and Makefile for the numbered section.
* `-d` _dirname_:
  Build starting at _dirname_.  Defaults to the current directory.  A directory called _man/_ will be created within this directory.
* `-e` _extension_:
  File extension used for `ronn`(1)-compatible markdown files.  Defaults to _md_ because GitHub renders files with this extension.

## EXAMPLES

The directory structure build by `manskeleton` will allow gems and other packages installed in non-standard locations to provide man pages by tweaking your manpath.  Setting the `MANPATH` environment variable will do but you'll have to re-run this command each time you need to add to your manpath.

    export MANPATH=$(for MAN in /var/lib/gems/1.8/gems/*/man; do echo -n :$MAN; done)

A better, though slower, solution is to alias `man`(1) to recalculate your manpath at each invocation.

	alias man='man --manpath=$(echo -n $(manpath); for MAN in /var/lib/gems/1.8/gems/*/man; do echo -n :$MAN; done)'

## AUTHOR

Richard Crowley <r@rcrowley.org>

## SEE ALSO

`manskeleton`'s source code is available at <http://github.com/rcrowley/manskeleton>.

`ronn`(1) is used by the generated makefiles to render man pages: <http://github.com/rtomayko/ron>

`gem-man`(1) inspired this program and provides an alternative to the environment-based method above for finding man pages in non-standard locations: <http://github.com/defunkt/gem-man>
