# Lesson 02: Setting Up Your Django Project

## 🚀 Concept

Before we build anything, we need to prepare the **workspace** — like setting up a clean construction site.

In this lesson, we’ll:
- Create a virtual environment (a safe workspace)
- Install Django (your main toolset)
- Start your first Django project (the blueprint)
- Run the development server (to view your app)

---

## 🧱 Analogy: Your Web App is Like a Construction Site 🏗️

Think of Django like your **construction crew**.

- Your **virtual environment** is the fenced-off area for this one project. No one else touches it.
- **Django** is your toolbox. It has drills, saws, bricks — everything to build.
- A **project** is the site plan: how things are laid out.
- An **app** is like a building within that site (e.g. blog, store, chat). 
Example, in a supermarket(project/site), there are sections for clothes, food,toiletaries, and more. These sections are designed and organized to fit perfectly inside the supermarket. In django, these 'sections' are called apps.

We're preparing your site now — so you can build later!

---

## 🛠️ Step-by-Step Instructions

> Do all of this inside your Codespaces terminal

### 1. Create and activate a virtual environment

```bash
python3 -m venv env
source env/bin/activate

✅ This keeps your Python packages safe and separate.i.e fence for the project.

2. Install Django
bash
pip install django

✅ Now you have Django ready to use in your toolbox.

3. Start a new Django project

django-admin startproject mysite #this is what you want to create.i.e. the supermarket building called mysite
cd mysite #move inside your building i.e. mysite

4. Run the development server #local testing area to check how the project is going, if everything is working properly

python manage.py runserver

✅ Django will start a mini server, and you’ll see a URL like:

http://127.0.0.1:8000/ #Click to see django's welcome page









