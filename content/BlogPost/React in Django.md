All the code and the is available [here](https://github.com/Guillaumecoi/Blog_Django_React).
## Introduction
---
I'm diving into integrating the React framework with [[Django]].
### Current skill level
While I know my way around Django well and have experience utilizing HTML, CSS, and JavaScript within that framework, I am new to the realm of React and other JavaScript frameworks.
### Motivation
I am tired of wrestling with vanilla JavaScript and HTML for dynamic pages in Django. Setting it up and keeping things organized is a major headache. On top of that, I've been wanting to delve into front-end development for a while now. Ultimately, React's popularity and the ease of finding learning materials for combining it with Django made it my preferred choice.

## Set-up
---
### React within Django
Firstly, I've [[Setting up React within Django|set up React within my Django project]]. What I like about this setup is its live update feature. When `npm run dev` is active, saving a React file triggers an automatic update to `main.js`, which in turn, updates the Django server as long as it's running. Another advantage is the integration convenience: if `main.js` is set correctly and you're not modifying React files, you can manage the project just like any other Django project. 
#### Managing URL Routing
I've implemented a basic [[Software Development/Django/React/Setup/Routing URL's|routing system to render multiple pages]]. The current setup requires setting the path in two places. Which could become tedious with a large number of URLs. Here are a few initial solutions I considered:

- **Decoupling Frontend and Backend:** Separating React and Django into distinct servers.
- **Automation:** A script to synchronize URL definitions.
- **Dynamic Content:** Dynamically loading page content to reduce URL dependency.

### React and Django as separate servers
You can also create an [[Setting up React and Django as separate servers.|independent React server which communicates with Django]] via an API. Now, everything frontend-related is managed by React, SEO, the icon, title, etc.

### Conclusion
From here on out, both approaches work quite similarly, communicating with Django via the API.

#### React within Django
- Interesting for smaller projects that need more than vanilla HTML/JavaScript.
- Only one server needs to be deployed and maintained.
- You retain the rendering capabilities of Django.
- Managing routing is more complicated with many URLs.

#### React and Django as separate servers
- Clear separation between frontend and backend.
- These two servers can scale independently.
- React and Django developers can work in their preferred environments.

## Using Django API in React
----
The first thing i wanted to set up is authentication. 
