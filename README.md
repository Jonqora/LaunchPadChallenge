# 🚀 UBC Launch Pad - Technical Challenge (2022)
My technical challenge submission for Fall 2022 application to UBC Launch Pad.

## Submission Instructions
> Please complete one of the tasks below and upload your solution outlining to GitHub. Your solution should include a written component, and optionally, a small code example (you do not need to implement anything extensive). Make sure the GitHub repository you intend to submit is public. When you're done, please submit the link to your project using [this Google form](https://forms.gle/asBhJtnGEGtWFggG6).

## Prompt
> ### Frontend Web 👩‍💻
> You and your friends are developing a new start-up called DRUBER, a drone-based ride share application that carries you to your destination. The original specification was to develop a web page that works in 1920x1080 however your company has realized that it is missing an entire market of smartphone users. Describe how you can modify your code to work in smartphone resolutions e.g. 750x1334 (iPhone 8). Please give specific examples where possible, but do not implement an entire DRUBER clone!

## Answer
I will start by providing context of my background knowledge for this prompt, then will discuss different decision areas that could be considered when planning and implementing changes to optimize the DRUBER 🛸 website for smartphone use.

### My background
The knowledge I have on adapting code for small screens comes from two main sources. My answers are informed by these expleriences and general knowledge.
- **Building [my personal website](https://ellenlloyd.ca/) to be fully responsive.** This is a simple, static site in vanilla HTML/CSS/JavaScript, but I really wanted it to look clean and organized on all devices. In my quest to do this I learned a lot about Flexbox, media queries, and rule hierarchies in CSS.
- **Interning on an enterprise SAAS web app with limited to no mobile accessibility.** We just don't have it! At work, we are saddled with a 20-year-old code base having a lot of technical debt; the extent of changes needed to provide a mobile experience just hasn't been overcome. Here I gained a better understanding of barriers and challenges that can stand in the way of modifying websites for good mobile design. 

I tend to be a big-picture sort of thinker, and although I'm a Developer applicant my response here trends more into Design territory—I hope that's okay. 😊 I like to work closely with design thinking when I code.

### 🛸 Decisions: Refining the Problem
- We have an original spec (1920x1080) and a new spec to meet (750x1334 and similar). But why stop there? *Should* we stop there? Two main paradigms for mobile-friendly sites are adaptive web design (AWD) and responsive web design (RWD). Choosing a responsive approach could give seamless elegance across all screen sizes. 👀
  - For **adaptive**, we would define a fixed number of different layouts meant for different screen widths, and we design each layout. For our DRUBER 🛸 app, this would mean designing two different fixed-width page layouts and using media queries to determine which one to display.
  - For **responsive**, we would design fluid changes (for example, column widths changing continuously with window size and page elements rearranging themselves into fewer columns when small). There are neat tools like Flexbox, Flexgrid (and frameworks like Bootstrap) that can help us realize a fully responsive design. Responsive design is beautiful when done well (I'm partial to it)... but here's the catch: it also takes a lot longer _to_ do well. Since my friends and I at DRUBER 🛸 are running a startup, maybe we should focus on a quick MVP for now and choose a slim, 2-design AWD approach to help capture more mobile market share ASAP. 😎
- Media queries are useful in both cases, since Flexbox/grid alone has limits if we want to make bigger changes to layout at certain cutoff points. As an example, this media query could contain CSS rules that are conditional on a wider, larger-than-smartphone display: 

    ```@media only screen and (min-width: 768px)```

- Another decision to keep in mind (though perhaps outside scope of this prompt) is whether we really want to rely on a mobile _web_ app. Should we instead go whole hog and build a separate native app for mobile? This may be complex, but there could be ways to construct a common backend for our DRUBER 🛸 service that serves two completely different frontend implementations on web and on mobile.

### 🛸 Decisions: UX Discovery and Analysis
To design a great mobile experience we should put the user first. Here are some questions to be asking:
- How are people using our app on mobile already, if any are? How might they be likely to use it or want to use it if we implemented a mobile-friendly design?
- What page elements and information are high priority for our users on the go? With limited screen space and constrained ease of navigation on mobile, it is essential to put our most-used elements front and center. In our case, how about a way to request a DRUBER 🛸 drone ride? Or a way to sign up with an account? 
- How can we reduce friction for the mobile UX experience? One way is to minimize typing input if we can, which is clunky on mobile. Can we offer text field hints from data-driven suggestions? Can we accept non-text input such as choosing a ride pickup location by tapping on a map?
- Simplicity is golden for smaller mobile screens. Are there pages or page elements we can hide inside menus? Or elements that we can remove completely on our mobile site? (maybe we don't need to thank *all* our venture capital investors on the mobile site...)
- How different of design and interface are we thinking to achieve on desktop versus mobile? Are there any page elements or data that will work similarly under the surface for both even though the UI on mobile and desktop may need to look very different?

### 🛸 Decisions: Code Modularity and Refactoring
In parallel with our exploration and decision process for the above areas, my DRUBER 🛸 friends and I should\ examine our existing codebase and readiness to refactor things to have two separate site versions as needed.
- When I made my static, vanilla personal webpage, making sure my data was separated from design was as simple as writing semantic, well-organized HTML and having all styling and page layout organized using style sheets. BUT...
- For a complex webapp built on backend services like I imagine DRUBER 🛸 might be, it becomes **really** essential that we separate our data model (and operations on it) enough from the views of that model that are rendered on a webpage and presented to the user. Then we can alter and have multiple views of the same information while keeping DRY backend code that is easier to maintain down the road.
- Advanced performance considerations: informed by the UX analysis, do any of our existing services perform costly computations that we won't need to see on mobile? Example: maybe DRUBER 🛸 homepage on a desktop browser shows a real-time, dynamic map of all drones in your neigbourhood for cool visual impact. And mayyyybe the UX designers on our team recommend to us that we don't *really* need to show the location of so many drones on mobile app because there is limited screen space. Or maybe, UX insight suggests we should do away with the real-time all-drones map on mobile completely. In such cases, we'd want to make sure our backend service that fetches/updates all nearby drone locations is run on-demand, or with limits that can be scaled according to the browser environment. This can help us have better performance and page load times for users by not querying locations for hundreds of neighborhood drones that are off-screen to a mobile user.

### Summary
If I were to help plan a new and high-quality mobile web experience for a complex web app, I would raise these topics for discussion: 1) adaptive vs responsive approaches, 2) user-centered UX design, and 3) code modularity on both front and back end. As a final thought, I'll also note: if my friends and I had built the DRUBER 🛸 app using a particular web framework(s), the specific frameworks that we used will likely influence and inform our final implementation of changes to realize a mobile-friendly site view. 
