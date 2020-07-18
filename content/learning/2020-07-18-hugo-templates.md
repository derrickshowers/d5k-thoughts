---
title: "Mike Dane: Templates (and more)"
date: 2020-07-18T14:00:00-00:00
slug: hugo-templates
link: https://www.mikedane.com/static-site-generators/hugo/introduction-to-templates/
subjects: ["hugo", "web"]
---

Linked to "Introduction to Templates" but watched a whole bunch of videos from Mike's site to better understand Hugo's terminology around templates. Now everything is finally starting to make sense!

* Two types of templates: single and list
* There's technically a homepage template as well (index.html)
* A base template can be used with blocks (baseof.html)
* `.Data` is used to retreive data from `/data`. Basically a local database (json, toml, yaml).
* `.Pages` is all the pages in the current section (from [functions video](https://www.mikedane.com/static-site-generators/hugo/functions/)).
* The term "front matter" just means the meta data at the top of each markdown file. These are just variables (from [variables video](https://www.mikedane.com/static-site-generators/hugo/variables/)).
* Types vs sections
    * Sections are what directory the content is in `/content/post/` is therefore in the post section. Layout directory can override list or single templates.
    * Types are the section by default, but can be a different type via front matter (e.g. `/content/post/` is of type “post” by default, but can be changed, `type: short-post`).

_also watched [homepage templates](https://www.mikedane.com/static-site-generators/hugo/home-page-templates/), [section templates](https://www.mikedane.com/static-site-generators/hugo/section-templates/), [block templates](https://www.mikedane.com/static-site-generators/hugo/block-templates/)_