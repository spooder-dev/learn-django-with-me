# Lesson 08: Django Admin Panel

## 🚀 Concept

Django gives you a built-in **admin panel** — a full-featured web interface for managing your site’s data.

Instead of building your own dashboard from scratch, you get a beautiful one “for free” — and it’s super powerful!

---

## 🛠️ What Can You Do With It?

- Add, edit, or delete data
- Manage users
- View and search models
- Save loads of time while building apps

---

## 🧠 Analogy: Admin is the Control Room

Imagine your website is a theme park 🎢

- The admin panel is the **control room**
- You, the developer or admin, can **see everything**, **control rides (data)**, and **manage visitors (users)**

It’s not meant for visitors — it’s for you!

---

## 🧪 Let’s Try It Out

We’ll set up Django Admin and use it to manage data from your `hello` app.

---

### ✅ 1. Create a Superuser

Run this in the terminal:

```bash
python manage.py createsuperuser

Follow the prompts:

    Username

    Email (optional)

    Password (twice) #don't be shocked when it shows blank, passwords aren't revealed in the terminal

✅ 2. Run the Server and Access Admin

python manage.py runserver

Then visit: http://127.0.0.1:8000/admin/

Log in using the superuser account you just created.
🎉 You’re now inside the Django Admin panel!

📦 3. Register a Model in Admin
A model is like a table to store data. Each class is a table, ie the class Greeting is a table with the fields name and message. The fields are the columns in the table.

Create a model in hello/models.py:

from django.db import models

class Greeting(models.Model):
    name = models.CharField(max_length=50)
    message = models.TextField()

    def __str__(self):
        return f"Greeting from {self.name}"

✅ 4. Add to admin.py
We register it in the admin.py so that django knows to display that information in the admin panel and no where else; only the superuser can access that data

Open hello/admin.py and register your model:

from django.contrib import admin
from .models import Greeting

admin.site.register(Greeting)

✅ 5. Apply Migrations
makemigrations is like staging the tables to add to the database. This is like git add . command. saying you want to add those tables to your database.
migrate is saving the changes made/ tables made to the database. This is like git commit -m "" command.i.e saving that version .

To create the table for your model in the database:

python manage.py makemigrations
python manage.py migrate

✅ 6. Add, Edit, and View in Admin

    Refresh the admin panel

    You’ll see a section for Greetings

    Add a few records and play around!

