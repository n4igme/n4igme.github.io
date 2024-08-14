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
                    <a href="https://github.com/n4igme/pvascan" class="image fit"><img src="{{ '/images/PythonVAScan.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3 style="color: #333;">Python Vulnerability Scanner</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://n4igme.github.io/emlize/" class="image fit"><img src="{{ '/images/eMailAnalysis.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3 style="color: #333;">eMail Analyst Tools</h3>
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
            <h2>Collections</h2>
        </header>
        <div class="row">
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://university.pagerduty.com/page/certification/" class="image fit"><img src="{{ '/images/PagerDuty.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>PagerDuty University</h3>
                    </header>
                </article>
                <article class="item">
                    <a href="https://training.linuxfoundation.org/certification-catalog/" class="image fit"><img src="{{ '/images/LinuxFoundation.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>The Linux Foundation</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://cyberwarfare.live/" class="image fit"><img src="{{ '/images/CyberWarfareLabs.jpeg' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>CyberWarfare Labs</h3>
                    </header>
                </article>
                <article class="item">
                    <a href="https://www.hackerrank.com/skills-verification/" class="image fit"><img src="{{ '/images/HackerRank.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>HackerRank</h3>
                    </header>
                </article>               
                <article class="item">
                    <a href="https://csilinux.com/academy/" class="image fit"><img src="{{ '/images/CSILinux.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>CSI Linux</h3>
                    </header>
                </article>
            </div>
            <div class="col-4 col-12-mobile">
                <article class="item">
                    <a href="https://secops.group/" class="image fit"><img src="{{ '/images/TheSecOpsGroup.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>The SecOps Group</h3>
                    </header>
                </article>
                <article class="item">
                    <a href="https://www.qualys.com/training/" class="image fit"><img src="{{ '/images/Qualys.png' | relative_url }}" alt="" /></a>
                    <header>
                        <h3>Qualys</h3>
                    </header>
                </article>
            </div>
        </div>
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
