opam-lock
=========

opam-lock is a little utility designed to dump the state of opam switches
(along with pins) and assist the user with sharing and installing these states

If you're a familiar with `opam switch {import,export}` then opam-lock is an
attempt to improve on that by adding support for git switches.`

Installation
------------

Naturally::

    $ opam install lock

Usage
-----

Create a lock file with the full state of a switch::

    $ opam lock -all > opam.lock

Create a lock file for the dependencies (transitive too) of a particular
package::

    $ opam lock -pkg cohttp > cohttp.lock

On one of my switches, this yields the following lock file::

    base64 = 2.0.0
    cmdliner = 0.9.8
    conduit = 0.12.0
    conf-m4 = 1
    cppo = 1.3.2
    cstruct = 2.1.0
    fieldslib = 113.33.03
    ipaddr = 2.7.0
    js-build-tools = 113.33.04
    magic-mime = 1.0.0
    ocamlbuild = 0
    ocamlfind = 1.6.2
    ocplib-endian = 0.8
    ppx_core = 113.33.03
    ppx_deriving = 3.3
    ppx_driver = 113.33.03
    ppx_fields_conv = 113.33.03
    ppx_optcomp = 113.33.03
    ppx_sexp_conv = 113.33.03
    ppx_tools = 5.0+4.02.0
    ppx_type_conv = 113.33.03
    re = 1.6.0
    sexplib = 113.33.03
    stringext = 1.4.2
    uri = 1.9.2

Install a set of packages from a lock::

    $ opam lock -install < cohttp.lock

Limitations
-----------

* Doesn't support all pin types that opam currently does

* A lock file that is later invalidated by updated opam package constraints
  will no longer be installable

* Gets the git hash of pin's up to 8 chars. I don't know how to get the full
  hash of a currently pinned package.
