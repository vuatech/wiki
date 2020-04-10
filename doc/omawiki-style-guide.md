---
title: OpenMandriva wiki specific style guide
description: 
published: true
date: 2020-03-13T18:13:46.565Z
tags: 
---

# OpenMandriva wiki specific style guide
> Read first [general wiki style guide](/en/doc/wiki-style-guide)
{.is-danger}

## OpenMandriva wiki specific rules

> This page is a work in progress, it will be updated over time as soon as I find any reason to add more hints.
{.is-info}


### Images
Screenshots and common images which are inserted in wiki pages must be uploaded **only** to `/images` folder.
It is what the folder has been created for.

Images file name should not contain:
- Space (use dashes instead)
- Underscore (use dashes instead)
- Period (reserved for file extensions)
- Unsafe URL characters (such as punctuation marks, quotes, math symbols, etc.)

When at all possible, rename your image filename to something meaningful related to the page or to what you are showing.

### Paths
Paths  must be lowercase. Use dashed to separate the words.
No punctuation allowed except dashes/hyphens and/or underscores.
-- Note: even if *technically* permitted, OpenMandriva wiki standard is to use dashes instead of underscores.
No need for full title of the page in the path: it can, and should when possible, be shortened.

Paths cannot contain the following characters:
- Space (use dashes instead)
- Period (reserved for file extensions)
- Unsafe URL characters (such as punctuation marks, quotes, math symbols, etc.)

As we often have to write release version number (4.0, 4.1, 4.2, etc.), while creating new pages just convert it into `40`, `41`, `42`, etc. by omitting the dot in the path.

If the page is called "*How to foo bar whatever*" the path must be `/doc/guides/howto-something`
No `how-to`, no `howtos`, no `how-tos`, etc.
  

  


