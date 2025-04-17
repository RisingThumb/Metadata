# Metadata
## How and what
A werc app that provides a library of utility functions for getting metadata. Intended to be used alongside other werc apps

To enable the metadata tool, add `conf_enable_metadata` to your site's `_werc/config` file. IMPORTANT: You should put this at the top level `_werc/config` file, and as the first line in it. This app needs to initialise before any werc apps that depend on it.

To add metadata to a page...
```
---
title=Bladerunner
description=blah
rating=10
tags=Movies,Films,TV,Entertainment
---
# Header

rest of the page goes here...
```
Note the lack of spaces between the = sign. You cannot use an = sign in a metadata key, but spaces and other characters should work fine. Unicode characters might work too, but I haven't tested this.

Wherever you wish to get the metadata, you call
`get_metadata title` where title is replaced with your key. This is case sensitive.

`metadata_table` is also provided as a utility function that allows you to get a full table of all metadata keys and values. Intended for debug purposes.

## Todo
- Writing back metadata. Can already be done by manually editing the file with dirdir
- Adding something to trim out the --- enclosed metadata from the page. This may have to be an extended awk script? Explore options.
- Rewriting parts of goralog to depend on this lib
