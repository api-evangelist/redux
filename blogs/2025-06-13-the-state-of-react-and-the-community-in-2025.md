---
title: "The State of React and the Community in 2025"
url: "https://blog.isquaredsoftware.com/2025/06/react-community-2025/"
date: "Fri, 13 Jun 2025 14:00:00 -0500"
author: ""
feed_url: "https://blog.isquaredsoftware.com/index.xml"
---
<h2 id="introduction">Introduction</h2>

<p>Today, the state of React and its ecosystem is complicated and fractured, with a mixture of successes, skepticism, and contention.</p>

<p>On the positive side: React is the most widely used UI framework, and its concepts have influenced the rest of the JS ecosystem. The React team recently released React 19 after multiple years of development. This was a huge release, including official stable React Server Components support, the new <code>use</code> hook for handling promises, multiple new form integrations, and the removal of many long-deprecated and obsolete features.</p>

<p>However, I've observed and experienced that <strong>the React community has had a growing sense of frustrations and disagreements on where React is headed, how it's developed, and the recommended approaches for using React, as well as the interactions between the React team and the community</strong>. This in turn overlaps with dozens of different arguments that have ricocheted around the React and general web dev communities in the last few years, as well as specific technical concerns with how React works, comparisons with other similar JS frameworks, and how web apps should be built going forward.</p>

<p>What makes this a lot worse is that everyone is arguing and debating a different subset of these concerns, and <strong>many of the stated concerns are either false or outright FUD</strong>. Unfortunately, the arguments and fears have also been complicated by <strong>communications problems, self-inflicted marketing mis-steps, and lack of developer relations work from the React team itself</strong>. All of these intertwine heavily.</p>

<p>I've been involved in many related discussions on social media. I've written numerous comments both defending and critiquing the React team, explaining why they made certain decisions or how things actually happened, pushing for improvements to docs and explanations, and more.</p>

