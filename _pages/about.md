---
layout: single
permalink: /
title: "Hi, I’m Trang."
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I’m a Data Scientist with experience in credit risk modeling and predictive analytics.  
I’ve worked on building and deploying scorecard models, automating data workflows, and monitoring model performance in production.

Recently, I’ve been expanding into AI, with a focus on applying machine learning to real-world problems.

This site showcases some of the projects I’ve worked on and what I’m currently learning.

---

## Featured Projects

{% include base_path %}

{% assign sorted_projects = site.projects | sort: 'date' | reverse %}
{% for post in sorted_projects limit:3 %}
  {% include archive-single.html %}
{% endfor %}

<p>
  <a href="{{ base_path }}/projects/"><strong>View all projects →</strong></a>
</p>

---

## Latest Posts

{% assign latest_posts = site.posts | sort: 'date' | reverse %}

{% for post in latest_posts limit:3 %}
  <article style="margin-bottom: 1.2em;">
    <h3 style="margin-bottom: 0.2em;">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h3>
    <p style="font-size: 0.9em; color: #666; margin-top: 0;">
      {{ post.date | date: "%B %d, %Y" }}
    </p>
    {% if post.excerpt %}
      <p>{{ post.excerpt | strip_html | truncate: 160 }}</p>
    {% endif %}
  </article>
{% endfor %}

<p>
  <a href="{{ base_path }}/year-archive/"><strong>View all posts →</strong></a>
</p>
