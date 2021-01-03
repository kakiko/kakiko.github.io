---
layout: post
title: How to enable automatic directory indexing/listing on GitHub Pages
---
As you may know GitHub uses Jekyll for its free GitHub pages hosting.

If you have a bunch of html files in a repo, if would be useful if the index page display a list of html files contained inside the repository. So when user visit your repository home page, it will have a quick overview of the html files available.

However it is troublesome to edit home page (index.html) manually each time you make changes to one of the html files.

## Guide
So here is a guide to automate it. It uses existing Jekyll only, no other dependencies.

1. Enable GitHub page and choose a theme. Doing so will generate a _config.yml on your directory.

2. Git pull it to sync the files. Now add the following code to index.md or index.html.

```xml
{% raw %}
   {% assign doclist = site.pages | sort: 'url'  %}
    <ul>
       {% for doc in doclist %}
            {% if doc.name contains '.md' or doc.name contains '.html' %}
                <li><a href="{{ site.baseurl }}{{ doc.url }}">{{ doc.url }}</a></li>
            {% endif %}
        {% endfor %}
    </ul>
{% endraw %}
```
3. Commit and push it to GitHub, and you should see an updated directory listing on index page every time you commit.

## Note
Two things to take note:

### First
It can't detect .html file if it doesn't have the [front matter](https://jekyllrb.com/docs/front-matter/) inside. There are two ways to remedy it:
- For each .html file, put `------` before the <html> tag.
  - PRO: It retained html extension on the repository
  - CON: Doesn't look good when loading the html locally, the `------` will still appear in the repo.
- Change all .html file to .md extension. So it become a markdown file.
  - PRO: No need to put `------`
  - CON: GitHub pages will automatically use `_layout/default.html` to wrap your file code, so your `<head>` information will go missing.
  - CON2: You have to use md extension.


So next time when u git push the repo, GitHub's Jekyll builder will automatically convert all md file (except README.md) to html, and populate the list on the repo automatically. Yay!

### Second
You can't track other file format aside from markdown, HTML and CSS, I’m not sure about it though.

<br/>
<br/>

> Useful reference: https://jekyllrb.com/docs/variables/

