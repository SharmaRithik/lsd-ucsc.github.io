Languages, Systems, and Data Lab @ UCSC website
-----------------------------------------------

Website for the Languages, Systems, and Data Lab @ UCSC website.

This website is largely based on [the Cornell PL website](https://github.com/cornell-pl/pl.cs.cornell.edu), with thanks to 
[Rachit Nigam](https://rachitnigam.com)!

## Pre-requisites

The website is generated by the [Hugo][hugo] website generator and uses the
[Academic][academic] theme. The theme is stored as a submodule under
`themes/academic/`.  We use an older version of the Academic theme, before it morphed into Wowchemy.

1. Recursively clone the repository:
   ```
   git clone --recurse-submodules https://github.com/cornell-pl/pl.cs.cornell.edu.git
   ```
2. Install [Go][go] (ver >= 0.49.2) and [Hugo][hugo] (ver >= 1.11 && ver <= 49.2). **Note**: The website will not build with newer versions of Hugo.  You can probably get a prebuilt binary of Hugo 49.2 for your machine [here](https://github.com/gohugoio/hugo/releases/tag/v0.49.2).

3. Run `hugo server -w` to generate the website locally.

[hugo]: https://gohugo.io/
[go]: https://golang.org/
[academic]: https://github.com/gcushen/hugo-academic

## Adding news items

In two easy steps!

1. Edit the [news file][news] using one of the formats.
2. If you don't have write access, create a pull request and tag @lkuper. If you do, just merge! The website automatically rebuilds and redeploys on each push.

[news]: https://github.com/lsd-ucsc/lsd-ucsc.github.io-source/edit/master/content/home/news.md

If it's a new paper and you want the author's name to link to their web page, edit `layouts/partials/authors.html`.

## LSD Seminar

To create a new LSD Seminar page:

```
hugo new lsd-seminar/<term>.md
```

where `<term>` is of the form `2020fa`.

Next, edit the file generated in `content/lsd-seminar/<term>.md` and update the
link in `config.toml` for `lsd-seminar` to point to the latest webpage.


## Content Mangement

Most of the content is stored under `/content/home`.

- **about.md**: Content for the about widget.
- **news.md**: Latest news about the group. To add a new news item, use the
  format from the other items. Since the `[[news]]` list is order, make sure
  that the item is added to the top.
- **faculty.md**, **students.md**, **alumni.md**...: Content for various groups
  of members.


## Styling

The styling templates are stored under `layouts/`. Hugo uses a priority-based
override method for determining which template to use. By default, it uses
the template from `theme/academic/layouts` **unless** there is another template
of the same name (and directory structure) in `layout/`.

For example, if you want to override the styling in
`theme/academic/layout/foo/bar.html`, simply copy it to `layout/foo/bar.html`
and add your changes.