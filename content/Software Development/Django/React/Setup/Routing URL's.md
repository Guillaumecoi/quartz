After [[Setting up React within Django|setting up React in Django]] , let's enable navigation to multiple pages. We'll create "home", "blog", and "contact" pages and set up routes to them.

**Code:** All code can be found [here](https://github.com/Guillaumecoi/Blog_Django_React/tree/main/2_Routing_Url).

## Setup your Routing
---
Follow the steps [[Software Development/React/Routing URL's|here]] to setup the routing within React.

### Include the new paths in Django
---
Update your `urls.py` in the `frontend` folder like this:
```python
from django.urls import path
from django.views.generic import RedirectView
from .views import index

urlpatterns = [
    path("", RedirectView.as_view(url='home/')),
    path("home/", index),
    path("contact/", index),
    path("blog/", index),
]
```

##### Notice:
- `index` renders all the pages from Django's perspective.
- The empty path (`""`) redirects to "home/" in Django to avoid a 404 error.
	- An other solution is replacing `"home/"` with `""` in both Django and React.


### Testing the code
---
If everything went well `http://127.0.0.1:8000/` + the correct paths should now render correctly. Displaying each their content.

### Troubleshoot
---
Firstly make sure there are no **typo's** in the paths!

- **404 Page not found:** 
	- Make sure your `urls.py` files are set up correctly in Django
- **Blank page**:
	- Make sure the path is correctly set in `RoutesComponent.js`
	- Make sure your component renders correctly

