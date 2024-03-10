## Why
---
- **Avoiding URL Name Conflicts:** When multiple Django apps within your project might have views with the same name (e.g., 'index', 'detail'), namespaces prevent collisions.
- **Reusability:** Namespaces make it easier to reuse apps in different projects without worrying about URL pattern clashes.
## How
---
Let's assume you have a blog app named 'blog'.
- In your `blog/urls.py`:
```python
from django.urls import path
from . import views

app_name = 'blog'  # Define the app namespace

urlpatterns = [
    path('', views.post_list, name='post_list'),
    # ... other URL patterns for your blog app
]
```
- In your main `urls.py`:
```python
path('blog/', include(('blog.urls', 'my_app'), namespace='blog')), 
```

**Usage**:
```python
from django.urls import reverse 
blog_list_url = reverse('blog:post_list')
```

```HTML
<a href="{% url 'blog:post_list' %}">Blog posts</a>
```