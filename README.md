# greptools
Basic replacement tool for templating things


## Usage
Edit the `frags.json` file to your content. To see the output;

`python3 htmlgrep.py $file`

Where the `$file` has been replaced with the file name. The program looks for the `frags.json` file in the current directory. You can use the `--config` flag to set where the program pulls it from.


## Theory of Operation
The program takes an input file finds and replaces items as defined in the `frags.json` config file.




## Why don't you just use X
I didn't know X existed. This started as an addition to `pandoc` as I found their filters to be way to hard to learn for the little use I was probably going to end up getting out of them. Because of this the program includes the ability to read in `pandoc` style metadata on-the-fly replacement;

With a `frags.json` like this;
```json
{"rep1":"This", "rep2":"t" }
```

And a input file like this;
```markdown
---
title: Example
author: Sam
...

Wri%rep2*2%en by %author%

%rep1% %title% was made by %author*2%

```

Will output a file like this
```markdown
---
title: Example
author: Sam
...

Written by Sam

This Example was made by SamSam

```

I use this for templating for pandoc stuff, it can be quite handy at times!