---
layout: page
permalink: /about/index.html
title: About Me
tags: [Roberson, Christian, theroberson]
chart: true
---
<figure>
  <img src="{{ site.url }}/images/me.jpg" alt="Christian Roberson" height="434" width="297">
  <figcaption>Christian Roberson</figcaption>
</figure>

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}


My name is **Christian Roberson**, and this is my blog. It currently has {{ site.posts | size }} posts in {{ site.categories | size }} categories. {% if featuredcount != 0 %}It has <a href="{{ site.url }}/featured">{{ featuredcount }} featured post{% if featuredcount > 1 %}s{% endif %}</a> which you should definitely check out.{% endif %} The most recent post is {% for post in site.posts limit:1 %}{% if post.description %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">"{{ post.title }}"</a>{% endif %}{% endfor %} which was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%B %d, %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%B %d, %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The last commit was on {{ site.time | date: "%A %B %d, %Y" }} at {{ site.time | date: "%I:%M %p" }}.

Since 2007 I have been a faculty member in the [Computer Science and Technology Department](https://www.plymouth.edu/compsci){:target="_blank"} at [Plymouth State University](https://www.plymouth.edu){:target="_blank"}. I have taught a wide variety of courses including introductory programming, data structures, algorithms, software engineering, computer security, web programming, and mobile application development. I have served as chair of the department since 2012.