# Winmerge line filter for empty XML Tags

After changing the XML implementation in one of our projects, I used Winmerge to check that the XML output did not change. But Winmerge reported differences for several thousand of the generated XML files. When I looked at the differences reported, it turned out that the new code generated the short-circuit form for empty XML tags:

* old: `<tag></tag>`
* new: `<tag/>`

This is an acceptable change for our project, but how to tell nothing else changed? Winmerge supports line filters based on perl compatible regular expressions (PCRE).

The line filter to ignore different syntax for empty XML tags is this:

`<([a-zA-Z][a-zA-Z0-9]*\b)((\/)|(><\/\1))>`

I hope this will help others as I did not find this anywhere else on the net.
