# 🍔 Food Ordering System — Django

![Python](https://img.shields.io/badge/Python-54.9%25-3776AB?style=flat&logo=python&logoColor=white)
![HTML](https://img.shields.io/badge/HTML-45.1%25-E34F26?style=flat&logo=html5&logoColor=white)
![Django](https://img.shields.io/badge/Django-4.x-092E20?style=flat&logo=django&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?style=flat&logo=bootstrap&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

A full-stack **Food Ordering Web Application** built with **Django**, allowing users to browse food items, customize them with multiple options, manage a cart, place orders, and receive **email confirmations**. Features a clean admin dashboard for managing foods and orders, with a scalable, real-world project structure.

---

## 📑 Table of Contents

- [✨ Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [📁 Project Structure](#-project-structure)
- [🚀 Installation & Setup](#-installation--setup)
- [🔑 Environment Variables](#-environment-variables)
- [📧 Email Configuration](#-email-configuration-gmail-smtp)
- [🗄 Admin Panel](#-admin-panel)
- [🔁 Order Flow](#-order-flow)
- [🖼 UI & UX](#-ui--ux)
- [🔒 Security](#-security)
- [🔮 Future Enhancements](#-future-enhancements)
- [📄 License](#-license)

---

## ✨ Features

- 👤 **User Authentication** — Register, Login & Logout with secure password hashing
- 🔐 **reCAPTCHA** protection on registration forms
- 🍕 **Browse Food Items** — View items with images, descriptions, ratings & pricing
- 🎛 **Food Customization** options:
  - 🍞 Base
  - 📏 Size (with size in cm)
  - 🧀 Toppings
  - 🥣 Sauces
- 🛒 **Cart Management** — Add, update quantity & remove items
- 📦 **Order Placement** — Order summary with total price calculation
- 📧 **Email Confirmation** — HTML invoice email sent after successful order
- 🛠 **Django Admin Panel** — Full CRUD management for foods, options & orders
- 📱 **Responsive UI** — Built with Bootstrap 5
- 🧾 **Clean Forms** — Powered by Django Crispy Forms
- 🎨 **Modern Icons** — Bootstrap Icons throughout the UI
- 👤 **User Profile** — View and update profile with photo upload

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Django (Python) |
| **Frontend** | HTML5, CSS3, Bootstrap 5 |
| **Forms** | Django Crispy Forms + crispy-bootstrap5 |
| **Icons** | Bootstrap Icons |
| **Database** | SQLite (default, easily swappable) |
| **Authentication** | Django Auth System + django-recaptcha |
| **Email** | Gmail SMTP |
| **Media Storage** | Local filesystem (`userimg/`, `foodimg/`, etc.) |

---

## 📁 Project Structure

```text
food-ordering-system-django/
│
├── foodsapp/                  # Core food ordering app
│   ├── migrations/
│   ├── admin.py               # Registers all models to admin
│   ├── apps.py
│   ├── context_processors.py  # Global cart count context
│   ├── models.py              # FoodItems, Cart, Order, Options models
│   ├── urls.py                # Food-related URL routes
│   ├── utils.py               # Email sending utility
│   └── views.py               # All food/cart/order views
│
├── learningapp/               # User management app
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py               # UserForm, UserprofileForm, UpdateForms
│   ├── models.py              # UserDetails model
│   ├── urls.py                # Auth URL routes
│   └── views.py               # Registration, login, profile, logout
│
├── learning/                  # Django project settings
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── templates/                 # HTML templates
│   ├── base.html
│   ├── home.html
│   ├── registration.html
│   ├── login.html
│   ├── profile.html
│   ├── update.html
│   ├── bill_invoice_template.html
│   ├── foods/
│   │   ├── allfoods.html
│   │   ├── foodDetails.html
│   │   ├── customize.html
│   │   ├── addfood.html
│   │   └── cart.html
│   └── orders/
│
├── static/                    # Static files (CSS, images)
│   ├── css/
│   └── images/
│
├── userimg/                   # Uploaded user profile images
├── db.sqlite3                 # SQLite database
├── manage.py
├── LICENSE
└── README.md
```

---

## 🚀 Installation & Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/GowthamReddyT/food-ordering-system-django.git
cd food-ordering-system-django
```

### 2️⃣ Create & Activate Virtual Environment

```bash
# Create virtual environment
python -m venv env

# Activate — Windows
env\Scripts\activate

# Activate — Linux / Mac
source env/bin/activate
```

### 3️⃣ Install Dependencies

```bash
pip install django django-crispy-forms crispy-bootstrap5 pillow django-recaptcha
```

### 4️⃣ Configure Crispy Forms

Add the following to `learning/settings.py`:

```python
INSTALLED_APPS = [
    ...
    "crispy_forms",
    "crispy_bootstrap5",
    "django_recaptcha",
]

CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
CRISPY_TEMPLATE_PACK = "bootstrap5"
```

### 5️⃣ Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6️⃣ Create Superuser

```bash
python manage.py createsuperuser
```

### 7️⃣ Run the Development Server

```bash
python manage.py runserver
```

Open in browser: **http://127.0.0.1:8000/**

---

## 🔑 Environment Variables

For production, it is recommended to store sensitive values in environment variables or a `.env` file. Key values to configure in `settings.py`:

| Variable | Description |
|---|---|
| `SECRET_KEY` | Django secret key |
| `DEBUG` | Set to `False` in production |
| `ALLOWED_HOSTS` | List of allowed hosts |
| `EMAIL_HOST_USER` | Your Gmail address |
| `EMAIL_HOST_PASSWORD` | Your Gmail App Password |
| `RECAPTCHA_PUBLIC_KEY` | Google reCAPTCHA site key |
| `RECAPTCHA_PRIVATE_KEY` | Google reCAPTCHA secret key |

---

## 📧 Email Configuration (Gmail SMTP)

Add the following in `learning/settings.py`:

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'your_email@gmail.com'
EMAIL_HOST_PASSWORD = 'your_app_password'  # Use a Gmail App Password
DEFAULT_FROM_EMAIL = EMAIL_HOST_USER
```

> ⚠️ Use a **Gmail App Password** (not your regular Gmail password). Enable 2-Step Verification in your Google account first.

---

## 🗄 Admin Panel

Access the Django Admin Panel at: **http://127.0.0.1:8000/admin/**

Admin can manage:

| Model | Description |
|---|---|
| `FoodItems` | Add / edit / delete food items with images |
| `SizeOption` | Size variants per food item |
| `BaseOption` | Base variants per food item |
| `ToppingOption` | Topping variants per food item |
| `SauceOption` | Sauce variants per food item |
| `Order_Details` | View all placed orders |
| `OrderItem` | View individual items per order |
| `UserDetails` | Manage user profiles |

---

## 🔁 Order Flow

```
User registers / logs in
        ↓
Browses food items (allfoods/)
        ↓
Views food details (food/<id>/)
        ↓
Customizes food (size, base, topping, sauce)
        ↓
Adds to cart (add-to-cart/<id>/)
        ↓
Views & updates cart (cart/)
        ↓
Proceeds to checkout → Places order (order/)
        ↓
Payment confirmation (payment/)
        ↓
📧 Email invoice sent to user
        ↓
Admin views order in dashboard
```

---

## 🖼 UI & UX

- **Bootstrap 5** based fully responsive layout
- **Django Crispy Forms** for clean, styled form rendering
- **Bootstrap Icons** for action buttons and navigation
- Organized templates with a shared `base.html` layout
- Separate template directories per app (`foods/`, `orders/`)
- Global **cart count** available in all pages via context processor

---

## 🔒 Security

- ✅ CSRF protection enabled on all forms
- ✅ Secure password hashing (Django's default PBKDF2)
- ✅ Django ORM used throughout (SQL injection safe)
- ✅ `@login_required` decorator protecting sensitive routes
- ✅ reCAPTCHA on registration to prevent bots

---

## 🔮 Future Enhancements

- [ ] Online payment gateway integration (Razorpay / Stripe)
- [ ] Order tracking system with status updates
- [ ] REST API using Django REST Framework
- [ ] Docker containerization support
- [ ] Cloud deployment (AWS / Azure / Railway)
- [ ] Mobile app integration
- [ ] Product reviews & ratings by users
- [ ] Vendor dashboard for multi-restaurant support

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

> Built with ❤️ by [GowthamReddyT](https://github.com/GowthamReddyT)