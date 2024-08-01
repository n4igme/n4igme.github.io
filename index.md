---
layout: default
title: Home
---

 <section id="top" class="one dark cover">
    <div class="container">
        <header>
            <h2 class="alt">Hi! This is just a personal log of my stuff.</h2>
            <p>Don't expect too much, please...</p>
        </header>
        <footer>
            <a href="https://github.com/n4igme" class="icon brands fa-github-square"> View on GitHub</a>
        </footer>
    </div>
</section>

<section id="about" class="three">
    <div class="container">
        <header>
            <h2>Who am I?</h2>
        </header>
        <a href="#" class="image featured"><img src="{{ '/images/unnamed.jpg' | relative_url }}" alt="" /></a>
        <p>Be <b>Red</b>, feel <b>Blue</b>, and yet behave <b>Purple</b>.</p>
    </div>
</section>

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

<script>
    document.addEventListener('DOMContentLoaded', function() {
        const API_KEY = 'AIzaSyCdiOBx7On0ZdgQpPRrvv8iXOBgsXwS2SQ';
        const CHANNEL_ID = 'UCk8gNn8kHS0muE_d2jRuIpw';
        const API_URL = `https://www.googleapis.com/youtube/v3/search?key=${API_KEY}&channelId=${CHANNEL_ID}&part=snippet,id&order=date&maxResults=20`;

        async function fetchAndEmbedVideo() {
            try {
                const response = await fetch(API_URL);
                const data = await response.json();
                const videos = data.items.filter(item => item.id.videoId);

                if (videos.length > 0) {
                    const randomVideo = videos[Math.floor(Math.random() * videos.length)];
                    const videoId = randomVideo.id.videoId;
                    document.getElementById('video').src = `https://www.youtube.com/embed/${videoId}`;
                } else {
                    console.log('No videos found');
                }
            } catch (error) {
                console.error('Error fetching videos:', error);
            }
        }

        // Fetch and embed a random video when the page loads
        fetchAndEmbedVideo();
    });
</script>
<section id="content" class="four">
    <div class="container">
        <header>
            <h2>YouTube Channel</h2>
        </header>
    </div>
    <iframe id="video" width="560" height="315" src="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br/>
</section>