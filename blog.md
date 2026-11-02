---
layout: default
title: Blog
permalink: /blog/
---

# Articles & Writings

Here are my latest posts published on [Medium](https://dinanoviana.medium.com):

<div id="medium-posts-container">
  <p style="color: #6b7280; font-style: italic;">Loading articles from Medium...</p>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const rssFeedUrl = "https://medium.com/feed/@dinanoviana";
    const apiUrl = `https://api.rss2json.com/v1/api.json?rss_url=${encodeURIComponent(rssFeedUrl)}`;

    fetch(apiUrl)
      .then(response => response.json())
      .then(data => {
        const container = document.getElementById("medium-posts-container");
        if (data.status === "ok" && data.items && data.items.length > 0) {
          let html = '<ul style="list-style: none; padding: 0; margin: 20px 0;">';
          
          data.items.forEach(item => {
            const pubDate = new Date(item.pubDate).toLocaleDateString("en-US", {
              year: 'numeric',
              month: 'short',
              day: 'numeric'
            });

            html += `
              <li style="margin-bottom: 24px; padding-bottom: 16px; border-bottom: 1px solid #f3f4f6;">
                <h3 style="margin: 0 0 6px 0; font-size: 18px; font-weight: 600;">
                  <a href="${item.link}" target="_blank" style="text-decoration: none; color: #2563eb;">${item.title}</a>
                </h3>
                <span style="font-size: 12px; color: #9ca3af;">Published on ${pubDate}</span>
              </li>
            `;
          });

          html += '</ul>';
          container.innerHTML = html;
        } else {
          container.innerHTML = '<p style="color: #6b7280;">No articles found yet.</p>';
        }
      })
      .catch(error => {
        console.error("Error fetching Medium feed:", error);
        document.getElementById("medium-posts-container").innerHTML = '<p style="color: #ef4444;">Unable to load Medium posts right now.</p>';
      });
  });
</script>