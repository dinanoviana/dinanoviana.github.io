---
layout: default
title: Projects
permalink: /projects/
---

## SQA

<ul style="list-style: none; padding: 0; margin: 20px 0 40px 0;">
  <li style="margin-bottom: 28px; padding-bottom: 20px; border-bottom: 1px solid #f3f4f6;">
    <h3 style="margin: 0 0 4px 0; font-size: 18px; font-weight: 600; color: #7089c1;">
      Core Banking Implementation
    </h3>
    <p style="margin: 0 0 6px 0; font-size: 13px; font-weight: 500; color: #4b5563;">PT Bank KB Indonesia Tbk &bull; Mar 2024 – Apr 2025</p>
    <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 600; color: #4e77cf;">Quality Assurance Financial Accounting Stream Lead</p>
    <ul style="margin: 0 0 8px 0; padding-left: 20px; font-size: 14px; color: #4b5563;">
      <li style="margin-bottom: 4px;">Execute System Integration Testing (SIT) and User Acceptance Testing (UAT).</li>
      <li style="margin-bottom: 4px;">Collaborate with external IT vendor and client's Business team to resolve defects and problems.</li>
      <li>Ensure technical delivery meets business requirement standards prior to deployment.</li>
    </ul>
  </li>
</ul>

## UI/UX Design

Latest visual design and UI/UX projects fetched dynamically from my [Behance](https://behance.net/dinanov) profile:

<div id="behance-projects-container">
  <p style="color: #6b7280; font-style: italic;">Loading projects from Behance...</p>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const behanceUsername = "dinanov";
    const rssFeedUrl = `https://www.behance.net/feeds/user?username=${behanceUsername}`;
    const apiUrl = `https://api.rss2json.com/v1/api.json?rss_url=${encodeURIComponent(rssFeedUrl)}`;

    fetch(apiUrl)
      .then(response => response.json())
      .then(data => {
        const container = document.getElementById("behance-projects-container");
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
                <span style="font-size: 12px; color: #9ca3af;">Published on Behance • ${pubDate}</span>
              </li>
            `;
          });

          html += '</ul>';
          container.innerHTML = html;
        } else {
          container.innerHTML = '<p style="color: #6b7280;">No Behance projects found or user feed unavailable.</p>';
        }
      })
      .catch(error => {
        console.error("Error fetching Behance feed:", error);
        document.getElementById("behance-projects-container").innerHTML = '<p style="color: #ef4444;">Unable to load Behance projects at this moment.</p>';
      });
  });
</script>