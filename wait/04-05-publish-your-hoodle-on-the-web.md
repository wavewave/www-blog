---
title: publish your hoodle on the web 
tags: hoodle, haskell 
---

One of the newest potential killer features of hoodle is that hoodle can have hyperlinks to other hoodle 
documents. Recently, I made a utility called <code>hoodle-publish</code> for publishing hoodle files to 
pdf files preserving the links. <code>hoodle-publish</code> takes a directory as an argument and 
transforms all the hoodle files in the directory recursively to pdf files and interlinks files by 
URL with a designated URL base. It is currently a separate command line utility (Later, this will also be
incorporated into a submenu in hoodle main program ),  so that one can use it by <pre> <code>> hoodle-publish (urlbase) (hoodledir) (pdfdir) </code> </pre>
where <code>(urlbase)</code> is the URL base for the publication, <code>(hoodledir)</code> is 
the directory in which hoodles files to be published are present, and <code>(pdfdir)</code> is 
the directory to which generated pdf files will be located. The source code can be found at ....

The implementation of this feature became possible thanks to an excellent pdf manipulating library 
[<code>pdf-toolbox</code>](https://github.com/Yuras/pdf-toolbox). Thank Yuras. 

For the sake of presentation, my wife made a sample hoodle publication. It's about ..... Check this
URL : 


Hoodle is now the simplest publishing program with your own handwriting. Now you can publish articles, 
doodles, free-form documents and whatever with your unique character. One may use it as a personal
diary or blog, or a personal quick-scratch information database in a wiki-like form 
as one wishes.  

Enjoy!

p.s. I also plan to implement publishing hoodle directly to html. Tagging and some other useful features 
are under consideration. Stay tuned!

