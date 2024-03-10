### Create the Pages
---
**Folder Structure:** Create `home.js`, `blog.js`, and `contact.js` inside of the `components` folder. Optionally, place them in a new `pages` folder within the `components` folder. Structure your project as you prefer.

- `home.js`
  ```js
import React from "react";

const HomePage = (props) => {
    return (<h1>This is the Homepage</h1>);
}

export default HomePage;
```

- `blog.js`
  ```js
import React from "react";

const BlogPage = (props) => {
    return (<h1>This is the BlogPage</h1>);
}

export default BlogPage;
```

- `contact.js`
  ```js
import React from "react";

const ContactPage = (props) => {
    return (<h1>This is the ContactPage</h1>);
}

export default ContactPage;
```

### Create the `RoutesComponent.js`
---
`RoutesComponent.js` manages the mapping between URLs and the components to display. 

```js
import React from "react";
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import HomePage from './pages/home';
import BlogPage from './pages/blog';
import ContactPage from './pages/contact';

const RoutesComponent = () => {
    return (
        <Router>
            <Routes>
                <Route path="/home" element={<HomePage />} />
                <Route path="/blog" element={<BlogPage />} />
                <Route path="/contact" element={<ContactPage />} />
            </Routes>
        </Router>
    );
};

export default RoutesComponent;
```
##### Explanation of components:
- **Router:** Manages the mapping between the URL paths in your application and specific React components to display.
- **Routes:** A container for individual `Route` components.
- **Route:** A single configuration that defines the association between a URL path and a React component.
    - `path`: The URL pattern to match. For example, `/home` will match the URL `http://127.0.0.1:8000/home`
    - `element`: The React component to load when the `path` matches the current URL.

#### Placing `RoutesComponent.js` in `App.js`
- `App.js`
```js
import React from "react";
import { createRoot } from 'react-dom/client';
import RoutesComponent from './RoutesComponent';

const App = () => {
	return (
		<div>
			<RoutesComponent />
		</div>
	);
};

const appDiv = document.getElementById("app");
createRoot(appDiv).render(<App />);
```
