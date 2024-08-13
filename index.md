---
layout: default
title: Home
---

<section id="home" class="one dark cover">
    <div class="container">
        <header>
            <h2 class="alt">Hi! This is just a personal log of my stuff.</h2>
            <p>Don't expect too much, please...</p>
        </header>
        <div class="row">
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://github.com/n4igme/pvascan" class="image fit"><img src="/images/pythonvascan.jpg" alt="" /></a>
                    <header>
                        <h3>Python Vulnerability Scanner Tool</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://n4igme.github.io/emlize/" class="image fit"><img src="/images/emailanalysis.jpg" alt="" /></a>
                    <header>
                        <h3>eMail Analyst Tools</h3>
                    </header>
                </article>
            </div>
        </div>
        <footer>
            <a href="https://github.com/n4igme" class="icon brands fa-github-square"> View on GitHub</a>
        </footer>
    </div>
</section>

<section id="about" class="two">
    <div class="container">
        <header>
            <h2>Who am I?</h2>
        </header>
        <a href="#" class="image featured"><img src="{{ '/images/unnamed.jpg' | relative_url }}" alt="" /></a>
        <p>Be <b>Red</b>, feel <b>Blue</b>, and yet behave <b>Purple</b>.</p>
    </div>
</section>

<section id="content" class="three">
    <div class="container">
        <header>
            <h2>YouTube Channel</h2>
        </header>
    </div>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/Dc5sQPeqo5w" frameborder="0" allowfullscreen></iframe><br/>
    <a href="https://www.youtube.com/channel/UCk8gNn8kHS0muE_d2jRuIpw" target="_blank" class="icon brands fa-youtube-square"> Visit on YouTube</a>
</section>

<section id="post" class="four">
    <div class="container">
        <header>
            <h2>LatePost</h2>
        </header>
            
        <div id="medium-feed"></div>
    </div>
</section>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        const sections = document.querySelectorAll('section');
        sections.forEach(section => section.style.display = 'none');

        // Function to show the selected section and hide others
        function showSection(selectedId) {
            sections.forEach(section => {
                if (section.id === selectedId) {
                    section.style.display = 'block';
                } else {
                    section.style.display = 'none';
                }
            });
        }

        // Add event listeners for navigation (modify this part according to your navigation setup)
        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                showSection(targetId);
            });
        });

        // Show the home section by default
        showSection('home');

        // Medium RSS feed integration
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

        fetchMediumRSS();
    });
</script>
