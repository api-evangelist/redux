---
title: "React Advanced 2023 - Building Better React DevTools with Replay Time Travel"
url: "https://blog.isquaredsoftware.com/2023/10/presentations-react-devtools-replay/"
date: "Tue, 24 Oct 2023 10:00:00 -0500"
author: ""
feed_url: "https://blog.isquaredsoftware.com/index.xml"
---
<p></p>

<p>I work at <a href="https://replay.io">Replay.io</a>, and I've spent all of this year building some incredibly advanced React debugging features that make use of our time-traveling backend API. The biggest one is our React DevTools integration. Early in 2023, I wrote a post for the Replay.io blog on <a href="https://blog.replay.io/how-we-rebuilt-react-devtools-with-replay-routines">How We Rebuilt React DevTools with Replay Routines</a>, which recapped the initial working version. I've spent much of this year improving on that and building other related features.</p>

<p>At React Advanced, I got to share details on how the React DevTools work internally, and dive into how we extract React DevTools component tree data from recorded React apps using a combination of custom Chrome modifications and backend post-processing &quot;routines&quot; that leverage our time-travel API. Along the way, I showed off some crazy tricks like serializing JS functions as strings, sourcemapping original component names from production apps, and generating sourcemaps for React itself!</p>

<p>I also got to participate in a group panel discussion about Open Source, including questions about how we got involved and what it's like to &quot;compete&quot; with other OSS projects.</p>

<p>I've linked the livestream at the right timestamp for now, and will link the final video when it's live.</p>

<h3 id="building-better-react-devtools-with-replay-time-travel-video-https-www-youtube-com-watch-v-jvv3huromu8-start-2896"><a href="https://www.youtube.com/watch?v=jvV3HurOMu8&amp;start=2896">Building Better React DevTools with Replay Time Travel - video</a></h3>

<p>And here's the slides:</p>

<h3 id="building-better-react-devtools-with-replay-time-travel-slides-presentations-2023-10-react-devtools-replay"><a href="https://blog.isquaredsoftware.com/presentations/2023-10-react-devtools-replay/">Building Better React DevTools with Replay Time Travel - slides</a></h3>

<p>and the OSS Panel video:</p>

<h3 id="react-advanced-panel-open-source-video-https-www-youtube-com-watch-v-tuqy9cp38ue-t-8001s"><a href="https://www.youtube.com/watch?v=tUqY9CP38uE&amp;t=8001s">React Advanced Panel: Open Source - video</a></h3>
