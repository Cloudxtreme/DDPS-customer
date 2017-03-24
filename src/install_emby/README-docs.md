
# Docs - where to put what

The project template_ may also be used as a boiler template for writing
documentation in [markdown](https://daringfireball.net/projects/markdown/), see
the [article](https://en.wikipedia.org/wiki/Markdow) on Wikipedia on syntax
etc.

The _docs_ directory has the following structure adopted from
[TextBundle](textbundle.org):

  - **assets/CSS**: CSS for generating html and pdf files
  - **assets/img**: Images for your files
  - **media-source**: Image source if the image is created in e.g an OS X application

Compilation from markdown to other formats may be achieved using ``make`` - provided
the correct compilers are installed.
 
#### Notice about this documentation

The text is written in [markdown](https://en.wikipedia.org/wiki/Markdown) and
rendered to html with [mulitmarkdown](fletcherpenney.net/multimarkdown) using
an internal [css](https://en.wikipedia.org/wiki/Cascading_Style_Sheets),
converted to pdf with [wkhtmltopdf](http://wkhtmltopdf.org) while the images
currently are made with [diagramix](diagrammix.com), an inexpensive OS X software.
Everything is kept in [textbundle format](textbundle.org) and lives within the
[git server of ssi.i2.dk](http://gitlab.ssi.i2.dk).

