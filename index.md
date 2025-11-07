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
                    <a href="https://n4igme.github.io/gamze/" class="image fit"><img src="{{ '/images/MiniGameCollections.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3 style="color: #333;">Mini-Game Collections</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://github.com/n4igme/pvascan/" class="image fit"><img src="{{ '/images/PythonVAScan.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3 style="color: #333;">Python-VAScan Project</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://n4igme.github.io/scopstls/" class="image fit"><img src="{{ '/images/SecOpsTools.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3 style="color: #333;">Security-Ops Tools</h3>
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
        <p>Be <b style="color: red;">Red</b>, feel <b style="color: blue;">Blue</b>, and yet behave <b style="color: purple;">Purple</b>.</p>
        <header>
            <h2></h2>
        </header>
        <a href="#" class="image featured"><img src="{{ '/images/unnamed.webp' | relative_url }}" alt="" /></a>
        <style>
            .libutton {
                display: flex;
                flex-direction: column;
                justify-content: center;
                padding: 7px;
                text-align: center;
                outline: none;
                text-decoration: none !important;
                color: #ffffff !important;
                width: 200px;
                height: 32px;
                border-radius: 16px;
                background-color: #0A66C2;
                font-family: "SF Pro Text", Helvetica, sans-serif;
                font-size: 14px; 
            }
        </style>
        <center><a class="libutton" href="https://www.linkedin.com/comm/mynetwork/discovery-see-all?usecase=PEOPLE_FOLLOWS&followMember=maruha" target="_blank">Follow on LinkedIn</a></center>
    </div>
</section>

<section id="content" class="three">
    <div class="container">
        <header>
            <h2>YouTube Channel</h2>
        </header>
    </div>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/XXZ_PV_Tg0Y" frameborder="0" allowfullscreen></iframe><br/>
    <a href="https://www.youtube.com/channel/UCk8gNn8kHS0muE_d2jRuIpw" target="_blank" class="icon brands fa-youtube-square"> Visit on YouTube</a>
</section>

<section id="post" class="four">
    <div class="container">
        <header>
            <h2>LatePost</h2>
        </header>
        <div id="rss-feed"></div>
        <div id="pagination"></div>
        <header>
            <h2></h2>
        </header>        
        <div class="row">
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://pentestmag.com/ensuring-application-security-in-the-workplace/" class="image fit"><img src="https://pentestmag.com/wp-content/uploads/2023/12/hakin9_Application_Security_in_the_Workplace_30ff5068-8db4-4250-9f01-6724fd3bdde8.jpg" alt="" /></a>
                    <header>
                        <h3>Ensuring Application Security in the Workplace</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://pentestmag.com/just-script-your-own-vulnerability-scanner-tools/" class="image fit"><img src="https://pentestmag.com/wp-content/uploads/2024/06/hakin9_script_Vulnerability_Scanner_Tools_dabc7660-b484-464d-bf36-86b89cfb9f9b.jpg" alt="" /></a>
                    <header>
                        <h3>Just Script Your own Vulnerability Scanner Tools</h3>
                    </header>
                </article>
            </div>
        </div>
        <header>
            <h2>. . .</h2>
        </header>
    </div>
</section>

<script>
    document.addEventListener('DOMContentLoaded', function () {
        const sections = document.querySelectorAll('section');
        sections.forEach(section => section.style.display = 'none');

        function showSection(selectedId) {
            sections.forEach(section => {
                if (section.id === selectedId) {
                    section.style.display = 'block';
                } else {
                    section.style.display = 'none';
                }
            });
        }

        showSection('home');

        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                showSection(targetId);
            });
        });

        let allItems = [];
        let currentPage = 1;
        const itemsPerPage = 5;

        async function fetchRSSFeeds() {
            const feeds = [
                { url: 'https://medium.com/feed/@bibib', source: 'Medium' },
                { url: 'https://nbsc7.wordpress.com/feed', source: 'WordPress' },
                { url: 'https://kumelsnote.blogspot.com/feeds/posts/default?alt=rss', source: 'Blogspot' }
            ];

            for (const feed of feeds) {
                const rssToJsonUrl = `https://api.rss2json.com/v1/api.json?rss_url=${encodeURIComponent(feed.url)}`;

                try {
                    const response = await fetch(rssToJsonUrl);
                    if (!response.ok) {
                        throw new Error(`Failed to fetch feed from ${feed.source}`);
                    }
                    const data = await response.json();
                    const items = data.items.map(item => ({
                        title: item.title,
                        link: item.link,
                        pubDate: new Date(item.pubDate),
                        source: feed.source
                    }));
                    allItems = allItems.concat(items);
                } catch (error) {
                    console.error(`Error fetching ${feed.source} feed:`, error);
                    const feedContainer = document.getElementById('rss-feed');
                    if (feedContainer) {
                        feedContainer.innerHTML += `<p>Failed to load ${feed.source} feed.</p>`;
                    }
                }
            }

            // Sort by date
            allItems.sort((a, b) => b.pubDate - a.pubDate);

            // Display the first page
            displayPage(currentPage);
        }

        function displayPage(page) {
            const feedContainer = document.getElementById('rss-feed');
            feedContainer.innerHTML = ''; // Clear current content

            // Calculate the items to display on the current page
            const start = (page - 1) * itemsPerPage;
            const end = page * itemsPerPage;
            const itemsToShow = allItems.slice(start, end);

            if (itemsToShow.length) {
                itemsToShow.forEach(item => {
                    const feedItem = document.createElement('div');
                    feedItem.innerHTML = `
                        <h3>${item.pubDate.toLocaleDateString()} - ${item.source} | <a href="${item.link}" target="_blank">${item.title}</a></h3>
                    `;
                    feedContainer.appendChild(feedItem);
                });
            } else {
                feedContainer.innerHTML = 'No feed items available.';
            }

            // Update pagination controls
            updatePaginationControls(page);
        }

        function updatePaginationControls(page) {
            const paginationContainer = document.getElementById('pagination');
            paginationContainer.innerHTML = ''; // Clear existing controls

            const totalPages = Math.ceil(allItems.length / itemsPerPage);

            if (totalPages > 1) {
                if (page > 1) {
                    const prevButton = document.createElement('button');
                    prevButton.textContent = '<<';
                    prevButton.onclick = () => {
                        currentPage--;
                        displayPage(currentPage);
                    };
                    paginationContainer.appendChild(prevButton);
                }

                if (page < totalPages) {
                    const nextButton = document.createElement('button');
                    nextButton.textContent = '>>';
                    nextButton.onclick = () => {
                        currentPage++;
                        displayPage(currentPage);
                    };
                    paginationContainer.appendChild(nextButton);
                }
            }
        }

        fetchRSSFeeds();
    });
</script>
