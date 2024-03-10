The code for this can be found [here](https://github.com/Guillaumecoi/Blog_Django/tree/main/SessionBased_Authentication_api/djangoserver).
## Prerequisites
---
- [[Setting up Django|Django project]]
- [[Installing Django's rest_framework|Django's rest framework]]

## Setup
---
### Create an app Users in Django
- Run `django-admin startapp users`
- [[Include your Apps URL]]

### `serializers.py` Set-up
---
- Create `serializers.py` in the users folder
```python
from rest_framework import serializers
from django.contrib.auth import get_user_model, authenticate

UserModel = get_user_model()

class UserRegisterSerializer(serializers.ModelSerializer):
    email = serializers.EmailField()
    password = serializers.CharField(write_only=True)

    class Meta:
        model = UserModel
        fields = ["email", "password"] 
    
    def create(self, validated_data):
        if 'email' not in validated_data:
            raise serializers.ValidationError("The email field is required.")
        validated_data['username'] = validated_data['email']
        user = UserModel.objects.create_user(**validated_data)
        return user
    

class UserLoginSerializer(serializers.Serializer):
    email = serializers.EmailField()
    password = serializers.CharField(write_only=True)

    def validate(self, data):
        user = authenticate(username=data['email'], password=data['password'])
        if user and user.is_active:
            return user
        raise serializers.ValidationError("Incorrect Credentials")
    

class UserSerializer(serializers.ModelSerializer):
    class Meta:
        model = UserModel
        fields = ["id", "email"]
```

### Session based login
---
- `views.py`:
```python
from django.contrib.auth import get_user_model, login, logout
from rest_framework import permissions, status
from rest_framework.authentication import SessionAuthentication
from rest_framework.views import APIView
from rest_framework.response import Response
from .serializers import UserRegisterSerializer, UserLoginSerializer, UserSerializer


class UserRegister(APIView):
    permission_classes = (permissions.AllowAny,)

    def post(self, request):
        serializer = UserRegisterSerializer(data=request.data)
        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data, status=status.HTTP_201_CREATED)
        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)
    

class UserLogin(APIView):
    permission_classes = (permissions.AllowAny,)
    authentication_classes = (SessionAuthentication,)

    def post(self, request):
        data = request.data.copy()
        serializer = UserLoginSerializer(data=data)
        if serializer.is_valid():
            user = serializer.validate(data)
            login(request, user)
            return Response(serializer.data, status=status.HTTP_200_OK)
        else:
            return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)


class UserLogout(APIView):
    permission_classes = (permissions.AllowAny,)

    def post(self, request):
        logout(request)
        return Response(status=status.HTTP_200_OK)


class UserProfile(APIView):
    permission_classes = (permissions.IsAuthenticated,)
    authentication_classes = (SessionAuthentication,)

    def get(self, request):
        serializer = UserSerializer(request.user)
        return Response(serializer.data, status=status.HTTP_200_OK)
```

- Users `urls.py`:
```python
from django.urls import path
from . import views

urlpatterns = [
    path("register", views.UserRegister.as_view(), name="register"),
    path("login", views.UserLogin.as_view(), name="login"),
    path("logout", views.UserLogout.as_view(), name="logout"),
    path("profile", views.UserProfile.as_view(), name="profile"),
]
```

- Mains `urls.py`
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('users/', include('users.urls')),
]
```
#### API Guide
1. **User Registration (`/register/`)**
    - **Method:** POST
    - **Permissions:** Open to anyone
    - **Request Body:**
        ```JSON
	{
		"email": "user@example.com",
		"password": "strongpassword123"
	}
	```
    
    - **Successful Response (201 Created):**
	```json
	{
		"email": "user@example.com"
	}
	```

2. **User Login (`/login/`)**
    - **Method:** POST
    - **Permissions:** Open to anyone
    - **Request Body:** Same as registration
    - **Successful Response (200 OK):**
        ```json
	{
		"email": "user@example.com"
	}
	```        
	- The login process sets a session cookie in your client for subsequent requests.

3. **User Logout (`/logout/`)**
    - **Method:** POST
    - **Permissions:** Open to anyone
    - **Request Body:** Empty
    - **Successful Response (200 OK):** A simple confirmation message (e.g., "User logged out").

4. **User Profile (`/profile/`)**
    - **Method:** GET
    - **Permissions:** Requires authentication
    - **Successful Response (200 OK):**
        ```json
	{
		"id": 1,
		"username": "user@example.com",
	}
	```