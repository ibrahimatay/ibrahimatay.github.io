---
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: page
title: 
---
As an experienced architect and leader, he has a proven track record of helping companies implement next-generation technology architectures that are both robust and scalable. By building solutions that are designed for maintainability, reliability, and cost-effectiveness, he enables organizations to achieve their business goals and stay competitive in today's rapidly changing technological landscape.

He is a specialist in domain-driven design, cloud-native technologies, integration, and microservices architecture.

He holds a Master's degree in Engineering Management from Sakarya University. In addition, he has obtained the following professional certifications. 

- The Open Group Architecture Framework (TOGAF) Certified
- ITIL Foundation
- PMI Agile Certified Practitioner (PMI-ACP)
- Certified Scrum Master (CSM)
- Kanban Management Professional (KMP)

<div>
{%- if site.posts.size > 0 -%}
    <h2 class="post-list-heading">{{ page.list_title | default: "Latest Posts" }}</h2>
    <ul class="post-list">
      {%- assign post_limit = site.home_post_limit | default: 5 -%}
      {%- for post in site.posts limit:post_limit -%}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <span>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </span>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>

    <p class="rss-subscribe">Subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
  {%- endif -%}
  </div>