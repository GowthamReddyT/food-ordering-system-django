# foodappp
🍽️ Django Food Ordering Application

A full-stack Food Ordering Web Application built using Django, allowing users to browse food items, customize them with multiple options, manage a cart, place orders, and receive email confirmations.
The project uses Django Crispy Forms for clean form rendering and Bootstrap Icons for a modern UI.

🚀 Features

User authentication (Login / Logout)

Browse food items with images and pricing

Food customization options:

Base

Size

Toppings

Sauces

Add to cart & update quantities

Order placement with summary

Email confirmation after successful order

Django Admin panel for full management

Responsive UI using Bootstrap

Clean forms using Django Crispy Forms

Modern icons using Bootstrap Icons

🛠️ Tech Stack

Backend: Django (Python)

Frontend: HTML, CSS, Bootstrap

Forms: Django Crispy Forms

Icons: Bootstrap Icons

Database: SQLite (default)

Email Service: Gmail SMTP

Authentication: Django Auth System

📁 Project Structure
Learning/
│
├── foodsapp/
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── urls.py
│   ├── utils.py
│   └── views.py
│
├── learning/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── learningapp/
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   └── views.py
│
├── templates/
│   ├── base.html
│   ├── foods/
│   └── orders/
│
├── static/
│   ├── css/
│   └── images/
│
├── db.sqlite3
├── manage.py
└── README.md




Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/your-username/django-food-app.git
cd django-food-app
2️⃣ Create & Activate Virtual Environment
python -m venv env
env\Scripts\activate        # Windows
source env/bin/activate    # Linux / Mac
3️⃣ Install Dependencies
pip install django django-crispy-forms crispy-bootstrap5
4️⃣ Configure Crispy Forms

Add to settings.py:

INSTALLED_APPS = [
    ...
    "crispy_forms",
    "crispy_bootstrap5",
]


CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
CRISPY_TEMPLATE_PACK = "bootstrap5"
5️⃣ Apply Migrations
python manage.py makemigrations
python manage.py migrate
6️⃣ Create Superuser
python manage.py createsuperuser
7️⃣ Run the Server
python manage.py runserver

Open in browser:

http://127.0.0.1:8000/
🔐 Admin Panel

Access Django Admin:

http://127.0.0.1:8000/admin/

Admin can manage:

Food items

Base / Size / Topping / Sauce options

Orders and order items

Users

📧 Email Configuration (Gmail SMTP)

Add the following in settings.py:

EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True


EMAIL_HOST_USER = 'your_email@gmail.com'
EMAIL_HOST_PASSWORD = 'your_app_password'

Used for order confirmation emails.

🧾 Core Modules
Foods App

Food items

Customization options

Cart logic

Order handling

Email utilities

Learning App

User-related models & views

🛒 Order Flow

User logs in

Browses food items

Selects customization options

Adds items to cart

Proceeds to checkout

Places order

Receives email confirmation

Admin views order in dashboard

🎨 UI & UX

Bootstrap-based responsive layout

Django Crispy Forms for clean forms

Bootstrap Icons for buttons and actions

Organized templates and static files

🔒 Security

CSRF protection enabled

Secure password hashing

Django ORM (SQL injection safe)

Auth-protected routes

🚧 Future Enhancements

Online payment gateway integration

Order tracking system

REST API with Django REST Framework

Docker support

Cloud deployment (AWS / Azure)

Mobile app integration
