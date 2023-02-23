---
layout: page
title: posts | goobbess
---

<section>
  {% if site.posts[0] %}

    {% capture currentmonth %}{{ 'now' | date: "%M" }}{% endcapture %}
    {% capture firstpostmonth %}{{ site.posts[0].date | date: '%M' }}{% endcapture %}
    {% if currentmonth == firstpostmonth %}
        <h3>This month's posts</h3>
    {% else %}
        <h3>{{ firstpostmonth }}</h3>
    {% endif %}

    {%for post in site.posts %}
      {% unless post.next %}
        <ul>
      {% else %}
        {% capture month %}{{ post.date | date: '%M' }}{% endcapture %}
        {% capture nmonth %}{{ post.next.date | date: '%M' }}{% endcapture %}
        {% if month != nmonth %}
          </ul>
          <h3>{{ post.date | date: '%M' }}</h3>
          <ul>
        {% endif %}
      {% endunless %}
        <li><time>{{ post.date | date:"%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ post.title }}
          </a>
        </li>
    {% endfor %}
    </ul>

  {% endif %}
</section>
