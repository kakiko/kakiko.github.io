---
layout: home
title: Blog
permalink: blog
---

{%- if site.posts.size > 0 -%}
 
  {%- for post in site.posts -%}
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
          [{{ post.title | escape }}]({{ post.url | relative_url }})
        <small>{{ post.date | date: date_format }}</small>  
        <br>        
      
      {%- if site.show_excerpts -%}
        {{ post.excerpt }}
      {%- endif -%}
  {%- endfor -%}

{%- endif -%}