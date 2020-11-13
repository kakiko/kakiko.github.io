---
layout: post
title: Quick Editing Feature for New Blogger Theme
permalink: blog/new-blogger-theme-quick-editing
---
The infamous pencil icon is missing from the new Emporio, Contempo, Soho and Notable Themes released by Blogger.

Here is a quickfix.

Create a bookmark link in the bookmark toolbar, and enter the following in the URL field.

    javascript:(function()%7Bvar%20str%20%3D%20document.getElementsByTagName('html')%5B0%5D.innerHTML%3Bvar%20w%3Bif%20(str.includes(%22blogId%22))%20%7Bvar%20v%20%3D%20str.split(%22blogId'%3A%20'%22)%5B1%5D%3Bw%20%3D%20v.substring(0%2C%20v.indexOf(%22'%2C%20'%22))%3B%7Dif%20(str.includes(%22postId%22))%20%7Bvar%20r%20%3D%20str.split(%22postId'%3A%20'%22)%5B1%5D%3Bvar%20z%20%3D%20r.substring(0%2C%20r.indexOf(%22'%2C%20'%22))%3Bvar%20url%20%3D%20%22https%3A%2F%2Fwww.blogger.com%2Fblogger.g%3FblogID%3D%22%20%2B%20w%20%2B%20%22%23editor%2Ftarget%3Dpost%3BpostID%3D%22%20%2B%20z%3Bwindow.open(url%2C'_blank')%3B%7Delse%20if%20(str.includes(%22pageId%22))%20%7Bvar%20k%20%3D%20str.split(%22pageId'%3A%20'%22)%5B1%5D%3Bvar%20b%20%3D%20k.substring(0%2C%20k.indexOf(%22'%2C%20'%22))%3Burla%20%3D%20%22https%3A%2F%2Fwww.blogger.com%2Fblogger.g%3FblogID%3D%22%20%2B%20w%20%2B%20%22%23editor%2Ftarget%3Dpage%3BpageID%3D%22%20%2B%20b%3Bwindow.open(urla%2C'_blank')%3B%7D%7D)()

To use it, go to the page/post that you want to edit, then press the bookmarklet, the online text editor should pop up in another tab.

If you want to compiled the javascript code yourself into a booklet, below is the source code:

```
  <script>
    function onclicka() {
        var str = document.getElementsByTagName('html')[0].innerHTML;
        var w;
        var urla = window.location.href

        if (urla.includes("blog.cl.mt")) {
            var v = str.split("targetBlogID=")[1];
            w = v.substring(0, v.indexOf("&"));
        }
        if (urla.includes("blog.cl.mt/p/")) {
            var k = str.split("static_page', 'pageId': '")[1];
            var b = k.substring(0, k.indexOf("', '"));
            urla = "https://www.blogger.com/blogger.g?blogID=" + w + "#editor/target=page;pageID=" + b;
            window.open(urla, '_blank');
        }else if (urla.includes("blog.cl.mt/2")) {
            var r = str.split("postId': '")[1];
            var z = r.substring(0, r.indexOf("', '"));
            var url = "https://www.blogger.com/blogger.g?blogID=" + w + "#editor/target=post;postID=" + z;
            window.open(url, '_blank');
        }
    }
</script>
<a class="" onclick="onclicka()">Click me</a>
```


