## Prerequisites
---
- [[Setting up Django|Django project]]

## Install Django REST Framework:
---
### Install using pip:
```Bash
pip install djangorestframework 
```

### Configuration
---
**Add to INSTALLED_APPS:**
- Edit your Django project's `settings.py` file.
- Find the INSTALLED_APPS list and add:
```Python
INSTALLED_APPS = [
    # ... other apps
    'rest_framework',
    'rest_framework.authtoken' # For token-based authentication
]
```
