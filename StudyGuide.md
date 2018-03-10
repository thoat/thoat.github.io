The directories beginning with an underscore: materials defining the 
basic layout and style for the site.

The [assets/](assets/) directory: non-Markdown materials for the site 
(e.g. images, example code). These files will be copied as is (i.e. 
won't be touched during the conversion).

The [pages/](pages/) directory: Markdown files that will be convered to html for 
my site.

The [\_config.yml](_config.yml) file: all sorts of configuration 
paramters (some of which I'll need to modify).

The [Rakefile](Rakefile) file: instructions for conversions - I won't 
modify this file.

The [License.md](License.md) and [README.md](README.md) files are good to have, but do not need to be on my website -- they'd just be viewed within my repo. The [\_config.yml](_config.yml) will contain a line to exclude these two files from the final site.

The header in most `.md` files says that:
* the current file is to be converted with the "page" layout
* the title
* the (optional) tagline
* the description will be converted to `<meta name="description" content="...">`which may be used in google search results.

When you hyperlink to any Markdown-pages e.g. those in [\_includes/](\_includes/), use a `.html` extension rather than `.md`.  
