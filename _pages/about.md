---
layout: single
permalink: /
title: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
Hi, I'm Trang !

I’m a Data Scientist with experience in credit risk modeling and predictive analytics.  
I’ve worked on building and deploying scorecard models, automating data workflows, and monitoring model performance in production.

Recently, I’ve been expanding into AI, with a focus on applying machine learning to real-world problems.

This site showcases some of the projects I’ve worked on and what I’m currently learning.


{% include base_path %}

## Latest Projects

{% assign sorted_projects = site.projects | sort: 'date' | reverse %}

{% for project in sorted_projects limit:3 %}
<div style="display: flex; margin-bottom: 25px;">

  <!-- Thumbnail -->
  <div style="flex: 0 0 120px; margin-right: 15px;">
    <img src="{{ base_path }}{{ project.image }}" style="width: 100%; border-radius: 6px;">
  </div>

  <!-- Content -->
  <div>
    <h3 style="margin-bottom: 5px;">
      <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    </h3>

    {% if project.authors %}
      <p style="margin: 2px 0; font-size: 0.95em;">
        {{ project.authors }}
      </p>
    {% endif %}

    {% if project.venue %}
      <p style="margin: 2px 0; font-size: 0.95em;">
        {{ project.venue }}
      </p>
    {% endif %}

    <!-- Links -->
    <p style="margin-top: 5px; font-size: 0.9em;">
      {% if project.project_page %}
        <a href="{{ project.project_page }}">Project Page</a>
      {% endif %}
      {% if project.code %}
        | <a href="{{ project.code }}">Code</a>
      {% endif %}
      {% if project.paper %}
        | <a href="{{ project.paper }}">Paper</a>
      {% endif %}
    </p>
  </div>

</div>
{% endfor %}


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
