# md-epub-kindle-test

Testing Markdown to ePub to Kindle Preview conversions and transformations using Pandoc

# Repo Purpose

The current build process for the eTextbook Boilerplate ePub fails to import into Kindle Preview - although it does successfully work for "Send to Kindle" testing.

I have not tried to upload to actual KDP yet.

So I am simplifying the content to fault find and rebuild back to the desired document.

# Research

Kindle Preview User Guide:

<https://kindlepreviewer3.s3.amazonaws.com/UserGuide320_EN.pdf>

Version used for testing in docs folder

# Build process

To convert a Markdown format to ePub for Kindle ebooks using pandoc - two options so far:

Test file for conversion is book.md which I will gradually increase the complexity of content for until Kindle Preview fails.

## VS Code Extension

Simply use the Markdown Preview Enhanced option to export ePub (requires installation of Pandoc and Calibre to work)

## Pandoc Process

The basic build process to convert a Markdown format to ePub for Kindle ebooks using pandoc:

> `pandoc book.md -o output.md`

but we want to put it into a subfolder so:

`pandoc book.md -o testing/output.md`

More complicated build process:

> `pandoc book.md -o output-toc.md --standalone --number-sections --toc --toc-depth=4`

and then run the original conversion process to get to .docx or epub:

.docx:

> `pandoc output-toc.md -o dist/output-toc.docx --standalone --number-sections --css=epub.css`

TO DO: Test .css aspect of word conversion

.ePub:

> `pandoc output-toc.md -o dist/output-toc.epub --standalone --number-sections --css=epub.css --epub-cover-image=cover.png`

# Testing

Record of testing in [testlog](testlog.md)

Record of development in response to test fails is in the [devlog](devlog.md)