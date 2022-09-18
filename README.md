# 🚀 UBC Launch Pad - Technical Challenge (2022)
My technical challenge submission for Fall 2022 application to UBC Launch Pad.

## Submission Instructions
> Please complete one of the tasks below and upload your solution outlining to GitHub. Your solution should include a written component, and optionally, a small code example (you do not need to implement anything extensive). Make sure the GitHub repository you intend to submit is public. When you're done, please submit the link to your project using [this Google form](https://forms.gle/asBhJtnGEGtWFggG6).

## Prompt
> ### Frontend Web 👩‍💻
> You and your friends are developing a new start-up called DRUBER, a drone-based ride share application that carries you to your destination. The original specification was to develop a web page that works in 1920x1080 however your company has realized that it is missing an entire market of smartphone users. Describe how you can modify your code to work in smartphone resolutions e.g. 750x1334 (iPhone 8). Please give specific examples where possible, but do not implement an entire DRUBER clone!

## Answer
I will start by providing context of my background knowledge for this prompt, then will discuss different decision areas that could be considered when planning and implementing changes to optimie the DRUBER website for smartphone use.

### My background
The knowledge I have on adapting webpages for small screens comes from two main sources. I will draw on both, plus general knowledge.
- **Building [my personal website](https://ellenlloyd.ca/) to be fully responsive.** This is a simple, static site in vanilla HTML/CSS/JS, but I really wanted it to look clean and organized on all devices. In my quest to do this I learned a lot about Flexbox, media queries, and rule hierarchies in CSS.
- **Interning on an enterprise SAAS web app with limited to no mobile accessibility.** We just don't have it! We're standing on a 20-year-old code base with a lot of technical debt, and the extent of changes needed to provide a mobile experience hasn't been overcome yet. Here I gained a better understanding of barriers and challenges that stand in way of modifying websites for good mobile design. 

> ## Ideas
> Give my background and perspective first
> I can talk about my experience of designing my very simple personal webpage to be fully responsive
> I can discuss high-level concepts that will be important to consider no matter what implementation or code stack we're on
> I can give examples from my personal wwebsite
> I can speculate or talk about what may need to be done for an app like DRUBER that is probably on an existing and quite large codebase that likely uses an opinionated framework for implementation

### Refining the Problem
- we want things to work with our initial spec and also a new spec. One big question: do we want to stop there? Two main approaches are adaptive web design (AWD) and responsive web design (RWD). For adaptive, we define a fixed number of different layouts meant for different screen widths, and we design each layout. For responsive, we design fluid changes (for example, text column width changing continuously with window size and then wrapping around when small). There are some really neat tools like Flexbox, Flexgrid (and frameworks like Bootstrap) that can help us realize a fully responsive design. RWD is beautiful when done well... but here's the catch: it also takes a lot longer _to_ do well. Since my friends and I are running a startup, maybe we should focus on a quick MVP for now and choose AWD to capture that mobile market share ASAP. 😎
- Another desision to keep in mind is whether we really want to do a mobile web app. Should we go full mobile app as a download instead? This may be complex, but there could be ways to construct a common backend to our app that serves two completely different front ends on web and on mobile.

### UX Discovery and Analysis
- how are people using our app on mobile AND/OR how might they be likely to use it/want to use it if we implement the mobile-friendly site?
- limited screen space and constrained ease of navigation on mobile means it's essential to put most-used elements and information front and center
- also avoid typing if we can (can we populate text fields with suggestions? give non-text input options e.g. find address on map?)
- simplicity is good... are there pages or page elements we can hide in menus? or remove completely on mobile site? (be cautious with the second one...)
- ...just how different of design and interface are we aiming here, for desktop vs mobile? Are there page elements or data that will work similarly under the surface even though they may need to look different?

### Code Modularity and Refactoring
- we want to examine our existing codebase and readiness to refactor things to have two separate site versions... 
- for my static, vanilla personal webpage, making sure data was separated from design meant ensuring that I wrote semantic, well-organized HTML and that all of my styling and layout was done using style sheets. (Give examples of rules that were different!) For a simple webpage, we can write style rules that depend on the user's data (NOTE: how to obtain user data about mobile vs desktop access and act on it? Talk about this)
- for a complex webapp built on backend services like I imagine of DRUBER, it becomes ESSENTIAL that we have separated our data model (and operations on it) enough from the view of that model that is rendered on the page and presented to the user. Then we can alter and have multiple views while keeping DRY code that is easier to maintain down the road.
- UI versus business logic
- performance considerations: informed by the UX analysis, do any of our existing services perform costly computations that we won't need to see on mobile? Maybe DRUBER homepage on a desktop browser shows a real-time, dynamic map of all drones in your neigborhood for cool visual impact. And well, maybe the UX designers recommend to us that we don't really need to show the location of so many drones on mobile app because of limited screen space... or maybe do away with the real-time all-drones map on mobile completely. In this case, we'd want to make sure our backend service that fetches all nearby drone locations is run on-demand, or with limits that can be scaled according to the browswer environment. This can make sure we have better performance and page load times for users by not querying locations for hundreds of neighborhood drones that are off-screen to a mobile user.

### Implementation Thoughts


### Summary
If I were to help plan a new and high-quality mobile web experience for a complex web app, I would raise these topics: 1) adaptive vs responsive approach, 2) user-centered UX design, and 3) code modularity on both front and back end. Aid one final note: if my friends and I have built our DRUBER startup web app using any particular web frameworks (I'd sure hope so!), the specific frameworks we already chose will likely influence and inform our final implementation of changes to realize a mobile-friendly site view. 

