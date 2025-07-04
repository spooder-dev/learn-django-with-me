# Lesson 07: Static Files — Adding CSS and Images

## 🚀 Concept

Websites don’t just show HTML — they include **CSS for styling**, **JavaScript for behavior**, and **images** for content. These are called **static files**.

In Django, you need to set up a few things to use them properly.

---

## 🎨 Analogy: Static Files Are Decorations

Imagine your web page is a room.  
- The **HTML** is the walls and furniture.
- The **CSS** is the paint and decorations.
- The **images** are artwork on the wall.

Static files are what **make your room beautiful** 🪴

---

## 🛠️ Let’s Add CSS and an Image

We’ll style the greeting page in your `hello` app.

---

### 1. Create the static folder structure

Inside the `hello/` app, create:

hello/
└── static/
└── hello/
├── style.css
└── image.jpg #download an image and save it in the folder as shown in the project structure


✅ Place your CSS file (`style.css`) and an image (`image.jpg`) in that folder.

---

### 2. Add content to `style.css`

```css
body {
    background-color: #fef6e4;
    font-family: sans-serif;
    text-align: center;
    padding: 50px;
}

h1 {
    color: #f582ae;
}

img {
    width: 200px;
    border-radius: 10px;
}
```

3. Update your HTML template

Open greeting.html and add this at the top of the file:
```
{% load static %}
<!DOCTYPE html>
<html>
<head>
    <title>Styled Page</title>
    <link rel="stylesheet" href="{% static 'hello/style.css' %}">
</head>
<body>
    <h1>Hello, {{ name }}! 👋</h1>
    <img src="{% static 'hello/image.jpg' %}" alt="Image"> 
    <p>Welcome to a styled Django page.</p>
</body>
</html>
```

🔍 What does {% load static %} mean?

In Django templates, {% load static %} is a special instruction that tells Django:

    “I want to use the static file features in this template — please load the tools that handle them.”

🧠 Analogy: Asking for the Toolbox

Imagine you’re in a kitchen 🍳 and you say:

    “Let me cut this fruit.”

You need to first open the drawer and get the knife.

    load static = open the drawer and get the tools

    static 'hello/style.css' = actually use the knife (get the file)

4. Make sure Django is configured to find static files

In mysite/settings.py, check this line exists:

STATIC_URL = 'static/'

This line in settings.py tells Django:

    “When I use {% static '...' %} in a template, start looking for the file at this base URL: /static/.”

It's the base URL prefix Django uses when serving static files in development (like CSS, images, JS).


5. Run your server and check /hello/
Visit http://127.0.0.1:8000/hello/ — your page should be styled and show the image!

