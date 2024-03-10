- Create a new project directory. 
- [[Create a React Project|Create your React frontend]]. 
- [[Setting up Django|Create your Django project]] in the same folder.

### Running the servers
- Run `npm start` in the react folder.
	- This will open your project in a web browser, usually at http://localhost:3000
- Run `python manage.py runserver`
	- You typically can access the server at http://localhost:8000

To let these two communicate you have to use Django's RESTful API in React.