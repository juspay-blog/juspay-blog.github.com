---
layout: page
title:
tagline: 
---
{% include JB/setup %}

{% for post in site.posts limit:5 %}

<div class="row article">
    <div class="span8">
        <div class="header">
            <h3><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h3>
            <h4><small>{{ post.date | date: '%d %b %Y' }}</small></h4>
            <hr>
        </div>
        <div class="main_section">
            {{ post.content }}
        </div>
    </div>
</div>

{% endfor %}
