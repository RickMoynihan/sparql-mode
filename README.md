# What is it?

A major mode for emacs that provides syntax highlighting for
[SPARQL](http://www.w3.org/TR/sparql11-query/). It also provides a way
to execute queries against a SPARQL HTTP endpoint, such as is provided
by [Fuseki](http://jena.apache.org/documentation/serving_data/). It is also possible to query
other endpoints like [DBPedia](http://dbpedia.org/sparql).

# Getting Started

* Download sparql-mode and put it in a directory somewhere.
* Add the following to your .emacs file

```elisp
(add-to-list 'load-path "/path/to/sparql-mode-dir")
(autoload 'sparql-mode "sparql-mode.el"
  "Major mode for editing SPARQL files" t)
(add-to-list 'auto-mode-alist '("\\.sparql$" . sparql-mode))
```

Now sparql-mode will load whenever you visit a file whose name ends
with .sparql. Alternatively, run `M-x sparql-mode` in an existing
buffer containing SPARQL commands.

It is also possible to add
```
# -*- mode: sparql -*-
```
to the top of the file. This is a comment read by emacs to discover
what mode to use.

## Auto-compete mode
SPARQL-mode now also supports auto-complete-mode. Just add

```elisp
(add-to-list 'ac-dictionary-files "/path/to/sparql-mode-dir/sparql-mode")
(add-hook 'sparql-mode-hook 'auto-complete-mode)
```

# Executing SPARQL Queries from within Emacs

From a buffer that is in sparql-mode, execute `M-x
sparql-query-region`. You will be prompted for a SPARQL HTTP endpoint
in the minibuffer, which defaults to `http://localhost:2020/`. Once
set, it will be used for all subsequent queries in that buffer.
Results will be displayed in another buffer in CSV format.

# Bugs and Enhancements

sparql-mode is currently very young, and lacks a lot of features that
I'd like it to have. If you have a problem or would like to see it get
better in a specific way, feel free to drop an issue in
[the issue tracker](https://github.com/ljos/sparql-mode/issues).
Enjoy!