<p>Trying to cover just <em>some</em> some of these topics has required an extensive and detailed post (and I'm not even going to touch on the &quot;is React bad / how does React compare to other tools?&quot; topics, which are even further out of scope). But, having spent far too many hours debating and explaining, I feel the need to write a consolidated post that covers many of these topics together.</p>

<p>I've also presented <a href="https://blog.isquaredsoftware.com/2025/06/presentations-react-community-2025/">a talk based on the topics in this post</a> as well.</p>

<h3 id="goals">Goals</h3>

<p><strong>My goals for this post are:</strong></p>

<ul>
<li><strong>Give an overview of how React has developed over time</strong></li>
<li><strong>Describe the forces driving React's development</strong></li>
<li><strong>Clarify why and how React's recent development directions have happened, and explain some of the architectural decisions behind that work</strong></li>
<li><strong>Clarify and dispel FUD and confusion regarding the motivations and intent behind React's development</strong></li>
</ul>

<h3 id="table-of-contents">Table of Contents</h3>

<ul>
<li><a href="#introduction">Introduction</a>

<ul>
<li><a href="#goals">Goals</a></li>
<li><a href="#background-my-role-and-involvement-in-the-react-community">Background: My Role and Involvement in the React Community</a></li>
<li><a href="#biases-and-caveats">Biases and Caveats</a></li>
</ul></li>
<li><a href="#a-brief-history-of-react">A Brief History of React</a></li>
<li><a href="#react-s-relationship-with-its-owners">React's Relationship with Its Owners</a>

<ul>
<li><a href="#facebook-meta">Facebook / Meta</a></li>
<li><a href="#vercel-next-and-react">Vercel, Next, and React</a></li>
</ul></li>
<li><a href="#react-usage-patterns">React Usage Patterns</a>

<ul>
<li><a href="#standard-react-architectures">Standard React Architectures</a></li>
<li><a href="#react-build-tool-usage">React Build Tool Usage</a></li>
</ul></li>
<li><a href="#inside-react-server-components">Inside React Server Components</a>

<ul>
<li><a href="#react-server-component-development-and-vercel">React Server Component Development and Vercel</a></li>
<li><a href="#rscs-frameworks-and-bundlers">RSCs, Frameworks, and Bundlers</a></li>
</ul></li>
<li><a href="#community-concerns-and-confusion">Community Concerns and Confusion</a>

<ul>
<li><a href="#concern-vercel-next-and-react">Concern: Vercel, Next, and React</a></li>
<li><a href="#concern-react-only-works-with-next">Concern: React Only Works with Next</a></li>
<li><a href="#concern-react-might-someday-stop-working-in-client-apps">Concern: React Might Someday Stop Working in Client Apps</a></li>
<li><a href="#concern-why-is-react-pushing-frameworks">Concern: Why Is React Pushing Frameworks?</a></li>
<li><a href="#concern-server-component-docs-and-explanations">Concern: Server Component Docs and Explanations</a></li>
</ul></li>
<li><a href="#takeaways-from-the-concerns">Takeaways from the Concerns</a></li>
<li><a href="#final-thoughts">Final Thoughts</a></li>
</ul>

<h3 id="background-my-role-and-involvement-in-the-react-community">Background: My Role and Involvement in the React Community</h3>

<p>(<em>aka &quot;who am I, why should you trust my descriptions, and why should you care at all what my opinions are about this? 😄&quot;</em>)</p>

<p><strong>I am not and never was part of the actual React team</strong>. That said, <strong>I've been deeply involved with the React ecosystem since 2015</strong>, and it's fair to say I'm as much part of the &quot;React community inner circle&quot; as anyone outside of Meta or Vercel.</p>

<p>As a TL;DR:</p>

<ul>
<li>I've used React since 2015</li>
<li>I maintain the Redux family of libraries, contributed to React, and been involved in React ecosystem discussions</li>
<li>I've written numerous lengthy tutorials on React and Redux, and frequently speak on React and Redux</li>
<li>I've been involved in moderating major React community sections most of that time</li>
</ul>

<p>If you want the long version:</p>

<p><details class="detailed-explanation">
  <h4>My Accomplishments, Involvement, and Credentials</h4></p>

<p>I started learning React in mid-2015, after using Backbone, jQuery, and GWT to build some geospatial visualization apps. Over the next year, I went from <a href="https://blog.isquaredsoftware.com/2016/09/how-i-got-here-my-journey-into-the-world-of-redux-and-open-source/">reading a few React tutorials, to lurking in the Reactiflux chat channels, to answering so many questions I became a moderator, to volunteering to write a Redux FAQ, to being handed the keys as the new Redux maintainer</a>.</p>

<p>I've maintained Redux since mid-2016. <a href="https://blog.isquaredsoftware.com/2019/10/redux-toolkit-1.0/">I created Redux Toolkit</a> as the modern way to write Redux apps. While working on Redux, I've designed and shipped <a href="https://blog.isquaredsoftware.com/2018/11/react-redux-history-implementation/">every version of React-Redux since v5</a>. I've had multiple conversations with the React team about how React should work with external state management libraries, and I was <a href="https://github.com/reduxjs/react-redux/pull/1808">the sole alpha-tester for the development of the <code>useSyncExternalStore</code> hook</a>.</p>

<p>I've written hundreds of thousands of words of tutorials and blog posts teaching people how to use React and Redux and how they work, including the <a href="https://redux.js.org/tutorials/essentials/part-1-overview-concepts">&quot;Redux Essentials&quot; tutorial</a> and my widely acclaimed <a href="https://blog.isquaredsoftware.com/2020/05/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior/">&quot;Guide to React Rendering Behavior&quot; post</a> (which is routinely recommended by the community as the single best explanation of how React actually works in practice). I've written thousands of comments and answered questions across Github, the Reactiflux Discord, Reddit, Twitter, Hacker News, and Stack Overflow, about all things React and Redux and JS. I've been referred to as <a href="https://blog.isquaredsoftware.com/about/#oss-support">&quot;the tech support for the React community&quot; and &quot;the master archiver and indexer of all things React&quot;</a>.</p>

<p>I've <a href="https://blog.isquaredsoftware.com/presentations/">spoken at numerous React-related conferences</a> on topics ranging from <a href="https://blog.isquaredsoftware.com/2023/08/presentations-react-rendering-behavior/">how React works</a> to <a href="https://blog.isquaredsoftware.com/2024/11/presentations-maintaining-community/">best practices and lessons learned maintaining widely used OSS libraries</a>. I've been on <a href="https://blog.isquaredsoftware.com/presentations">numerous podcasts discussing React and Redux</a>, including the ongoing <a href="https://www.reactiflux.com/transcripts/tmir-2024-12">&quot;This Month in React&quot; podcast hosted by the Reactiflux Discord</a> where we talk about the latest news, releases, and insights on React and the community.</p>

<p>I was part of the initial private React Hooks preview feedback group, and the invite-only-but-public React 18 Working Group, where we gave feedback on the design, docs, and usage aspects for both releases.</p>

<p>I'm an administrator in <a href="https://www.reactiflux.com">the Reactiflux Discord</a>, and have been the primary active moderator in <a href="https://reddit.com/r/reactjs/">the /r/reactjs subreddit</a> for several years.</p>

<p>I've dug inside of React, the repo, and the internals, including <a href="https://github.com/facebook/react/pull/26446">submitting a PR that generated production sourcemaps for React builds</a>, and <a href="https://blog.isquaredsoftware.com/2023/10/presentations-react-devtools-replay/">using time-travel debugging to integrate the React DevTools into Replay's DevTools</a>.</p>

<p></details></p>

<p>The point of listing those accomplishments is to establish that <strong>I have a long history and expertise around how React is developed, what's going on in the React community, what's happening <em>inside</em> the React team, and trying to help people learn React and Redux.</strong></p>

<h3 id="biases-and-caveats">Biases and Caveats</h3>

<p>Since this is the Internet, I'll try to preempt some concerns folks might have with me writing this.</p>

<p><strong>I am most definitely <em>not</em> always right, and I'm definitely going to end up describing some things incorrectly due to limited knowledge, misunderstandings, or over-summarizing</strong>. That said, <strong>I'm writing this as a best-faith effort to describe history, motivations, and behaviors as honestly and accurately as I can</strong>.</p>

<p>in more detail:</p>

<p><details class="detailed-explanation">
  <h4>More Detailed Biases and Caveats</h4></p>

<p>Since I maintain Redux, that does bias my own opinions to how React gets used, as well as the kinds of problems I deal with.</p>

<p>While I've used React in some form consistently since 2015, my own experiences using React have become more limited and more niche over time. Most of the React apps I've worked on have been internal tools with limited distribution, and mostly &quot;desktop-style apps in a browser&quot; - in other words, true SPAs without even any routing or CRUD-type behavior. I did work on <em>one</em> CRUD/dashboard-style app, but it was limited in scope. I've never built apps with huge audiences, never used SSR or RSCs in practice, never had to worry about i18n or other large-scaling concerns. I've spent much of my time working on libraries and developer tools, and much less time in the day-to-day of &quot;typical&quot; React app development.</p>

<p>I've read and been involved in inside-baseball React community discussions that the average React app dev never hears or cares about.</p>

<p>I've had personal interactions with the React team online and in person that have been both very positive, and very negative and frustrating. These color my own perspectives. But, I've also had enough discussions with other members of the community to have good confidence that many others share my concerns and opinions.</p>

<p>My normal writing style involves linking as many references and sources as possible. For this post I'll <em>try</em> to do that, but a lot of these historical descriptions and observations will be difficult to find specific sources for, so please trust that I'm doing my best to describe them accurately even if summarized.</p>

<p></details></p>

<p>So, with all those caveats stated, let's get going.</p>

<h2 id="a-brief-history-of-react">A Brief History of React</h2>

<p>The early history is covered better in other places, including <a href="https://www.youtube.com/watch?v=8pDqJVdNa44">the React Documentary</a>, but to provide some context for the rest of this post:</p>

<p>React was developed internally at Facebook around 2011-12, and open-sourced in 2013. It gathered a handful of external contributors, but <strong>until recently all actual development was done by the React core team inside of Facebook / Meta</strong>.</p>

<p>While the core concepts of React have always stayed the same (components, props, state, data flow), the implementation details, public APIs, and breadth of scope have shifted over time. React went from creating components with <code>createClass</code>, to ES6 <code>class MyComponent extends React.Component</code>, to <code>function MyComponent()</code>. React split from web-only to supporting mobile with React Native, then became customizable for other platforms such as WebGL (<code>react-three-fiber</code>) and CLI (<code>ink</code>) via a customizable <code>react-reconciler</code> core. The internals were completely rewritten to a new &quot;Fiber&quot; architecture, unlocking further architectural changes. Function components gained the ability to have state and side effects with the release of hooks in 2018.</p>

<p>For years, <strong>React pitched itself as a minimal UI-focused rendering library</strong> (&quot;the 'V' in 'MVC'&quot;, &quot;A JS library for building user interfaces&quot;). Other frameworks like Angular or Ember were fully batteries included and had significant opinions about how to build and structure apps, but the React team left all of that up to the community. This led to a massive explosion in the ecosystem, both for better and worse. For any conceivable library category, there were dozens of competing tools solving overlapping problems: state management (Redux, Mobx, Zustand, ....), CSS and styles (Styled-Components, Emotion, CSS Modules, ....), data fetching (React Query, Apollo, SWR, RTK Query, ....), build tools (Babel, Webpack, ESBuild, Vite, Parcel, ....), and hundreds more.</p>

<p>React users have always had to begin a project by picking and choosing a set of libraries to solve the various use cases in their app. Additionally, React could be used in numerous ways: rendering every single element on the client side in a Single-Page App (SPA), rendering multiple subtrees attached to a server-rendered page, on the server as part of a Multi-Page App (MPA), and much more. The flexibility and variety of ecosystem options has been both a strength and a weakness. You <em>get</em> to choose the exact combination of tools you need for your project... but you also <em>have</em> to choose a combination of tools. That leads to decision fatigue, variations in project codebases, and constant changes in what tools are commonly used.</p>

<p>Overall, <strong>both the React library and the React team intentionally stayed unopinonated</strong>. They didn't want to play favorites with specific tools in the ecosystem, their time and attention was focused on building React itself, and they still viewed the scope of React as being somewhat narrow.</p>

<p>That ecosystem variety provided flexibility, but also complexity. This was especially true with build tools. Early React tutorials often spent multiple pages at the start explaining &quot;here's how to configure Webpack and Babel&quot;, before you could even write your first React component. This led the React team to build a pre-packaged build tool configuration called Create React App. CRA was a CLI tool that could generate a new React project from a template, and built it with a a highly complex and customized Webpack + Babel config that was designed to make it simple to start a new project with a single command. That config was kept encapsulated as a black box, to hide the complexity out of sight.</p>

<p>React never had a built-in method for data fetching, so it was standard to use third-party libraries to fetch and cache data. React did have server rendering (SSR) capabilities early on, with methods to render React component trees to HTML as strings or streams, but those had to be used manually in server handlers. Over time, other prepackaged React build systems and &quot;frameworks&quot; became popular. Next.js also wrapped Webpack, but added more features like built-in server rendering with filesystem routing conventions and page-based data fetching. Gatsby generated sites from GraphQL-based data sources. Later, Remix added server &quot;data loaders&quot; and pushed for more HTML/platform-based usage conventions.</p>

<p>In late 2020, the React team announced a prototype for &quot;React Server Components&quot;, an architectural approach that allowed async React components to run on the server and fetch data, then render child components and pass the children and data to React running on the client. This was intended to be a React-idiomatic solution to data fetching, and marked a significant shift from React's original &quot;just the view on the client&quot; historical pitch. During the development of RSCs, some of the React core team members left Meta and joined Vercel, creators of Next.js. They continued building out the initial RSC implementation, and worked with the Next dev team to rearchitect Next with the new &quot;App Router&quot;, the first production implementation of RSCs.</p>

<p>The React team also spent 2020-2023 completely rewriting the React docs site from scratch. The new React docs at <a href="https://react.dev">react.dev</a> have a fantastic tutorial that walks through React's concepts step-by-step, with numerous in-page examples in runnable sandboxes, as well as much improved API reference pages.</p>

<p>When the new docs came out, the React team made a significant shift in how they recommended using React. Previously, the old React docs <a href="https://legacy.reactjs.org/docs/create-a-new-react-app.html#recommended-toolchains">recommended starting with CRA if you were learning or building a client-side SPA</a>, or pointed to a couple other frameworks like Next or Gatsby if you needed SSR or static sites. With the new docs, the React team changed their approach, and begin specifically and strongly recommending &quot;you <em>should</em> use a framework to write React apps - they have routing, data fetching, and build capabilities built in&quot;. This also tied into the work to build RSCs. As part of this, the <a href="https://web.archive.org/web/20250125034212/https://react.dev/learn/start-a-new-react-project">&quot;Start a New React Project&quot; page</a> specifically warned <em>against</em> using React without a framework. Next was listed prominently on that docs page - ordered first on the &quot;Frameworks&quot; list (for the Pages router), and then mentioned further down as the only available RSC implementation. React team members working at Vercel were quoted as saying <a href="https://x.com/acdlite/status/1549853625673023488">&quot;I think of the upcoming Next.js release as the 'real' React 18 release&quot;</a>,</p>

<p>This tied into Create React App having effectively died around 2022. It had been unmaintained for some time prior. When a PR was filed recommending &quot;mark CRA as deprecated and recommend Vite&quot;, Dan Abramov wrote an detailed comment explaining <a href="https://github.com/reactjs/react.dev/pull/5487#issuecomment-1409720741">why CRA was created, problems with CRA, the rise of frameworks, and the shift of React's vision</a>. In response, the React community collectively moved on from CRA, and the docs stopped recommending it, but nothing was done to officially mark it as &quot;deprecated&quot;.</p>

<h2 id="react-s-relationship-with-its-owners">React's Relationship with Its Owners</h2>

<p>Today, React's development work is sponsored and owned by two companies: Meta (formerly Facebook), and Vercel.</p>

<h3 id="facebook-meta">Facebook / Meta</h3>

<p>From the beginning, React was a Facebook / Meta-owned project. The code was open-sourced, and anyone <em>could</em> submit a PR, but essentially all dev work was done by the React team at Meta.</p>

<p>This had significant impacts on how React was developed. React core team meetings were generally internal, as were any roadmaps. The React team would often prototype a half-dozen ideas for a problem space, then get app teams at Meta to try them out for vetting. By the time a new React feature was announced, it had gone through many internal iterations and been validated in actual usage. At the same time, the React team has also been responsible for supporting Meta's app teams with bug fixes and other support.</p>

<p>Despite this, the React team has had a fairly free hand in how they've developed the library. While React was created inside Facebook for Facebook usage, the React team itself has decided their roadmap and long-term vision for how the library should work. For the most part, React's actual development process and roadmap has been driven themselves, rather than by other influences inside Facebook / Meta. That said, they also do have to justify their own performance and how projects benefit Meta.</p>

<p>Meta's own use of React is both widespread and distinct from how the community uses it. Meta has its own massive server infrastructure, including standard techniques for data fetching, routing, security, and more. Meta invented the GraphQL protocol, as well as the Relay GraphQL client layer, and frequently uses those with their React code. This means that Meta's React use rarely needs third-party libraries for routing, state management, styling, or other problems common to the rest of the community.</p>

<h3 id="vercel-next-and-react">Vercel, Next, and React</h3>

<p>Vercel is primarily a hosting platform for web apps. They mostly make money by having more people host apps on their platform, and charge for the convenience of easier usage. They have put massive amounts of engineering time into building the Next.js framework (as well as supporting other frameworks), and making it trivial to set up and deploy Next apps on Vercel infrastructure.</p>

<p>Vercel's CEO, Guillermo Rauch, is a long-time believer in React and its capabilities, as shown by his 2015 blog post <a href="https://rauchg.com/2015/pure-ui">Pure UI</a> that talks about the power of React's rendering model.</p>

<p>In late 2021, <a href="https://vercel.com/blog/supporting-the-future-of-react">React team lead Sebastian Markbage left Meta to join Vercel</a>. This was the first instance of full-time React core team members working anywhere other than Meta. He was later joined by core team member Andrew Clark and former React org lead Tom Occhino. The React team had already done significant prototyping on RSC functionality in React internally. Seb helped design the Next.js App Router, and Vercel had additional engineers begin contributing to React's core and server rendering capabilities.</p>

<p>Today, <a href="https://react.dev/community/team">the React team is split between Meta and Vercel</a> (with a majority still at Meta), plus a handful of team members or consistent contributors externally.</p>

<h2 id="react-usage-patterns">React Usage Patterns</h2>

<h3 id="standard-react-architectures">Standard React Architectures</h3>

<p>The React (and ReactDOM in particular) library itself does not care how you use it within a page. You can serve a near-empty HTML placeholder and render a React tree that generates the entire page contents on the client side, as a Single-Page App (&quot;SPA&quot;). You can use React for server rendering (&quot;SSR&quot;), where the server dynamically responds to each request, or static site generation (&quot;SSG&quot;), where you pre-generate static HTML pages at build time. You can serve a static or server-rendered HTML page using any language or framework (Python + Django, Ruby + Rails, PHP + WordPress, .NET, etc), and sprinkle bits of React throughout the page to add interactivity.</p>

<p>That said, by 2015 React was most commonly used for client-side SPA app architectures. As with everything, these had tradeoffs. They made it easier to generate the page contents (it's all React components), had faster user interactions (show a different component on click or route change instead of a full page refresh), and enabled richer app experiences. It didn't matter what the backend was (JS, Java, PHP, .NET, Python) - just expose a JSON API and fetch data. However, they also were slower to load the initial page bundle, and client-side routing could lead to uncanny interactions vs native browser behavior.</p>

<p>Data fetching on those clients was initially fairly manual, and required careful logic in side effects (such as triggering a fetch in <code>componentDidMount</code> to request data when a component first rendered). This was often done with Redux-based logic to handle the fetching and caching, although that code was typically full of boilerplate and complexity. Later, purpose-built data fetching libraries like React Query, Apollo, SWR, and RTK Query greatly simplified data fetching on the client, providing purpose-built <code>useQuery</code> hooks and prebuilt caching mechanisms.</p>

<p>Frameworks like Next and Remix provided standardized approaches to server-rendering React, with built-in filesystem routing conventions. However, there was no convention for server-based data fetching. Next invented a <code>getServerSideProps</code> mechanism to specify an async function for fetching alongside a component. Remix later invented &quot;loaders&quot; with a similar architecture. Neither of those <em>felt</em> particularly native to React.</p>

<p>This has led to a general mindset shift in the React ecosystem. There's more of a push for SSR-based architectures to improve page loading experiences and minimize the amount of JS needed for a page, as well as removing the need to use data fetching libraries on the client side. The React team has argued loudly against &quot;waterfalls&quot; in data fetching in order to improve page loading performance, and even client-side routers like React Router and TanStack Router offer ways to prefetch data at the route/page level rather than triggering fetches nested deep in the component tree.</p>

<h3 id="react-build-tool-usage">React Build Tool Usage</h3>

<p>It's worth looking at the download stats for several major React related build tools and frameworks to get a sense of usage scale in the ecosystem over time and today.</p>

<p>Loosely put, today the major options for tools in terms of mindshare and/or downloads are</p>

<ul>
<li><a href="https://nextjs.org">Next.js</a> (SSR / SSG / RSC / SPA)</li>
<li><a href="https://remix.run/">Remix</a> / React-Router v7 (SSR / SSG / SPA)</li>
<li><a href="https://vite.dev/">Vite</a> (SPA)</li>
<li><a href="https://create-react-app.dev/">Create React App</a> (SPA)</li>
</ul>

<p>It's also worth noting that Vite itself started off from the Vue ecosystem, but has become a standardized and widely used build tool with support for many different client-side frameworks. It also has a plugin ecosystem, including the plugin for React support, and has become the build tool of choice for various frameworks. That includes Remix / React-Router, which recently switched from using ESBuild internally to providing a Vite plugin to enable their SSR and SSG support.</p>

<p>Here's <a href="https://npm-stat.com/charts.html?package=react-dom&amp;package=next&amp;package=%40vitejs%2Fplugin-react&amp;package=%40remix-run%2Freact&amp;package=react-scripts&amp;from=2018-01-01&amp;to=2025-05-31">a graph of NPM downloads for these tools over the last few years</a>, with ReactDOM for scale:</p>

<p><img alt="NPM download stats" src="https://blog.isquaredsoftware.com/images/2025-06-react-community-2025/react-frameworks-usage.png" /></p>

<p>Until recently, the React docs also listed Gatsby as a recommended framework for web and Expo as the only recommended framework for React Native. Gatsby effectively died after being purchased by Netlify. Meanwhile, Astro is a more generic static-site-focused tool that supports many frameworks including React. Here's their download stats for comparison:</p>

<p><img alt="NPM download stats 2" src="https://blog.isquaredsoftware.com/images/2025-06-react-community-2025/react-frameworks-usage-2.png" /></p>

<p>A few takeaways from those stats:</p>

<ul>
<li>Next.js is most widely used</li>
<li>Vite's React plugin has grown steadily, and is now the second most widely used React-related build tool</li>
<li>CRA usage peaked in mid-2023 and has been declining since, but still sees considerable usage</li>
<li>Remix has strong word of mouth at this point, but is relatively smaller. React Router is very widely used, but the newer versions that support &quot;framework mode&quot; aren't as widely adopted yet.</li>
<li>Gatsby never had anywhere near as much traction as Next, CRA, or Vite, and Astro recently surpassed it.</li>
<li>Astro is not React-specific, but has roughly the same downloads as Remix does</li>
<li>Vite + CRA together equal Next's usage, which shows that there's still a strong demand for plain SPA projects in the React ecosystem</li>
</ul>

<h2 id="inside-react-server-components">Inside React Server Components</h2>

<h3 id="react-server-component-development-and-vercel">React Server Component Development and Vercel</h3>

<p>The React team had experience with server-based data fetching from Meta's infrastructure, as well as automatically splitting JS bundles and lazy-loading code. However, unlike previous React feature development, their options for iterating on and shipping RSCs inside of Meta were limited. Meta's existing server infra and technologies made it difficult to fully design RSCs in a way that the rest of the community could actually use and benefit from.</p>

<p>It's worth noting that <strong>React Server Components were the <em>React</em> team's vision for how to write React apps in the future</strong>. As far as I know, this was not something that either Meta or Vercel came up with, or pushed the React team to build.</p>

<p>There had been intermittent discussion and complaints about &quot;all of React's development is done by Meta employees&quot; for years, and occasional comments of &quot;it might be nice if there was a 'React Foundation', or folks outside Meta working directly on React&quot;. While I don't know the actual discussions involved, from the outside my understanding is that <strong>the React team approached Vercel and pitched their vision of RSCs, and Vercel agreed to be the new proving ground as RSCs were developed</strong>. This led to Sebastian Markbage (and later Andrew Clark) moving from Meta to Vercel, and the Next team spending huge amounts of time, money, and engineering effort to design and build the Next App Router as the first working implementation of RSCs.</p>

<p>As <a href="https://www.reddit.com/r/reactjs/comments/1kg3yqh/rsc_for_astro_developers_overreacted/mr2bl62/">Dan Abramov described it</a>:</p>

<blockquote>
<p>The Vercel team has allocated many full-time engineer/years to implementing the things the React team wanted. That’s not to speak of directly taking the technical direction from the React team. Next.js was more or less rewritten from scratch.
<br />
The person designing Next.js now is the person who invented React Hooks. So if anything, <strong>it was more of a case of React team “taking over” the Next.js direction</strong> rather than “favouring” it.</p>
</blockquote>

<p>There <em>were</em> efforts made to get other frameworks and companies involved in that process. Shopify's Hydrogen framework did some very early testing and feedback of RSCs, but eventually concluded it wasn't a good fit for them. The Remix team was asked several times if they'd like to be involved, but initially decided to focus on their own approaches.</p>

<p>As a result, <strong>Next became the first (and effectively still the <em>only</em>) &quot;production-ready&quot; RSC implementation</strong>. Today several other frameworks are working on RSC integration (including Parcel, React Router, and Waku), but Next's App Router is the only widespread option for using RSCs today.</p>

<h3 id="rscs-frameworks-and-bundlers">RSCs, Frameworks, and Bundlers</h3>

<p>I commonly see questions like &quot;why do RSCs require a bundler or framework? Why can't they just be built into React?&quot;.</p>

<p>React's existing server-rendering methods like <code>renderToString</code> and <code>renderToPipeableStream</code> could be called anywhere, such as an Express route handler. However, architecturally RSCs are much more complex. RSC functionality requires parsing code to look for the <code>'use client'</code> and <code>'use server'</code> directives, then transforming that code to insert the appropriate calls to register Client Components and server functions with the RSC core functionality. That requires tight integration with a bundler, so that it can correctly determine the full module graph for both server and client and compile them appropriately.</p>

<p>Additionally, while the React core implements the actual RSC functionality, and provides primitives for sending serialized components and data between client and server, it's up to a framework to actually <em>call</em> and use those primitives in the right place. This is primarily about integration with a router, so that the client app receives the right lazy-loaded Client Components, and calls the right endpoints with actions and data.</p>

<p>This also means that every framework's use and implementation of RSCs will be different. Next made very specific implementation decisions with the App Router for handling layouts and routing. Other frameworks and build tools like Waku, Parcel, and React Router are already making some very different design decisions.</p>

<p>Overall, RSCs are an unusual hybrid feature. The main functionality is built directly into the React core packages, but that functionality cannot be used until it is integrated into some kind of bundler/router/framework combination.</p>

<h2 id="community-concerns-and-confusion">Community Concerns and Confusion</h2>

<p>With all that history and context in mind, let's move on to answering (and hopefully clarifying or dispelling) several frequently repeated concerns that are either confused, FUD, or outright conspiracy theories.</p>

<h3 id="concern-vercel-next-and-react">Concern: Vercel, Next, and React</h3>

<p>There's now an extremely common viewpoint that &quot;Vercel is driving React development, with a goal of making more money hosting sites&quot;. As an example, this is the highest-upvoted comment from a Reddit thread earlier this year:</p>

<blockquote>
<p>&quot;Vercel has effectively taken over React and has a primary interest of pushing users to NextJS, deployed on Vercel, so Vercel shareholders get richer.&quot;
<a href="https://www.reddit.com/r/react/comments/1iarj85/xbluesky_react_recently_feels_biased_against_vite/m9cb51h/">https://www.reddit.com/r/react/comments/1iarj85/xbluesky_react_recently_feels_biased_against_vite/m9cb51h/</a></p>
</blockquote>

<p>This ties into several other related points of concern:</p>

<ul>
<li>Next is recommended first in the React docs, and the Next App Router is also mentioned as the main example under &quot;Which features make up the React team’s full-stack architecture vision?&quot;</li>
<li>Next is still the only production implementation of RSCs</li>
<li>React team members have been quoted as saying that <a href="https://x.com/acdlite/status/1549853625673023488">&quot;This Next release is the real React 18&quot;</a></li>
</ul>

<p>I can see how people might come to this conclusion. Vercel hired several React team members, who are working on both React itself and Next. Timeline-wise, this did naturally coincide with the development of RSCs, and the new shift towards pushing users to use a framework... and look, the &quot;obvious&quot; framework is indeed Next! Meanwhile, Vercel has put massive amounts of money and effort into making Next easy to deploy and host on Vercel. It's <em>possible</em> to host Next elsewhere, but there's always been features that didn't work or things were hard to configure.</p>

<p>All that said, from everything I've seen, this take generally inverts the cause and effect, and is mostly FUD. Yes, of course Vercel has invested in efforts they think will end up making them money. But, per above, everything I've seen describing Seb and Andrew going to Vercel and the development process of RSCs says that it was the <em>React team</em> that drove this set of changes.</p>

<p>RSCs were the React team's vision. They couldn't effectively be prototyped and tested inside of Meta, so for the first time there was a need for some other sponsor to invest in the development and provide a setting to iterate on the design. I don't know the specifics of how it happened, but my understanding is that the React team convinced Vercel to buy into the React team's vision, <em>and</em> let them drive rearchitecting Next to design the App Router approach that would match that vision.</p>

<p>There certainly has been <em>some</em> amount of &quot;Next needs this&quot;-type changes to React. I know I saw several PRs getting merged in the React repo the night before one of the NextConfs that had a significant Next version announcement (possibly the stable App Router in 13.4?). But, it was still the React team members doing that work.</p>

<p>At this point, the React team is split. The majority are still at Meta, but the members at Vercel are key to the core implementation. I've read that &quot;React team meetings are still the same as always&quot;, but I wouldn't be surprised if there's <em>some</em> additional complexity from splitting that way.</p>

<p>All that said, I do think that &quot;Vercel took over React&quot; is wrong, and it's more like &quot;part of React core migrated to Vercel and convinced Vercel to align with React's vision&quot;. I also don't see evidence that &quot;Vercel&quot; is driving the design of React, or that the emphasis on frameworks and RSCs is with the specific intent to make Vercel money.</p>

<h3 id="concern-react-only-works-with-next">Concern: React Only Works with Next</h3>

<p>I've seen multiple comments online with people saying, either seriously or wonderingly, that &quot;React only works with Next now&quot;.</p>

<p>This is easily refuted. <strong>Even just looking at <a href="https://react.dev/learn/start-a-new-react-project">the &quot;Start a New React Project&quot; page</a> shows other frameworks that are <em>not</em> Next</strong>, as well as the somewhat infamous &quot;Can I use React without a framework?&quot; section.</p>

<p>Clearly this is a complete misunderstanding of how React works.</p>

<p><em>But</em>, it also says something about how confused the messaging around React, &quot;use frameworks&quot;, and Vercel's influence has become.</p>

<p>I'll tack on the very related &quot;Should I use Next or React?&quot; question, which also pops up frequently. The literal reading is that &quot;Next&quot; and &quot;React&quot; are different things. This is also clearly wrong. Next is a framework that <em>uses</em> the React libraries. It's a superset, not a competitor. I assume that what most people <em>mean</em> is &quot;should I use Next, or a client-side SPA like CRA or Vite?&quot;, but they don't have the vocabulary to state that clearly.</p>

<p>Again, that shows how much confusion there is around the boundaries here.</p>

<h3 id="concern-react-might-someday-stop-working-in-client-apps">Concern: React Might Someday Stop Working in Client Apps</h3>

<p>I've seen this one come up repeatedly too. The concern is that &quot;if the React team is putting <em>this</em> much emphasis and work into features that require a server, does that mean that <em>someday</em> the client-side functionality might change or go away?&quot;.</p>

<p>I can understand <em>why</em> people have this fear. It's driven by the huge shift in tone and emphasis from the React team, as well as the amount of effort they've put into server-side functionality.</p>

<p>However, it's also clearly impossible that this will ever happen. <strong>React's client rendering functionality <em>will not</em> ever go away!</strong> Just the fact that Meta itself has millions of lines of existing React code shows that. On top of that, the React team <em>has</em> always been extremely good about code-level backwards compatibility - describing breaking changes, keeping around deprecated features for years before finally removing them, providing migration guides and codemods.</p>

<p>It's also worth noting that many of the features in React 19 and 19.1 are client-only. If anything, the community has over-estimated the amount of effort put into server-side functionality, and missed the amount of effort put into client-side features.</p>

<h3 id="concern-why-is-react-pushing-frameworks">Concern: Why Is React Pushing Frameworks?</h3>

<p>And that leads us to our next argument: <strong>why is the React team so dead-set on making all React users use frameworks, to the point of telling people they're doing it wrong otherwise?</strong></p>

<p>This is a concern that I have a lot more sympathy and agreement for. I just said that I don't think they're saying &quot;use frameworks&quot; with a goal of &quot;get people using Next and hosting on Vercel&quot;, so what's the reasoning?</p>

<h4 id="react-team-opinions-on-frameworks">React Team Opinions on Frameworks</h4>

<p>Andrew Clark's <a href="https://x.com/acdlite/status/1617667097424986114">tweets from Jan 2023 state the intent pretty clearly</a>:</p>

<blockquote>
<p>If you use React, you should be using a React framework. If your existing app doesn't use a framework, you should incrementally migrate to one. If you're creating a new React project, you should use a framework from the beginning</p>

<p>Your React framework of choice should have built-in solutions for data fetching, routing, and server rendering. Frameworks don't treat these as independent concerns — they provide deeply integrated solutions that are easy to use and result in excellent performance out of the box.</p>

<p>If you choose to forgo a framework, what you're really choosing is to build your own bespoke framework, one that's likely much worse than what you'd get off the shelf. Even if you think your bespoke framework is better than the alternatives today, will that be true in a year?</p>

<p>It takes lots of time and energy to keep up with the state of the art. Are you ready to become a framework maintainer? Or are there better things you should be doing with your time?</p>

<p>The main thing that has changed since then is that the frameworks got really, really good. It used to be that plain React + Webpack was as good or better than all-in-one frameworks. IMO, that's no longer true</p>

<p>The question isn't whether it's possible to build a React app without using a framework. You'll always have that option.
The question is whether your homegrown set up can compete with the industry leaders — on features, on performance, on DX.
The bar is constantly being raised.</p>
</blockquote>

<p>Similarly, in Dan Abramov's <a href="https://github.com/reactjs/react.dev/pull/5487#issuecomment-1409720741">explanation of why they were considering CRA deprecated</a>:</p>

<blockquote>
<p>Create React App solved only one side of the problem. It provided a good (at the time!) development experience, but it didn't impose enough structure to help you leverage the strong sides of the web for a good user experience. You could try to solve these problems yourself, but that would involve &quot;ejecting&quot; and significantly customizing your setup, which defeated the point of Create React App. Every truly efficient React setup was custom, different, and unachievable with Create React App.</p>

<p>These user experience problems are not specific to Create React App. They are not even specific to React. For example, apps created from the Vite homepage templates for Preact, Vue, Lit, and Svelte suffer from all of the same problems. These problems are inherent to purely client-side apps with no static site generation (SSG) or server-side rendering (SSR).</p>

<p>If you build entire apps with React, being able to use SSG/SSR is important. The lack of support for them in Create React App is glaring. But it's not the only area where Create React App is behind</p>

<p>React itself is only a library. It does not dictate how to do routing or data fetching. Neither does Create React App. Unfortunately, this means that neither React alone nor Create React App, as originally designed, can solve these problems. As you can see, this isn't about a single missing feature. These features — server-side rendering and static generation, data fetching, bundling, and routing — are interconnected.</p>

<p>Times changed. Now it's getting increasingly difficult to recommend a solution where you are locked into not having these features. Even if you don't use all of them immediately, they should be available for you when you need them. You shouldn't have to migrate to a different template and restructure all of your code to take advantage of them. Similarly, not all data fetching or code splitting needs to be route-based. But it's a good default that should be available to most React apps.</p>
</blockquote>

<p>I've also had conversations with the React team where they directly told me that they have heard many of the external complaints about React apps having bad loading times and overall poor performance. So, the frameworks emphasis is a direct response to that, with the goal of getting more apps to have decent performance by default.</p>

<p>Based on that, we can summarize the React team's stance as:</p>

<ul>
<li>Frameworks have built-in approaches for data fetching, routing, and server rendering, that are designed to work together</li>
<li>Those are all provided out of the box, so you don't have to spend time picking and choosing pieces (that may not work well together)</li>
<li>Frameworks lead to better performance by default, due to build setups and better data fetching patterns</li>
<li>Additionally, React Server Components <em>require</em> integration into a framework to work properly</li>
<li>Those concerns are critical to how the React team feels React <em>should</em> be used today</li>
</ul>

<p>In other words, it's a combination of an ideological stance, a belief that &quot;this will save you time and effort&quot;, and also a belief that &quot;most React apps follow similar patterns and need similar solutions&quot;.</p>

<h4 id="frameworks-ssr-and-spas">Frameworks, SSR, and SPAs</h4>

<p>Also, note the specific mention of &quot;server rendering&quot;. In general, both the React team and other key members of the ecosystem (such as Ryan Florence and Michael Jackson of Remix / React Router) have put heavy emphasis on the need to do server rendering to avoid &quot;waterfalls&quot; of data fetching on the client (such as <code>&lt;List&gt;</code> fetching a set of items, rendering its children, <code>&lt;ListItem&gt;</code> doing its own fetch after mount, etc ). Frameworks like Next and Remix have been specifically designed to support server rendering out of the box.</p>

<p>The justifications for SSR around &quot;faster initial page loads&quot;, &quot;less JS on the client&quot;, and &quot;avoiding waterfalls&quot; all make reasonable sense. I also agree that client-side SPAs have been used in a lot of places they probably shouldn't have been (same as with Redux, really), and that it can make sense to start with a framework even if you don't need <em>all</em> the functionality right away, so that you can take advantage of those features when you decide you need them.</p>

<p>I'll note that Next and Remix <em>do</em> have <a href="https://nextjs.org/docs/pages/building-your-application/deploying/static-exports">&quot;SPA / export&quot; modes</a> that just output static JS/HTML assets, so it <em>is</em> possible to use them to create a purely client-side app with no Node server process needed. However, those are not the defaults, and I would assume most of the community is unaware that is even an option.</p>

<h4 id="framework-push-lacks-nuance">Framework Push Lacks Nuance</h4>

<p>Given all that: I <em>understand</em> why the React team has decided to recommend frameworks as a default. I think it's a reasonable opinion, and valid intentions to improve the average React app.</p>

<p>But I also feel that <strong>the &quot;recommendation&quot; has turned into an overly-broad prescription that doesn't give enough credit to the variety of ways React is used in practice throughout the ecosystem</strong>.</p>

<p>There's many good reasons to use a full-stack React framework, but also plenty of reasons <em>not</em> to:</p>

<ul>
<li>Frameworks add many additional features and functionality, but that's also added complexity to learn, making them less suitable for beginners that are just trying to get a handle on how to use React at all.</li>
<li>The added complexity can also be a trap that leads to confusion, such as accidentally using Context or hooks in Server Components (which throws errors)</li>
<li>Many companies may not be running JS backends, and may even have rules and restrictions against that</li>
<li>Frameworks with server functionality do require specific hosting to run, whereas a pure SPA can be trivially hosted anywhere that serves static HTML and JS (including Github Pages and Amazon S3)</li>
<li>While the <em>need</em> to pick and choose your libraries has often been a source of frustration for React users, it does enable customizing projects to meet your specific needs. Opinionated frameworks remove the need to make most of those decisions, but can also limit your ability to customize behavior later.</li>
<li>The emphasis on &quot;server rendering&quot; clearly helps <em>some</em> kinds of apps, but not all - there are plenty of apps that only need to live on the client side.</li>
</ul>

<h4 id="docs-recommendations-matter">Docs Recommendations Matter</h4>

<p>The React team has said that &quot;the docs are aimed at beginners&quot;, so they want to keep the list of recommended tools and options fairly simple to avoid confusion. This is a very reasonable stance.</p>

<p>They've <em>also</em> said that &quot;anyone who's experienced enough to know to use Vite doesn't need to see it listed in the docs anyway&quot; (paraphrased). That's <em>technically</em> true.</p>

<p>However, it's not just beginners that read the docs, and what the docs recommend does have an influence as a stamp of official approval. That's a large part of why the React team had historically avoided recommending specific libraries or techniques.</p>

<p>If we refer back to the framework / build tool usage stats, today Vite React and CRA usage outweighs Next, and it's clear that SPA usage is still at <em>least</em> half of the React ecosystem. The docs recommendations ought to reflect that usage.</p>

<h4 id="dismissal-of-the-ecosystem">Dismissal of the Ecosystem</h4>

<p>When the new React docs came out, the only mention of non-framework options was an expandable details section labeled <a href="https://web.archive.org/web/20230318003653/https://react.dev/learn/start-a-new-react-project#can-i-use-react-without-a-framework">&quot;Can I Use React Without A Framework?&quot;</a>, with several paragraphs saying &quot;yes, but we don't think it's a good idea&quot;.</p>

<p>And buried at the end of that section was this statement:</p>

<blockquote>
<p>If you’re still not convinced, or your app has unusual constraints not served well by these frameworks and you’d like to roll your own custom setup, we can’t stop you—go for it! Grab react and react-dom from npm, set up your custom build process with a bundler like Vite or Parcel, and add other tools as you need them for routing, static generation or server-side rendering, and more.</p>
</blockquote>

<p>So, not only did the new setup page <em>not</em> list Create React App, but the closest equivalent tool (Vite) wasn't even listed as a meaningful option in the outer section of the page. Instead, it was buried as a mere mention at the bottom of this expandable explanation.</p>

<p>I'd also say that the phrase &quot;unusual constraints&quot; is very poor here. SPAs had been the standard architecture in the React community since the beginning. CRA and Vite are commonly used. How is building an SPA suddenly an &quot;unusual constraint&quot;? There are <em>many</em> reasons to want an SPA, from architectural to business reasons to simplicity of learning. Those aren't &quot;unusual&quot; - those are all common use cases.</p>

<p>And beyond that... note the phrase &quot;<strong>we can't stop you</strong>&quot;. That phrase stuck out to many people as poor phrasing that came across as dismissive of the community, and an indication that the React team was relegating SPAs as an unsupported approach, overnight.</p>

<p>As an example of this, here's a quote from a debate about the &quot;frameworks&quot; emphasis in the docs from mid-2023:</p>

<blockquote>
<p>In some ways React is having its AngularJS moment. Teams are using this time of instability and uncertainty to shop around for alternatives. We certainly are.<br />
React is great. It's the strong server &amp; framework alignment tone change that's concerning to communities. The server-neutral aspects that made it what it is today suddenly feel second-class. (SPA routers &amp; loaders are a mess &amp; underserved!)<br />
It's not about React or Vite. It's the ecosystem. It's painful to realize that React won't encourage the traditional &quot;non-framework&quot; as strongly as the &quot;new ways&quot;. The &quot;React without a framework&quot; section is tucked away in the docs and depressing.<br />
As a non-Node backend company we see those docs as a sign that we don't align with React's primary direction anymore. Framework endorsements are a big enough change to cause teams to reevaluate entire stacks. React is great, but its influence has limits on architecture.
It's not &quot;wrong&quot; for React to go this direction. But we can't pretend that non-Framework React usage is now a second-class concern. How long until it's not a viable option? It's uncomfortable. So, we look for safer bets. What would you recommend a non-node backend company do?<br />
<a href="https://x.com/vyrotek/status/1649097699696992256">https://x.com/vyrotek/status/1649097699696992256</a></p>
</blockquote>

<h4 id="fixing-the-docs-recommendations">Fixing the Docs Recommendations</h4>

<p>When the React team finally <a href="https://react.dev/blog/2025/02/14/sunsetting-create-react-app">announced CRA as deprecated in early 2025</a> (after I helped push them to fix it and make that deprecation official), the <a href="https://github.com/reactjs/react.dev/pull/7495">initial docs update</a> included a new &quot;Building Your Own Framework&quot; page. The concept was that picking your own router and data fetching approach was equivalent to cobbling together a bespoke framework that wouldn't be as good as a &quot;real&quot; framework.</p>

<p>I understand the mental model here, but this is also rather dismissive of both the way the ecosystem had been building apps, and of people's ability to choose their own options.</p>

<p>As an example, Vite creator <a href="https://x.com/youyuxi/status/1892000761778929931">Evan You posted his take</a>:</p>

<blockquote>
<p>it feels the React team's hesitance on Vite (and build tooling in general) is how it aligns with their vision of React (i.e. RSC being the recommended paradigm), and how much influence / connection they have with the said tools to make sure the integration works as they designed and can adapt to design iterations.
...<br />
I apologize if this is not what the React team is thinking, but it’s my honest guess because I am just as puzzled as many React users by what took it so long for Vite to be better acknowledged as a recommended tool.</p>
</blockquote>

<p>I ended up <a href="https://github.com/reactjs/react.dev/pull/7618">filing a draft PR to revamp the setup pages</a> to improve the tone, add nuance in recommending project setup tools, and offer some architectural guidance on choosing approaches. That PR got closed, but the React team did cherry-pick some of the ideas and phrasing over into a new PR.</p>

<p>Ultimately, they ended up with a <a href="https://web.archive.org/web/20250526084038/https://react.dev/learn/build-a-react-app-from-scratch">&quot;Building a React App from Scratch&quot; setup page</a> that is fairly reasonable. It recognizes SPAs and picking your own tools as a valid approach, lists Vite / Parcel / RSPack as suggested build tools, points to some routers and data fetching libraries, and provides some actual useful guidance to users trying to set up a project.</p>

<p>It's unfortunate that it took us multiple years to get the docs to that point :( Much of the confusion and angst could have been avoided if the React team had applied some of the community-recommended phrasing changes soon after the new docs were released.</p>

<h3 id="concern-server-component-docs-and-explanations">Concern: Server Component Docs and Explanations</h3>

<p>One of the big pain points and sources of confusion around React Server Components is that official docs and info has been scattered and unfortunately lacking.</p>

<p>The React team <a href="https://react.dev/blog/2020/12/21/data-fetching-with-react-server-components">originally announced RSCs with an explanation video in Dec 2020</a>, and that was followed by <a href="https://github.com/reactjs/rfcs/blob/main/text/0188-server-components.md">a lengthy and detailed RFC doc explaining RSCs</a>. These did do a decent job of explaining the background and primary motivations.</p>

<p>However, the development process of RSCs, combined with the fact that it's up to frameworks to implement design choices, meant that the actual React docs have never meaningfully documented RSCs.</p>

<p>It took almost 2 years for <a href="https://nextjs.org/blog/next-13">Next 13.0</a> to come out with the first official beta release of RSCs in the form of the new App Router, and another 6 months until <a href="https://nextjs.org/blog/next-13-4">Next 13.4 officially declared the App Router as &quot;stable&quot; and ready for production</a> in May 2023. Vercel and Next have a small but very active devrel team, and by the time of Next 13.4's release, <a href="https://web.archive.org/web/20230502235021/https://beta.nextjs.org/docs">they had done a sizeable rewrite of the Next docs to cover the then-new App Router, available as &quot;beta&quot; docs</a>. That included some docs pages that talked about using RSCs, <a href="https://web.archive.org/web/20230422084216/https://beta.nextjs.org/docs/data-fetching/fundamentals">under the &quot;Data Fetching&quot; category</a>, as well as later detailed blog posts like <a href="https://vercel.com/blog/understanding-react-server-components">Understanding React Server Components</a>. These were excellent resources, with very helpful explanations of architecture and concepts.</p>

<p>And yet, even though the RSC functionality was part of React itself, <strong>the React docs didn't have <em>any</em> information on RSCs</strong>. Not &quot;What Are RSCs&quot;, not &quot;How Do I Use an RSC&quot;, and <em>definitely</em> not &quot;How Do I Integrate My Library With RSCs&quot;. Vercel's team did a good job documenting their actual product and some of the overlap with React, but it was extremely confusing to people why there was no info or explanations about RSCs in the actual React docs themselves (which, timeline-wise, had just officially launched a couple months earlier).</p>

<p>There's been lots of discussion from individual React team members on social media, responding to questions, arguing in favor of RSCs as a concept, and trying to flesh out sales pitches for RSCs. But as of today, the only official core docs page on RSCs is <a href="https://react.dev/reference/rsc/server-components">API Reference: Server Components</a>. This page is, honestly, confusing and not particularly helpful. It's definitely not an &quot;API reference&quot; content-wise, and the content doesn't have any real context introducing RSCs or explaining when and how to use them - it's a grab bag of random topics.</p>

<p>There <em>have</em> been a number of excellent external blog posts explaining various aspects of RSCs:</p>

<ul>
<li>Dan Abramov has written <a href="https://overreacted.io">numerous fantastic posts explaining the mental model of RSCs and the problems they solve</a>.</li>
<li>Vercel published a great <a href="https://vercel.com/blog/understanding-react-server-components">&quot;Understanding React Server Components&quot;</a> intro blog post</li>
<li>Daniel Saewitz wrote <a href="https://saewitz.com/server-components-give-you-optionality">Server Components Give You Optionality</a> explaining how they're an addition to your toolbox</li>
</ul>

<p>This is the kind of information that <em>should</em> be in the React core docs - explanations of RSC concepts and why you might want to use them, independent of how any specific framework implemented RSCs.</p>

<p>Related to this: the community has taken away the idea that &quot;RSCs are the future of React&quot;, and that &quot;the React team <em>wants</em> us to use RSCs all the time everywhere&quot;. In reality, I've seen React team members explicitly say on social media that &quot;RSCs are optional, we just want people to understand them properly&quot;. Given that confusion, it seems like making that point specifically in the docs is important.</p>

<p>Personally, I'd like to see an entire section on RSCs added to the React core docs, with pages like:</p>

<ul>
<li>&quot;Intro to RSCs&quot;</li>
<li>Mental model</li>
<li>Use cases / when to choose RSCs</li>
<li>Technical data flow / architecture</li>
<li>Adoption / migration</li>
<li>FAQ</li>
<li>Framework implementor's guide</li>
</ul>

<p>Having those docs pages would not make all the questions go away. Lots of people don't even read the docs in the first place :) But having those topics covered officially <em>would</em> make it visible, and it would act as a resource that could be used to answer these questions whenever they come up on social media.</p>

<h2 id="takeaways-from-the-concerns">Takeaways from the Concerns</h2>

<p>I don't think it's the React team's job to spend all their time dispelling FUD on the internet. Lots of people will have opinions, many of them will be differing or wrong.</p>

<p>That said, it's striking that there's a strongly consistent theme of &quot;all of this emphasis on frameworks and servers is being forced on us to make Vercel money&quot;. It's wrong, but there's enough circumstantial evidence to lead people to that belief, and the React team's actions and statements have to some extent reinforced that belief instead of disproving it. Unfortunately, at this point it seems to be a meme that is permanently embedded in the community, and I don't think we're going to make it go away.</p>

<p>It's also genuinely concerning that users are worried or assuming potential problems with how React <em>might</em> change or stop working in the future, especially when those concerns are clearly wrong and easily disprovable. You can continue to use React exactly as you always have, and all of the RSC / server functionality is entirely additive and optional.</p>

<p>The internet being what it is, even a blog post on the actual React blog that explicitly refuted those statements wouldn't change a lot of people's minds. But it does feel like <em>maybe</em> some of the worst of that could have been avoided with better developer relations work from the React org - more time spent reading the concerns, acknowledging that they exist and understanding where they're coming from, and trying clarify and answer them.</p>

<p>I do feel that the push for &quot;frameworks&quot; has been genuinely well intentioned, but also too broad and ultimately dismissive of the variety of usage patterns in the ecosystem. Yes, it's hard to write docs and provide recommendations that offer nuance, and it's understandable to try to keep things simple to target beginners and nudge the ecosystem in a better direction... but part of being a maintainer is recognizing and supporting the variety of ways your tools are used by the community.</p>

<p>We <em>did</em> finally end up with a reasonable set of React project setup docs that have useful instructions on setting up a project yourself and recognize that as a valid approach. It's unfortunate that it took us years to get to that point, and that the React team essentially ignored the very vocal feedback from the community on how to improve that section of the docs. The docs would still really benefit from more advice on how to approach choosing an appropriate tool and architecture for your app.</p>

<p>Similarly, the lack of official core docs info on RSC concepts and tradeoffs has contributed to the confusion. I strongly feel that covering those topics would be a huge improvement in people's understanding of RSCs and the resulting discourse.</p>

<h2 id="final-thoughts">Final Thoughts</h2>

<p>This hopefully answers a lot of questions about how and why React has developed the way it has, what the influences are on React's development process, the main goals of the React team, and where React usage patterns stand today.</p>

<p>I also hope I've been able to dispel some of the confusion and FUD around the React team's motivations and reasons for pushing in specific directions. It's fine if people disagree with the technical directions, or decide that they don't need React Server Components or to migrate to a larger framework. But the React team's intentions are valid and genuine here.</p>

<p>It's really hard to maintain widely-used libraries and satisfy the variety of needs and usage patterns in the community. I do think the React team has done a good job overall. Unfortunately, the places where the communications have been poor and the issues with the docs have been a big contributing factor to a lot of the frustration and angst in the community.</p>

<p>Going forward, I'm hopeful that we can find ways to improve that communication, and maybe even get more of the community involved in improving the docs.</p>
