---
title: Rails Girls Summer of Code Blog
class: page blog
layout: default
---

<section class="main container">
  <div class="wrapper-blog">
    {% for post in site.posts %}
      <article class="content-blog">
        <h1><a href="{{post.url}}">{{post.title}}</a></h1>

        <p class='meta'>
          {% if post.twitter %}
            <a href='http://twitter.com/{{ post.twitter }}'>{{ post.author }}</a>,
          {% else %}
            {{ post.author }},
          {% endif %}
          <time datetime="{{ post.created_at | date: "%Y-%m-%dT%H:%M:%S%z"  }}">{{ post.created_at | date: "%B %-d, %Y" }}</time>
        </p>
        {{ post.content }}
      </article>
    {% endfor %}
      
  </div>
</section>


<section class="main container">
<div class="wrapper-blog">
<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="date">{{ post.date }}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
{% endfor %}

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="/page{{ paginator.previous_page }}" class="previous">Previous</a>
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">Page: {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="/page{{ paginator.next_page }}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>

</div>
</section>
