# Lesson 04: Creating Your First Django App

## 🚀 Concept

A Django **project** is the overall website — but it’s made up of **apps**, each focused on one job.

---

## 🧱 Analogy: Project = City, App = Building

Imagine your Django project is a **city** 🏙️  
Each **app** is a different building:
- A blog 📝
- A store 🛒
- A user system 👤

Each app does one thing well — and Django lets you mix them together into one website.

---

## 🛠️ Let’s Build a “Hello” App

We'll create a simple app called `hello` that returns a greeting.

---

## 📄 Step-by-Step

> Run these in your Django project root (where `manage.py` is)

### 1. Create the app


`python manage.py startapp hello`   #This creates a folder called hello/ with starter code inside.

2. Register the app in settings.py
Open mysite/settings.py, and in the INSTALLED_APPS list, add this line:

'hello',

3. Create a view
Open hello/views.py and add:

`from django.http import HttpResponse`


  `def say_hello(request):
    return HttpResponse("Hello from your first app!")`

4. Add a URL route for the app
Create a new file in your hello/ folder called:
urls.py

Then paste:

`from django.urls import path`
`from . import views`
 `urlpatterns = [
    path('', views.say_hello),
]`

5. Connect the app to the project
Open your main mysite/urls.py and update it like this:

`from django.contrib import admin`
`from django.urls import path, include`
 `urlpatterns = [
    path('admin/', admin.site.urls),
    path('hello/', include('hello.urls')),
]`

Now visiting /hello/ will show your app's message!  #add /hello/ at the end of the url when the server runs






