# Lesson 03: Understanding Django Project Structure

## 🚀 Concept

When you run `django-admin startproject mysite`, Django creates a basic folder structure for you. Let’s break it down — so you’re not just copying commands, but actually **understanding** what’s going on.

---

## 🏗️ Analogy: Django Project is Like a Building

Think of your Django project as a building site 🏢:

- The **project folder** (`mysite/`) is like the entire construction site.
- Inside, you have your **blueprints**, **electric systems**, **front door**, and **manager**.

Let’s go room by room.

---

## 🗂️ File & Folder Overview

If you look inside your `mysite/` project, you'll see:

mysite/
├── manage.py
├── mysite/
│ ├── init.py
│ ├── asgi.py
│ ├── settings.py
│ ├── urls.py
│ └── wsgi.py


🔹 `manage.py`

> 💬 Think of this as **your site manager**.  
It lets you run commands like:
- `runserver`
- `migrate`
- `createsuperuser`

You’ll use it **a lot** during development.

---

### 🔹 The inner `mysite/` folder

Yes, Django creates two folders with the same name. The inner one holds your **project’s core settings and wiring**.

Let’s open it up:

#### 🛠️ `settings.py` — Your Control Panel

Like the **main circuit breaker box**.  
Controls:
- Which apps are installed
- Database settings
- Static files and media
- Debug mode and security

You'll return here often.

---

#### 🔌 `urls.py` — The Front Door

Like a **receptionist or security guard**.

This file decides what happens when someone visits:

yourwebsite.com/home

It connects each URL path to a **view** (you’ll build those soon).

---

#### 🌐 `wsgi.py` and `asgi.py` — The Internet Connectors

You won’t touch these much.  
They connect your Django app to web servers:
- `wsgi.py`: For regular web apps
- `asgi.py`: For async stuff like chat or websockets

---

#### 📦 `__init__.py`

This file tells Python:  
“Hey, this folder is a real Python package.”

---



