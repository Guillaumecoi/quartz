## Why
---
- **Organization:** Creating a separate `urls.py` for each app keeps your project structured. It avoids a single, giant `urls.py` for the entire project.
- **Modularity:** Apps become self-contained units of functionality. This makes them reusable.
- **Prefixing:** By including app URLs with a prefix (e.g., `'app/'`), you neatly organize URL patterns and help prevent future naming conflicts.

## How
---
- Create an `urls.py` file in your app directory.
- In the main project's `urls.py`, include the URLs from your app:	
```python
from django.urls import include, path

urlpatterns = [
	# ... other URL patterns
	path('app/', include('<app_name>.urls')), 
]
```

### Additional options
---
-[[Namespaces]]