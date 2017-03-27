#
# Generic Makefile for (multi)-markdown to html and pdf projects
# Usage:
#
#	- Create your (part of the) project in e.g. my-text.mmd (make my-text.mmd) and edit as reqired. Add files to the Files section
#	- Build your html or pdf document (my-text.pdf) with ``make my-text.pdf``
#   - pdf requires wkhtmltopdf, while html requires multimarkdown. Both applications are installed on office and buh
#  

date	= `date`
version	= `git describe --long --dirty --tags --always`
author	= Niels Thomas Haugård

# Default css: black text, blue headers, automatic numbering
css		= assets/CSS/nth2-number.css

# Syntax highlighting - see https://highlightjs.org
html_header = <link rel=\"stylesheet\" href=\"assets/CSS/default.min.css\"> <script src=\"assets/CSS/highlight.min.js\"></script> <script>hljs.initHighlightingOnLoad();</script>
html_header = <link rel=\"stylesheet\" href=\"assets/CSS/grayscale.css\"> <script src=\"assets/CSS/highlight.min.js\"></script> <script>hljs.initHighlightingOnLoad();</script>
html_header = <link rel=\"stylesheet\" href=\"assets/CSS/googlecode.css\"> <script src=\"assets/CSS/highlight.min.js\"></script> <script>hljs.initHighlightingOnLoad();</script>

%.mmd:
	# heredoc doesn't work in Makefile
	echo "Title:  Status"		>	$@
	echo "Subtitle:Status"		>>	$@
	echo "Author:  $(author)"	>>	$@
	echo "Date:   $(date)"		>>	$@
	echo "Version: $(version)"	>>	$@
	echo "ShortTitle: D"		>>	$@
	echo "Series:  SSI"			>>	$@
	echo "SeriesIndex:"			>>	$@
	echo "Tags: SSI"			>>	$@
	echo "Cover: coverpage.pdf"	>>	$@
	echo "CSS:  $(css)"			>>	$@
	echo "html header: $(html_header)" >> $@
	echo "Files: $<"			>>	$@

%.html: %.md %.mmd Makefile $(css)
	cat $(addsuffix .mmd, $(basename $<)) $< | multimarkdown --output=$(addsuffix .html, $(basename $<))

%.pdf: %.html #%.md %.mmd
	wkhtmltopdf	--margin-top 15 --margin-left 15 --margin-right 15								\
				--margin-bottom 20 																\
				--print-media-type 																\
				$< --enable-internal-links --footer-font-name Ariel								\
				--footer-font-size 8 --footer-spacing 2											\
				--footer-line																	\
				--footer-left "[isodate] [time] $(version)" 									\
				--footer-right 'Page [page] of [topage]' $(addsuffix .pdf, $(basename $<))
				if [ -f coverpage.pdf ]; then pdfunite coverpage.pdf $(addsuffix .pdf, $(basename $<)) $(basename $<)-with-coverpage.pdf;	\
				/bin/mv $(basename $<)-with-coverpage.pdf $(addsuffix .pdf, $(basename $<));	\
				fi

.SILENT:

.IGNORE:


