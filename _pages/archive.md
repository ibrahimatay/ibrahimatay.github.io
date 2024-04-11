---
layout: page
permalink: /archive/
title: Posts Archive
---


<div id="archives">
  <section id="archive">
     <h3>Most Recent Posts</h3>
      {%for post in site.posts %}
      {% unless post.next %}
      <ul class="this">
          {% else %}
          {% capture month %}{{ post.date | date: '%B %Y' }}{% endcapture %}
          {% capture nmonth %}{{ post.next.date | date: '%B %Y' }}{% endcapture %}
          {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
          {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
          {% if year != nyear %}
      </ul>
      <h2 style="text-align:left;">{{ post.date | date: '%Y' }}</h2>
      <ul class="past">
          {% endif %}
          {% if month != nmonth %}
          <h3 style="text-align:left;">{{ post.date | date: '%B %Y' }}</h3>
          {% endif %}
          {% endunless %}
          <p><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</p>
          {% endfor %}
      </ul>
    <h3>Oldest Posts</h3>
  </section>
</div>


<div>
{% for tag in site.tags %}
<h3>{{- tag[0] -}}</h3>
<ul>
  {%- for post in tag[1] %}
  <li><a href="{{ post.url }}">{{ post.date | date: "%b %Y" }} - {{ post.title }}</a></li>
  {%- endfor %}
</ul>
{%- endfor %}
<h3>Personal</h3>
<ul>
  {%- for post in site.personal %}
  <li><a href="{{ post.url }}">{{ post.date | date: "%b %Y" }} - {{ post.title }}</a></li>
  {%- endfor %}
</ul>
</div>