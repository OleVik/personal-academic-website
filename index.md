---
title: "Home"
summary: "About this page."
date: 2016-04-13
layout: default
---

A skeleton-site for a personal academic website, written in Jekyll for hosting with GitHub Pages.

## Features
- Minimal, clean design
	- CV-specific print-style
- Responsive layout with collapsible sidebar-menu
	- Hierarchical menu with deep linking
- Site-wide search-system
- Simple social sharing buttons
- Optional MathJax for displaying mathematical notations

## Setup

1. Register an account with GitHub
2. Fork `https://github.com/OleVik/personal-academic-website`
3. Rename repository to `username.github.io`, where `username` is your GitHub-username
4. Set `baseurl` to `username.github.io` in `_config.yml`
5. Edit Markdown-files (`.md`)

Edit the pages using any Markdown-editor (see below) or text-editor, then upload them.

### Custom Domain
If you want to use a custom domain, ie. not `username.github.io` but something like `mywebsite.com`, read [this guide](https://help.github.com/articles/using-a-custom-domain-with-github-pages/).

## Workflow
Pages are written Markdown and use FrontMatter. For Markdown, see [this cheatsheet](http://ricostacruz.com/cheatsheets/markdown.html) or [this quick guide](https://milanaryal.com/2015/writing-on-github-pages-and-jekyll-using-markdown/). Alternatively, view the default "Hello"-document on [StackEdit](https://stackedit.io/editor).

### FrontMatter
Defines the settings for each page, using this format (minimal requirements for each page):

- Title: Double quote-encapsulated string naming the page
- Summary: Double quote-encapsulated string describing the page
- Date: Date for when the page was written (YYYY-MM-DD)
- Layout: String governing layout to use, either "default" or "cv" (no quotes)

For example:

```
---
title: "About"
summary: "About this page."
date: 2016-04-02
layout: default
---
```

More options are [available here](https://jekyllrb.com/docs/frontmatter/).

Notes:

1. Indentation, if used, must be two spaces (not tabs).
2. Colons (`:`) can only be used in strings if enclosed in quotes.
3. Dashes can be used in strings, but should otherwise also be enclosed in quotes (see [this](https://docs.saltstack.com/en/latest/topics/yaml/)).

### FrontMatter for the CV
- Layout must be "cv" (`layout: cv`)
- See `cv.md` for other variables
- List-elements are the following: `experience, education, positions`
	- These consist of nested lists in YAML, for example:

```
education:
  - years: 2013-2015
    name: Master’s Degree
    location: University
    description: Includes qualitative and quantitative methods.
  - years: 2010-2013
    name: Bachelor’s Degree
    location: University
    description: Includes statistics and maths.
```

To add other list-elements, edit `_layouts/cv.html`, and duplicate the blocks of code including a for-loop, changing the variable (`page.variable`) in:

```
{% raw %}{% for item in page.experience %}
	Various HTML code...
{% endfor %}{% endraw %}
```

To whatever you name the list.

### Editors
In order of most recommended for this workflow:

- [Prose](http://prose.io/#about): "Simple content authoring environment for CMS-free websites", very easy to use for editing GitHub Pages.
	- Direct editing, only requires GitHub authorization.
- [StackEdit](https://stackedit.io/): Elegant interface with live preview and extensive features.
	- Can publish to GitHub, saves documents in local browser storage or the cloud.
- [DraftIn](http://docs.withdraft.com/): Also elegant and easy-to-use interface with extensive features.
	- Requires signup (e-mail).
	- Handy [Chrome extension](https://chrome.google.com/webstore/detail/draft/amlbbbgcijmiooecobhkjblcdkjldmdk) for editing text on any website.

Or just edit pages directly on GitHub.

#### Including files on pages
PDF-files can be linked to from the GitHub Repository, but it is far easier to upload it to [Google Drive](https://drive.google.com/drive/) and embed it (or any other cloud storage that generates an `<iframe>`-embed tag).

Procedure (from [here](http://www.steegle.com/websites/google-sites-howtos/embed-drive-pdf)):

1. Find the PDF file in Google Drive.
2. Preview the PDF file in Google Drive.
3. Pop-out the Google Drive preview.
4. Use the More actions menu and choose Embed item.
5. Copy code provided.
6. Paste it on a separate line in the Markdown-file, like this:

```
Paragraph...

<iframe style="margin: 10px 0 40px 0;" class="pdf-iframe" src="https://drive.google.com/file/d/0B-xXQEsWEjrUUmpBdkhIVS10YjA/preview" width="100%" height="768"></iframe>

Other Markdown and text.
```

#### Site settings
The links in the menu, and their order, are edited through `_config.yml`. The format is also nested YAML lists, like the FrontMatter described above. **'baseurl' must be set to your repository (eg. `baseurl: username.github.io`), or the build will fail.** The `name` and `description` variable should also be set, as well as `mathjax: true` if you need to render MathJax formulas on pages.

The `markdown, encoding, locale` variables **should not be changed**.

To find the right page-link (`#somethingonthepage`) you open the page, hover a heading so that the icon-link displays, right-click it and choose "Copy link". Everything after the `#` is the link for this specific title on the page.

Note that these links must be encapsulated in quotes in the lists in `_config.yml`, or they will be interpreted as code-comments.

### Development
Written in [Jekyll](http://jekyllrb.com/), structured with [Bootstrap v4](http://getbootstrap.com/), styled with [plain CSS](http://www.css3-tutorial.net/introduction/what-is-css/). The Jekyll-output (in the `_site`-folder when generated) can be hosted anywhere (static files). For further development, see [Jekyll Tips](http://jekyll.tips/) and [GitHub Pages Setup Guide](http://jmcglone.com/guides/github-pages/).
