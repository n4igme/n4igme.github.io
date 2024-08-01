---
layout: default
title: Content
---

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