👤 Author

Isaac Akhtar Zada

# Message Board App

A simple message board web application built with **Django 4.2**, created as part of coursework following the *Django for Beginners* tutorial.  
This project demonstrates core Django concepts such as models, views, templates, URL routing, and admin configuration.

---

## 📌 Features

- Fully functional Django project and app structure  
- `Post` model with text-based messages  
- Class-Based `HomePageView` using `ListView`  
- Homepage displays all posts dynamically  
- Django admin configured to manage posts  
- Clean template-based UI  
- Uses migrations to manage database schema  

---

## 🗂️ Project Structure

message-board-app/
│
├── django_project/
│ ├── init.py
│ ├── asgi.py
│ ├── settings.py
│ ├── urls.py
│ └── wsgi.py
│
├── posts/
│ ├── migrations/
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── models.py
│ ├── tests.py
│ ├── urls.py
│ └── views.py
│
├── templates/
│ └── home.html
│
├── manage.py
├── .gitignore
└── README.md

---

## 🚀 How to Run This Project Locally

### 1. Clone the repository

```bash
git clone https://github.com/IsaacAkh/message-board-app.git
cd message-board-app

###2. Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

3. Install dependencies
pip install django~=4.2.0

4. Run migrations
python manage.py migrate

5. (Optional) Create a superuser for admin access
python manage.py createsuperuser

6. Start the development server
python manage.py runserver

Open in your browser:
👉 http://127.0.0.1:8000/

📝 Django Admin

Access the dashboard:

👉 http://127.0.0.1:8000/admin/

✔️ Model Used
class Post(models.Model):
    text = models.TextField()

    def __str__(self):
        return self.text[:50]

✔️ View Used
class HomePageView(ListView):
    model = Post
    template_name = "home.html"

✔️ URL Configuration
Project-level django_project/urls.py
urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("posts.urls")),

App-level posts/urls.py
urlpatterns = [
    path("", HomePageView.as_view(), name="home"),
]

📄 Template (templates/home.html)
<h1>Message board homepage</h1>

<ul>
  {% for post in post_list %}
    <li>{{ post.text }}</li>
  {% endfor %}
</ul>

🎯 Purpose of This Project

This project demonstrates:

Creating Django apps and folders

Defining models and running migrations

Using the Django admin

Building class-based views

Rendering templates

Setting up URL routing
