---
title:
layout: page
permalink: /projects/
---

<div class="posts">
  {% for post in site.posts %}

    <article class="post">

      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>

      <div class="entry">
	  	<figure style="margin: 20px auto; text-align: center;" width='70%'>
	      <img src="{{ post.image.path }}" alt='missing' width='{{post.image.width}}' style='margin:20px auto; display:inline-block' text-align='center'/>
		</figure>
		<p>{{ post.excerpt }}</p>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
      </div>
	<p>-------------------------------------------------------------------------------------</p>
    </article>

  {% endfor %}
</div>
