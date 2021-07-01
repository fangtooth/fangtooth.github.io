---
title: "About Jekyll and Github Pages"
tags: usage jekyll
---

# Jekyll + Github Pages usage

How to use Jekyll for github-pages? Well, here is a summary.



### Understanding project structure

#### Posts

[Posts][jekyll-docs-posts] goes into the `_posts` directory.

Jekyll requires blog post files to be named according to the following format: `YEAR-MONTH-DAY-title.MARKUP`
Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary [front matter][jekyll-docs-front-matter].



### Build, run and debug

You can rebuild the site in many different ways, but the most common way is to run `bundle exec jekyll serve --drafts`, which launches a web server and auto-regenerates your site when a file is updated.

#### Run the server
```sh
bundle exec jekyll serve --drafts
```

#### Issues on Windows
For Windows, do this if the server does not works

```sh
gem uninstall eventmachine
# (uninstall all versions)
gem install eventmachine --platform ruby
code C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/eventmachine-1.2.7-x64-mingw32/lib/eventmachine.rb
# add this line `require 'em/pure_ruby'` at the beggining
```



### Project management

#### To update to the latest github dependencies

```sh
bundle update
```

#### Get location of gem files

```sh
bundle info --path <gem>
# e.g. bundle info --path minima
# e.g. bundle info --path jekyll-theme-midnight
```

#### To list current versions of github-pages

```sh
bundle exec github-pages versions
# online list here: https://pages.github.com/versions/
```



### Reference links

#### Guides
- [Setting up a site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
- [Posts][jekyll-docs-posts]
- [Markdown options](https://jekyllrb.com/docs/configuration/markdown/)
- [About Front Matter in Jekyll][jekyll-docs-front-matter]
- [Jekyll docs](https://jekyllrb.com/docs/)

#### Themes
- [minima, the dafault theme](https://github.com/jekyll/minima)
- [midnight, the theme I'm using here](https://github.com/pages-themes/midnight)

#### APIs for site development
- [Jekyll themes](https://jekyllrb.com/docs/themes/)
- [Jekyll global metadata](https://jekyllrb.com/docs/variables/)
- [site.github metadata](https://jekyll.github.io/github-metadata/site.github/)
- [Jekyll custom filters](https://jekyllrb.com/docs/liquid/filters/)
- [Liquid filters](https://shopify.github.io/liquid/)

#### Other links
- [Github pages, latest versions list](https://pages.github.com/versions/)



[jekyll-docs-posts]: https://jekyllrb.com/docs/posts/
[jekyll-docs-front-matter]: https://jekyllrb.com/docs/front-matter/
