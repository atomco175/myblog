---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<div class="home">
  <!-- Posts Section -->
  <section class="posts-section">
    <div class="main-posts">
      {% if site.posts.size > 0 %}
        <!-- Featured Post -->
        {% assign featured_post = site.posts.first %}
        <article class="featured-post">
          {% if featured_post.image %}
            <img src="{{ featured_post.image }}" alt="{{ featured_post.title }}" class="post-image">
          {% endif %}
          
          <div class="post-meta">
            <span class="post-date">{{ featured_post.date | date: "%B %d, %Y" }}</span>
          </div>
          
          <h2 class="post-title">
            <a href="{{ featured_post.url | relative_url }}">{{ featured_post.title }}</a>
          </h2>
          
          <div class="post-excerpt">
            {{ featured_post.excerpt | strip_html | truncate: 200 }}
          </div>
          
          <a href="{{ featured_post.url | relative_url }}" class="read-more">
            Read more →
          </a>
        </article>

        <!-- Other Posts -->
        <div class="other-posts">
          {% for post in site.posts offset: 1 %}
            <article class="post-item">
              <div class="post-content">
                <div class="post-meta">
                  <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
                </div>
                
                <h3 class="post-title">
                  <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </h3>
                
                <div class="post-excerpt">
                  {{ post.excerpt | strip_html | truncate: 120 }}
                </div>
              </div>
              
              {% if post.image %}
                <div class="post-image-small">
                  <img src="{{ post.image }}" alt="{{ post.title }}">
                </div>
              {% endif %}
            </article>
          {% endfor %}
        </div>
      {% else %}
        <div class="no-posts">
          <p>No posts yet. Stay tuned!</p>
        </div>
      {% endif %}
    </div>
  </section>
</div>

<style>
/* 調整首頁間距 */
.home {
  padding: 2rem 0;
}

/* 調整佈局為單欄式 */
.posts-section {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 2rem;
}

.main-posts {
  width: 100%;
}

.featured-post {
  margin-bottom: 4rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid #e6e6e6;
}

.featured-post .post-image {
  width: 100%;
  height: 400px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 2rem;
}

.featured-post .post-meta {
  color: #757575;
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.featured-post .post-title {
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 1rem;
}

.featured-post .post-title a {
  color: #292929;
  text-decoration: none;
  font-family: "Merriweather", Georgia, serif;
}

.featured-post .post-title a:hover {
  color: #1a8917;
}

.featured-post .post-excerpt {
  font-size: 1.1rem;
  color: #757575;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.featured-post .read-more {
  color: #84B067;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.9rem;
}

.featured-post .read-more:hover {
  text-decoration: underline;
}

.other-posts .post-item {
  display: flex;
  gap: 2rem;
  margin-bottom: 2.5rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #e6e6e6;
}

.other-posts .post-item:last-child {
  border-bottom: none;
}

.other-posts .post-content {
  flex: 2;
}

.other-posts .post-image-small {
  flex: 1;
  max-width: 200px;
}

.other-posts .post-image-small img {
  width: 100%;
  height: 120px;
  object-fit: cover;
  border-radius: 4px;
}

.other-posts .post-meta {
  color: #757575;
  font-size: 0.85rem;
  margin-bottom: 0.5rem;
}

.other-posts .post-title {
  font-size: 1.25rem;
  font-weight: 700;
  line-height: 1.3;
  margin-bottom: 0.5rem;
}

.other-posts .post-title a {
  color: #292929;
  text-decoration: none;
}

.other-posts .post-title a:hover {
  color: #1a8917;
}

.other-posts .post-excerpt {
  color: #757575;
  font-size: 0.95rem;
  line-height: 1.5;
}

.no-posts {
  text-align: center;
  padding: 4rem 2rem;
  color: #757575;
  font-style: italic;
}

/* 響應式設計 */
@media (max-width: 768px) {
  .posts-section {
    padding: 0 1rem;
  }
  
  .featured-post .post-title {
    font-size: 2rem;
  }
  
  .featured-post .post-image {
    height: 250px;
  }
  
  .other-posts .post-item {
    flex-direction: column;
    gap: 1rem;
  }
  
  .other-posts .post-image-small {
    max-width: 100%;
  }
  
  .other-posts .post-image-small img {
    height: 200px;
  }
}
</style>
