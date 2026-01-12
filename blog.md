---
layout: default
title: Blog
permalink: /blog/
---

<section class="blog-index">
  <h1 class="blog-title">Blog</h1>
  <p class="blog-intro">
    Yap time
  </p>

  <div class="post-list">
    {% for post in site.posts %}

      {% assign words = post.content | number_of_words %}
      {% assign reading_time = words | divided_by: 200 | at_least: 1 %}

      <article class="post-card">
        <a class="post-card-inner" href="{{ post.url | relative_url }}">

          <header class="post-card-header">
            <h2 class="post-card-title">{{ post.title }}</h2>
            {% if post.subtitle %}
              <p class="post-card-subtitle">{{ post.subtitle }}</p>
            {% endif %}
          </header>

          <div class="post-card-meta">

            <span class="meta-item">
              📅 {{ post.date | date: "%b %-d, %Y" }}
            </span>

            <span class="meta-item">
              ⏱ {{ reading_time }} min read
            </span>

            {% if post.last_modified_at %}
            <span class="meta-item">
              ✏️ Updated {{ post.last_modified_at | date: "%b %-d, %Y" }}
            </span>
            {% endif %}

            {% if post.categories %}
            <span class="meta-item">
              📂 {{ post.categories | first }}
            </span>
            {% endif %}

          </div>

          {% if post.tags %}
          <div class="post-card-tags">
            {% for tag in post.tags %}
              <span class="tag-pill">{{ tag }}</span>
            {% endfor %}
          </div>
          {% endif %}

        </a>
      </article>

    {% endfor %}
  </div>
</section>
