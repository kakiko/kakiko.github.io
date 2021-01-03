---
layout: post
title: How to implement CMS Netlify on Jekyll with Bitbucket
permalink: blog/cms-netlify-jekyll-bitbucket
---
This is how we intergrate Netlify CMS into an existing jekyll site. We assume we are making CMS for blog posts.

<p>1. Read the original guide first. <a href="https://www.netlifycms.org/docs/intro/">CMS Netlify</a> provide a lot of useful informations for you to get started, but it focused on GitHub users. This guide however show you from a bitbucket user perspective.</p>

<p>2. Make sure you already have your Netlify hooked to your bitbucket account. As in you can remotely push your local repository to bitbucket, and Netlify will automatically have your site build and deploy. If you have complete this step, move on!</p>

<p>3. Create a folder called "admin" in your jekyll directory, then create two files inside the "admin" folder, namely "index.html" and "config.yml".</p>

<p>4. Get the index.html code from <a href="https://www.netlifycms.org/docs/add-to-your-site/">https://www.netlifycms.org/docs/add-to-your-site/.</a></p>

<p>5. For the config.yml, paste the code below.</p>

    backend:
      name: git-gateway
      branch: master # Branch to update (optional; defaults to master)
    
    # This line should *not* be indented
    media_folder: "images/uploads" # Media files will be stored in the repo under images/uploads
    
    collections:
      - name: "post" # Used in routes, e.g., /admin/collections/blog
        label: "post" # Used in the UI
        folder: "_posts" # The path to the folder where the documents are stored
        create: true # Allow users to create new documents in this collection
        slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
        fields: # The fields for each document, usually in front matter
          - {label: "Layout", name: "layout", widget: "hidden", default: "post"}
          - {label: "Title", name: "title", widget: "string"}
          - {label: "Date", name: "date", widget: "date"}
          - {label: "Permalink", name: "permalink", widget: "string"}
          - {label: "Body", name: "body", widget: "markdown"}


<br/>
A few things to note here, title label is extremely important, without it the CMS won't work. Permalink label is there because when you change the title, the permalink won't automatically update itself, hence the need to include it. Date label is there for convenient editing.



<p>6. Now enable identity in your Netlify dashboard. Press invite users, and invite yourself. Go to your email inbox and click on the confirmation link. Walah! You're now a user.</p>

<p>7. Next go to settings, Access control, OAuth, and install provider. Choose bitbucket, it will ask you for secret and client id.</p>

<p>8. To get the two values, go to bitbucket, click on your profile and choose bitbucket settings. Under access management, click OAuth, add a consumer.</p>

For bare minimum, fill up the name, callback url (obtain from https://www.netlify.com/docs/authentication-providers/#using-an-authentication-provider), tick "this is a private consumer", tick read and write in repository. Shazam! you got yourself the two values. Fill it up at the Netlify dashboard panel.

<p>9. Go to your website (example.com/admin), login with your bitbucket account, grant it permission. And you should have access to the CMS!</p>

<p>10. Congratulation, you've build yourself a little wordpress. Without any database!</p>

I ended up not using the CMS, because when I edit the title, the file name remained the same. A small annoyance some would say, but it turns out I can't live with that. The OCD within me got the best of me, sadly.