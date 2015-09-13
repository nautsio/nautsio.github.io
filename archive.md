---
layout: clean
homeurl: /
permalink: /archive.html
---
<div>
    <section id="blog" >
        <div class="container">
            <div class="row">
                <div class="col-lg-12 text-center">
                    <h2 class="section-heading">Blogposts - Archive</h2>
                    <h3 class="section-subheading text-muted">We like to share our knowledge.</h3>
                </div>
            </div>
            <div class="row">
            {% for post in site.posts %}
                <div class="col-md-12 col-sm-12">
                    <h4>{{ post.title }}</h4>
                    <p class="text-muted">{{ post.excerpt }}</p>
										<a href="{{ post.externalurl }}">Read more on {{ post.author }}'s website</a>
										<p/>
                </div>
            {% endfor %}
            </div>
        </div>
    </section>
</div>