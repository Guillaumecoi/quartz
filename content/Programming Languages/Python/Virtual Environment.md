## Why use a Virtual Environment
---
- **Project Isolation:** They allow you to create separate environments for each project, preventing conflicts between dependencies that have different version requirements.
- **Cleanliness:** They keep your global Python installation clean by installing project-specific packages within the virtual environment.

## Set-up a Virtual Environment in Python
---
### Create the Environment 
- **Linux/macOS:** `python3 -m venv <environment_name>` 
* **Windows:** `python -m venv <environment_name>` 
* _Note: `venv` is a common name, but you can choose anything.

### Activate the Environment
* **Linux/macOS:** `source <environment_name>/bin/activate` 
* **Windows:** `<environment_name>\Scripts\activate.bat`

- **Automatically activate the environment in VS Code**
	- Press: `Ctrl+Shift+p`
	- Search for `Python: Select Interpreter`
	- Select your virtual environment

## Virtual Environment in Git
---
### Add it to your .gitignore
``` 
# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/
```
Make sure your `<environement_name>` is in here

### **Managing Requirements**
- **Install Packages:** Use `pip` to install any packages you need
	```shell
pip install <package_name>
```

- **List all installed packages:** This way you can upload this list as `requirements.txt` to the git which is way less overhead than uploading the virtual environment entirely. 
  ``` shell
pip freeze > requirements.txt
```

- **Install packages from `requirements.txt`**
  ``` shell
pip install -r requirements.txt
```