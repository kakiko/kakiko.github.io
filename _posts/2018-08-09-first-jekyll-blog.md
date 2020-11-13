---
layout: post
---
Today is an extremely momentous night, I'm typing this at 2.52 am right now. I finally get publish my first blog and content static generator site for the first time.

I learn about this years ago, but lack the time or commitment to learn this amazing technology. But now I have, it is freaking amazing!

It may be slightly inconvenient to update or publish new materials, or even doing slight editing adjustments, but if you treat this as updating a piece of software, it'll feel much better.

A few things I would like to take note in making this website successfully running.

This cheatsheet is amazing, so does a few others who tried their best making git as ELI5 as possible. 

#### git
http://rogerdudler.github.io/git-guide/ the simplest guide to git  
https://www.git-tower.com/blog/git-cheat-sheet  
a few essential commands in running this git-bitbucket-netlify combination.  
https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/#netlifystart

git init  
git clone  
git status  
git add .  
git commit (if you're in some weird interface of the command line, press esc, then :wq to exit, after entering your one line commit message of course.)  
https://stackoverflow.com/questions/13507430/git-commit-in-terminal-opens-vim-but-cant-get-back-to-terminal  
git log  
git remote add *name *url (*name are usually origin by convention? *url usually end with /folder.git)  
git pull *origin *master  
git push *origin *master  

#### markdown

use **two spaces** to end a line, if you want to do single line break. for paragraph break, css formating is done.

Oh my, I still have a lot to learn about this.

#### jekyll
https://learn.cloudcannon.com/jekyll-cheat-sheet/  
I just put it as a bookmark first, will refer to it when customizing this site.
every time something site wide is done, run `bundle exec jekyll serve`


oh, before publishing the site, don't forget to get it w3 validated.

special thanks to these people who inspired me:  
https://www.santi.cf/blog/hosting-a-website-for-free-with-a-custom-domain-using-bitbucket.html  
https://www.savjee.be  
