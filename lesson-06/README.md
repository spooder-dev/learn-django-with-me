# Lesson 06: Dynamic Templates with Context

## 🚀 Concept

Django templates can show more than static text — they can display **dynamic data** passed from your views.

This is done using something called **context** — a dictionary that sends information from the Python code to the HTML page.

---

## 🍱 Analogy: Context is Like a Lunchbox

Imagine you're a parent packing lunch for your kid 🍱

- The **template** is the lunch table (HTML page)
- The **context** is the lunchbox: it carries food (data) from home (Python) to the table (HTML)
- The **view** packs the lunchbox and delivers it

---

## 🛠️ Let's Build a Dynamic Page

We'll update your `hello` app to send a name to the HTML page.

---

### 1. Update the view

In `hello/views.py`, update `say_hello()`:

```python
from django.shortcuts import render

def say_hello(request):
    context = { 
        'name': 'Ann',
        'items': ['Apples', 'Bananas', 'Cookies']
    }
    return render(request, 'hello/greeting.html', context) #this means: take the greeting.html file, fill it with the data in context, and send it back to the browser as the web page the user will see.”
```

2. Update the template

In hello/templates/hello/greeting.html, replace its content with:
```
<!DOCTYPE html>
<html>
<head>
    <title>Hello Page</title>
</head>
<body>
    <h1>Hello, {{ name }}!</h1>

    <h2>Your favorite items:</h2>
    <ul>
        {% for item in items %} #for loop like in python, each item in the context/dictionary is treated as a variable
            <li>{{ item }}</li>
        {% endfor %}
    </ul>
</body>
</html>
```

✅ Now the page is using data passed from the view!

3. Run the server and visit /hello/

You should see:
Hello, Ann!
Your favorite items:
- Apples
- Bananas
- Cookies

NB: Context is just a regular Python dict. Django takes this dictionary and makes each key available inside the template as a variable. You can name it however you want, doesn't necessarily have to be named context. However, context is the standard naming convention.



💡 Tips

    {{ variable }} → displays a value

    {% for ... %} → loops through a list

    {% if ... %} → adds conditional logic
