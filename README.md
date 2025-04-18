# Metadata
## How and what
A werc app that provides a library of utility functions for getting metadata. Intended to be used alongside other werc apps

To enable the metadata tool, add `conf_enable_metadata` to your site's `_werc/config` file. IMPORTANT: You should put this at the top level `_werc/config` file, and as the first line in it. This app needs to initialise before any werc apps that depend on it.

To add metadata to a page...
```
<!---METADATA
title=Bladerunner
description=blah
rating=10
tags=Movies,Films,TV,Entertainment
--->
# Header

rest of the page goes here...
```
Note that`<!---METADATA` and `--->` on their own lines.
Note that these HTML comments use 3 dashes as opposed to 2.

Note the lack of spaces between the = sign. You cannot use an = sign in a metadata key, but spaces and other characters should work fine. Unicode characters might work too, but I haven't tested this.

Wherever you wish to get the metadata, you call
`get_metadata title` where title is replaced with your key. This is case sensitive.

Wherever you wish to set the metadata, you call:
`set_metadata title titlename site/risingthumb.xyz/index.md`
The 3rd parameter is optional for this, if it's not set, it will use the currently open file as defined in `$local_file` variable

`metadata_table` is also provided as a utility function that allows you to get a full table of all metadata keys and values. Intended for debug purposes. Commented out in the init is adding this to the footer

## Todo
- Not 100% on the way I write the metadata with the metadata function. I don't think the seds stop fields that can break it, but for now, just avoid weird characters
- Make the metadata table adding a debug option
- Rewriting parts of goralog to depend on this lib
