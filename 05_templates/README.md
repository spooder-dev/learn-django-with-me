# Lesson 05: Templates and HTML Pages

## 🚀 Concept

So far, we've been returning plain text using `HttpResponse`. But websites are made of **HTML pages**, not just messages.

In this lesson, you'll learn how to use **templates** — Django’s way of rendering real web pages.

---

## 🧁 Analogy: Templates Are Like Cake Molds

Imagine you’re a baker 🎂

- You don’t bake each cake by hand.
- You use a **cake mold (template)** and pour different ingredients into it.

In Django:
- The **template** is your mold (an HTML file).
- The **view** pours in the ingredients (data).
- The browser gets a full, beautiful cake (web page).

---

## 🛠️ Let's Build It

We’ll update your `hello` app to return an HTML page instead of plain text.

---

### 1. Create a `templates` folder

Inside your `hello/` app folder, create this structure:

hello/
└── templates/
└── hello/
└── greeting.html


# ✨ It’s important to match the folder name (`hello`) inside `templates/`.

---

### 2. Add an HTML template

Inside `greeting.html`, paste:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Greeting Page</title>
</head>
<body>
    <h1>Hello, Django learner! 🎉</h1>
    <p>This is your first real HTML page served by Django.</p>
</body>
</html>
```
3. Update the view

In hello/views.py, replace say_hello() with:
```
from django.shortcuts import render

def say_hello(request):
    return render(request, 'hello/greeting.html')`
```
✅ Now Django will render your template instead of returning plain text. Rendering is the process of combining a html file + the data in it into a html page to send to the browser. It's also known as showing or displaying.

4. Run the server and visit /hello/
```
python manage.py runserver
```
Then visit:
http://127.0.0.1:8000/hello/
🎉 You should see your HTML page — not just a message.
