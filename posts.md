---
layout: default
title: LatePost
---

<section id="post" class="two">
    <div class="container">
        <header>
            <h2>LatePost</h2>
        </header>
            
        <div id="medium-feed"></div>
        <script>
            async function fetchMediumRSS() {
                const rssFeedUrl = 'https://medium.com/feed/@bibib';
                const rssToJsonUrl = `https://api.rss2json.com/v1/api.json?rss_url=${encodeURIComponent(rssFeedUrl)}`;

                try {
                    const response = await fetch(rssToJsonUrl);
                    const data = await response.json();
                    displayFeed(data);
                } catch (error) {
                    console.error('Error fetching RSS feed:', error);
                }
            }

            function displayFeed(data) {
                const feedContainer = document.getElementById('medium-feed');
                const items = data.items;

                items.forEach(item => {
                    const feedItem = document.createElement('div');
                    feedItem.innerHTML = `
                        <h3>${new Date(item.pubDate).toLocaleDateString()} | <a href="${item.link}" target="_blank">${item.title}</a></h3>
                    `;
                    feedContainer.appendChild(feedItem);
                });
            }

            document.addEventListener('DOMContentLoaded', fetchMediumRSS);
        </script>
    </div>
</section>