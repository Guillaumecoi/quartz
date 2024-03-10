**Code:** All code can be found [here](https://github.com/Guillaumecoi/Blog_Django_React/tree/main/1_Setting_Up).
## Prerequisites
---
Before beginning, ensure you have:

- [[Setting up Django|An existing Django project]]
- Node.js and npm installed on your system

## Initializing the setup
---
 ### **Creating a Django App Called `frontend`**
- Navigate to your Django project directory (Note: This can be located in any folder).
- Generate a new app using the command below in your terminal:
``` Shell
django-admin startapp frontend
```

- Add `frontend` to `INSTALLED_APPS` in `settings.py`
```python
INSTALLED_APPS = [
	'django.contrib.admin',
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.messages',
	'django.contrib.staticfiles',
	'frontend',
]
```

### **Create the Required Folders and Files**
* Navigate to the new `frontend` directory.
* A `src` folder containing:
	* A `components` folder, which includes:
		- A file named `App.js`:
	  ```js
		import React from "react";
		import { createRoot } from 'react-dom/client';
		
		const App = () => {
			return (
			  <h2> Hello World </h2>
			);
		};
		
		const appDiv = document.getElementById("app");
		createRoot(appDiv).render(<App />);
		```
	- A file named `index.js` that imports `App.js`: (in `src`)
  ``` js
	import App from './components/App';
	```

* A `static` folder with subfolders:
	- `frontend`
	- `css`
	- `images`
- A `templates` folder containing:
	- A `frontend` folder, which includes:
		- An `index.html` file:
	``` html
	<!DOCTYPE html>
	<html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>PlanPulse</title>
		{% load static %}
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
		<link rel="stylesheet" type="text/css" href="{% static "css/index.css" %}" />
	</head>
	<body>
		<div id="main">
			<div id="app"></div>
		</div>
		
		<script src="{% static "frontend/main.js" %}"></script>
	</body>
	</html>
	```

### React setup
* Ensure you are in the app folder.
- Initialize the project with `npm`:
``` Shell
npm init -y
```
* Install the necessary packages:
``` Shell
npm i webpack webpack-cli --save-dev 
npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
npm i react react-dom --save-dev 
npm install @babel/plugin-proposal-class-properties 
npm install react-router-dom    
```

#### **Configuring Build Tools**
* `babel.config.json` containing:
```json
{
	"presets": [
	  [
		"@babel/preset-env",
		{
		  "targets": {
			"node": "20"  // Make sure this is the same as your node version
		  }
		}
	  ],
	  "@babel/preset-react"
	],
	"plugins": ["@babel/plugin-proposal-class-properties"]
  }
```

* `webpack.config.js` containing:
``` js
const path = require("path");
const webpack = require("webpack");

module.exports = {
  entry: "./src/index.js",
  output: {
	path: path.resolve(__dirname, "./static/frontend"),
	filename: "[name].js",
  },
  module: {
	rules: [
	  {
		test: /\.js$/,
		exclude: /node_modules/,
		use: {
		  loader: "babel-loader",
		},
	  },
	],
  },
  optimization: {
	minimize: true,
  },
  plugins: [
	
  ],
};
```

* Update the `scripts` section in `package.json`:
```json
"scripts": {
"dev": "webpack --mode development --watch",
"build": "webpack --mode production"
},	  
```

 ### Setting up Django
* In `views.py`, include the following code:
```python
from django.shortcuts import render

def index(request, *args, **kwargs):
return render(request, 'frontend/index.html')
```
* Create a `urls.py` in the `frontend` app with:
```python
from django.urls import path
from .views import index

urlpatterns = [
path("", index),
]
```
* Add the `frontend.urls` to the project's main `urls.py`:
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
path("admin/", admin.site.urls),
path("", include("frontend.urls")),
]
```

 ## **Running the Project**
* Inside the `frontend` directory, start the webpack process:
```Shell
npm run dev
```
* In the directory containing `manage.py`, launch the Django server:
```Shell
python manage.py runserver
```
* Access your application at http://127.0.0.1:8000/ to see the page.

By following these steps, you will have successfully integrated React with Django, showcasing a simple `"Hello World"` message.