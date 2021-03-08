## Welcome to Zhiqi Bu's blog

I am currently a PhD student at University of Pennsylvania working on highly multi-disciplinary research. I enjoy researching on machine learning, in particular statistical machine learning, optimization and deep neural networks. My ambition is to develop algorithms and models that are mathematically solid, empirically strong, intuitively simple and highly generalizable.

Research should be fun, but sometimes one lacks the stepping stones to get into the flow. Hopefully my posts help you gain some insights.

## More about me
[My personal website](https://sites.google.com/view/zhiqi-bu)

[My Google Scholar](https://scholar.google.com/citations?user=MEvTLxIAAAAJ&hl=en)

### Some topics I have worked on:
- Neural network theory
- Differential privacy
- L1 regularization in linear model
- Approximate message passing
- Missing value imputation
- Semi-parametric models
- Adversarial robustness


<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
	  	<figure style="margin: 20px auto; text-align: center;" width='100%'>
	      <img src="{{ post.image.path }}" alt='missing' width='{{post.image.width}}' style='margin:20px auto; display:inline-block' text-align='center'/>
		</figure>
		<p>{{ post.excerpt }}</p>
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>
