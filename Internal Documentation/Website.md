---
layout: page
title: Editing the Website
permalink: /internal/website
nav_order: 1
parent: Internal Documentation
---

The pleajustice.org website is a [GitHub Pages](https://pages.github.com/) site in the [plea-justice.github.io](https://github.com/Plea-Justice/plea-justice.github.io/) repository. It can be edited directly through the GitHub interface. It is possible to generate the site locally with [Jekyll](https://jekyllrb.com/) for more advanced editing.

To edit pages directly on GitHub. Open any of the `.md` ([Markdown](https://guides.github.com/features/mastering-markdown/)) files. The site content is written in Markdown but also supports intermixed HTML tags. The design and organization of the site is generated dynamically whenever changes to the `.md` documents are saved.

![Editng Pages on GitHub](/img/website/github-edit.gif)

The top of each file contains [a header in YAML format](https://jekyllrb.com/docs/front-matter/). This metadata defines the title of the page, how the page may be linked to from other pages, and where the page will appear in the sidebar. The following is the header for this page in `Website.md`.

```yaml
---
layout: page
title: Editing the Website
permalink: /internal/website
nav_order: 1
parent: Internal Documentation
---
```