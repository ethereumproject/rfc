GitBook COSS
============

This plugin is used to generate [COSS-compatible protocols](http://rfc.unprotocols.org/2/).

It will prepend specification title to every specification and produce links
in the following forms:

* /spec:NN
* /spec:NN/NAME
* /NN (shortcut form)
* /NAME

It will also use YAML front matter to populate specification metainformation, unless `noinsert` is specified in the front matter.
