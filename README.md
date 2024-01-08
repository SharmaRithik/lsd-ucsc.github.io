Languages, Systems, and Data Lab at UC Santa Cruz
-------------------------------------------------

Website for the Languages, Systems, and Data Lab at UC Santa Cruz.

This website is largely based on [the Cornell PL website](https://github.com/cornell-pl/pl.cs.cornell.edu), with special thanks to 
[Rachit Nigam](https://rachitnigam.com) for technical and moral support!

## Hosting

The LSD website available at <https://lsd-ucsc.github.io/> and mirrored with some delay at <https://lsd.ucsc.edu/>. If you ever notice discrepancies between these, please make an issue.

* Jan 2024 - We noticed that the mirroring wasn't working. Changes made on Jan 3rd were visible immediately on <https://lsd-ucsc.github.io/> but as of Jan 7th were not visible at <https://lsd.ucsc.edu/>. The ticket [INC1800159](https://slughub.ucsc.edu/its?sys_id=bf46e8ee1b2bf990931886e0604bcbe2&view=sp&id=ticket&table=incident) tracks this issue.
* Dec 2023 - UCSC hosting for the website website switched from ITS hosting on AFS to a new AWS host. We discussed how to mirror and struck an agreement in ticket [INC1792531](https://slughub.ucsc.edu/its?id=ticket&table=incident&sys_id=c418fd681b13f510e8c5eb93604bcb70) that UCSC would run a cron-job on their server to mirror the site from <https://lsd-ucsc.github.io/> to <https://lsd.ucsc.edu/>. If there's ever a discrepancy betwen those two URLs, we need to ask someone at UCSC to take a look at the cron-job.

## Making changes to the public site

Change the public website in three steps!

1. Change the markdown files and commit your changes to the `main` branch.
1. Push your changes back to the repository. No pull request is necessary. If you prefer to use a pull request, please notify someone in the casl-group mailing list.
    * Any changes made to the `main` branch will be reflected in the public site after CI/CD runs.
    * The `public` branch of this repo may be viewed at <https://lsd-ucsc.github.io/>.
1. Check that your commit results in a :heavy_check_mark: build status and not a :x: build status! ![](.build-status-example.png)
    * You can find the build status for your commit
      at the top of the [repo page](https://github.com/lsd-ucsc/lsd-ucsc.github.io)
      or on the [commit log](https://github.com/lsd-ucsc/lsd-ucsc.github.io-source/commits/main)
      or find details of the run on the [workflows](https://github.com/lsd-ucsc/lsd-ucsc.github.io-source/actions) page.
    * If you're unsure of whether your changes will build, then push to a new branch and make a pull request (please notify someone in the casl-group mailing list to check your pull request).
1. Your changes will appear at <https://lsd-ucsc.github.io/> when the build status is a :heavy_check_mark: and will be mirrored at <https://lsd.ucsc.edu/> after approximately one hour.

You don't need to install hugo because the public site has CI/CD set up. To see how to [build the site locally](#building-the-site-locally), click or scroll to the bottom.

## Content Mangement

Most of the content is stored under `/content/home`.

- **about.md**: Content for the About widget on the home page.
- **news.md**: Latest news about the group. To add a new news item, use the
  format from the other items. Since the `[[news]]` list is ordered, make sure
  that the item is added to the top.
- **faculty.md**, **students.md**, **alumni.md**...: Content for various groups
  of members.

### Adding news items

Edit the [news file][news] using one of the formats.
See the examples in the file.

[news]: content/home/news.md

### Adding a new person

You'll need the person's name as they want it to appear, title (e.g., "Ph.D. Student", "Assistant Professor", etc.), optionally a photo, and optionally a website URL.  If you don't provide a photo, a default image will appear.

Edit `content/home/faculty.md` or `content/home/students.md` and follow the format of existing entries.  If the person has a photo, add it to the `static/img/` directory.

### LSD Seminar

To create a new LSD Seminar page:

```
hugo new lsd-seminar/<term>.md
```

where `<term>` is of the form `2020fa`.

Next, edit the file generated in `content/lsd-seminar/<term>.md` and update the
link in `config.toml` for `lsd-seminar` to point to the latest webpage.

## Styling

The styling templates are stored under `layouts/`. Hugo uses a priority-based
override method for determining which template to use. By default, it uses
the template from `theme/academic/layouts` **unless** there is another template
of the same name (and directory structure) in `layout/`.

For example, if you want to override the styling in
`theme/academic/layout/foo/bar.html`, simply copy it to `layout/foo/bar.html`
and add your changes.

## Building the site locally

The website is generated by the [Hugo][hugo] website generator and uses the
[Academic][academic] theme. The theme is stored as a submodule under
`themes/academic/`.  We use an older version of the Academic theme, before it morphed into Wowchemy.  (Don't update the theme submodule unless you know what you're doing.)

1. Recursively clone the repository:
   ```
   git clone --recurse-submodules git@github.com:lsd-ucsc/lsd-ucsc.github.io-source.git
   ```
2. Install [Go][go] (`ver >= 0.49.2`) and [Hugo][hugo] (`ver >= 1.11 && ver <= 49.2`). **Note**: The website will not build with newer versions of Hugo.

3. Run `hugo server -w` to generate and serve the website locally.

[hugo]: https://github.com/gohugoio/hugo/releases/tag/v0.49.2
[go]: https://golang.org/
[academic]: https://github.com/gcushen/hugo-academic
