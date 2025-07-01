# Lesson 09: Building Your First Django Form

## 🚀 Concept

A **form** lets users send data to your website — like their name, a message, or feedback.

Django makes it easy to:
- Create a form
- Show it on a page
- Handle the submitted data

---

## 🧠 Analogy: A Form is Like a Mailbox

- The **form** is the paper where someone writes a message ✍️
- When they hit **Submit**, Django **receives the envelope** and processes the info 📬
- You can then **use** that info (save it, show it, or send a response)

---

## 🛠️ Let's Build a Simple Greeting Form

---

### ✅ 1. Create a Django form class

In your `hello/forms.py` file (create it if it doesn't exist), add:

```python
from django import forms

class GreetingForm(forms.Form):
    name = forms.CharField(label='Your Name', max_length=100)
    message = forms.CharField(widget=forms.Textarea, label='Message')

This defines a simple form with two fields.

✅ 2. Add a view that shows the form

In hello/views.py, add a new view:

from django.shortcuts import render
from django.http import HttpResponse
from .forms import GreetingForm  # Added in Lesson 09

# Lesson 03: Basic view that returns text
def basic_hello(request):
    return HttpResponse("Hello, world!")

# Lesson 04: Rendering a template without context
def say_hello(request):
    return render(request, 'hello/greeting.html')

# Lesson 06: Rendering a template with context (dynamic data)
def say_hello_with_context(request):
    context = {
        'name': 'Ann',
        'items': ['Apples', 'Bananas', 'Cookies']
    }
    return render(request, 'hello/greeting.html', context)

# Lesson 09: Form that collects and shows user input
def greeting_form(request):
    submitted_data = None

    if request.method == 'POST':
        form = GreetingForm(request.POST)
        if form.is_valid():
            submitted_data = form.cleaned_data
    else:
        form = GreetingForm()

    return render(request, 'hello/greeting_form.html', {
        'form': form,
        'submitted_data': submitted_data
    })

✅ 3. Create the template

In hello/templates/hello/greeting_form.html:

{% load static %}
<!DOCTYPE html>
<html>
<head>
    <title>Greeting Form</title>
</head>
<body>
    <h1>Send a Greeting</h1>

    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Send</button>
    </form>

    {% if submitted_data %}
        <hr>
        <h2>Submitted Data:</h2>
        <p><strong>Name:</strong> {{ submitted_data.name }}</p>
        <p><strong>Message:</strong> {{ submitted_data.message }}</p>
    {% endif %}
</body>
</html>

✅ {{ form.as_p }} automatically renders the form fields as HTML paragraphs
✅ {% csrf_token %} protects the form from cross-site attacks

✅ 4. Add the URL

In hello/urls.py, add:

from django.urls import path
from . import views

urlpatterns = [
    path('', views.basic_hello, name='basic_hello'),                     # Lesson 03
    path('hello/', views.say_hello, name='say_hello'),                   # Lesson 04
    path('hello-context/', views.say_hello_with_context, name='say_hello_with_context'),  # Lesson 06
    path('form/', views.greeting_form, name='greeting_form'),            # Lesson 09
]

Now when you visit /form/, you’ll see the form, and it will show the submitted message after you click Submit.