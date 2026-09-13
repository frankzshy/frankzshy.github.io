---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign published_papers = site.publications | where_exp: "post", "post.in_progress != true" %}
{% assign in_progress_papers = site.publications | where_exp: "post", "post.in_progress == true" %}

<h2 id="published">Published</h2>

{% for post in published_papers reversed %}
  {% include archive-single.html %}
{% endfor %}

<h2 id="working-papers">Working Papers</h2>

{% for post in in_progress_papers reversed %}
  {% if post.hide_link != true and post.paperurl or post.link %}
    {% include archive-single.html %}
  {% else %}
    {% assign title = post.title %}
    <div class="list__item">
      <article class="archive__item" itemscope itemtype="http://schema.org/CreativeWork">
        <h2 class="archive__item-title" itemprop="headline">{{ title }}</h2>
        <p>Draft available upon request.</p>
      </article>
    </div>
  {% endif %}
{% endfor %}
