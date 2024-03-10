## Django Project
---
### Create the project
- Create a [[Virtual Environment|virtual environment]] (optional but recommended) 
- Install Django: `pip install Django`
- Create the project: `django-admin startproject <project_name>`

### Project Structure
- `<project_name>/`: Your main project directory.
	- `<project_name>/__init__.py`: Lets Python know this is a package.
	- `<project_name>/settings.py`: Project-wide configuration settings.
	- `<project_name>/urls.py`: Where URL patterns are defined.
	- `<project_name>/wsgi.py`: Entry point for WSGI-compatible web servers.
- `manage.py`: A command-line utility for project management.

## Django Apps
---
 A Django app is a self-contained component within your project that handles a specific set of features. For example, a blog, an e-commerce store, or an authentication system could each be separate apps.

#### Create an App
- Run `django-admin startapp <app_name>`
#### Add Apps to `INSTALLED_APPS`
- Open your project's `settings.py` file.
- Locate the `INSTALLED_APPS` list and add your newly created apps:	
```python
INSTALLED_APPS = [
	# ... other apps
	'<app_name>',
 ]
```

### Additional options
---
 - [[Include your Apps URL]]