# Django and React Integration Project - Food Delivery App

## Table of Contents
- [Introduction](#introduction)
- [Technologies Used](#technologies-used)
- [Setup Instructions](#setup-instructions)
  - [Backend Setup (Django)](#backend-setup-django)
  - [Frontend Setup (React)](#frontend-setup-react)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Common Issues and Troubleshooting](#common-issues-and-troubleshooting)

---

## Introduction
This project integrates a Django backend with a React frontend to create a full-stack food delivery application. The Django backend handles user authentication, restaurant management, and order processing, while the React frontend provides a user-friendly interface for both customers and restaurant admins.

---

## Technologies Used
- **Backend**: Django, Django REST Framework, PostgreSQL
- **Frontend**: React, React Router DOM, Axios, Tailwind CSS (optional for styling)
- **Database**: PostgreSQL
- **Others**: Node.js, npm/yarn, Python

---

## Setup Instructions

### Backend Setup (Django)
1. **Clone the Repository:**
   ```bash
   git clone <repository_url>
   cd <repository_folder>/backend
   ```

2. **Create and Activate Virtual Environment:**
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Setup PostgreSQL:**
   Ensure PostgreSQL is running locally or use a hosted PostgreSQL instance. Update the PostgreSQL connection settings in `settings.py`:
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'food_delivery_db',
           'USER': 'your_db_user',
           'PASSWORD': 'your_db_password',
           'HOST': 'localhost',
           'PORT': '5432',
       }
   }
   ```

5. **Run Migrations:**
   ```bash
   python manage.py migrate
   ```

6. **Run the Development Server:**
   ```bash
   python manage.py runserver
   ```

7. **Setup CORS:**
   Ensure `django-cors-headers` is installed and configured in `settings.py` to allow requests from the React frontend:
   ```python
   INSTALLED_APPS += ['corsheaders']
   MIDDLEWARE.insert(0, 'corsheaders.middleware.CorsMiddleware')
   CORS_ALLOWED_ORIGINS = ['http://localhost:3000']
   ```

---

### Frontend Setup (React)
1. **Navigate to the Frontend Directory:**
   ```bash
   cd ../frontend
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Start the React Development Server:**
   ```bash
   npm start
   ```

---

## Running the Application
1. **Start the Django Backend:**
   ```bash
   python manage.py runserver
   ```
2. **Start the React Frontend:**
   ```bash
   npm start
   ```
3. **Access the Application:**
   - Django API: `http://localhost:8000`
   - React Frontend: `http://localhost:3000`

---

## Project Structure

### Backend (Django)
```
backend/
|-- manage.py
|-- db.sqlite3
|-- myapp/
    |-- migrations/
    |-- __init__.py
    |-- admin.py
    |-- apps.py
    |-- models.py
    |-- views.py
    |-- urls.py
```

### Frontend (React)
```
frontend/
|-- public/
|   |-- index.html
|-- src/
    |-- components/
        |-- registerRestaurant.js
        |-- registerCustomer.js
        |-- loginRestaurant.js
        |-- loginCustomer.js
        |-- restaurant.js
        |-- customer.js
    |-- App.js
    |-- index.js
```

---

## API Endpoints

### Registration Endpoints
- **Register Restaurant:** `POST /register/restaurant/`
  - Payload:
    ```json
    {
      "username": "<restaurant_username>",
      "password": "<restaurant_password>"
    }
    ```

- **Register Customer:** `POST /register/customer/`
  - Payload:
    ```json
    {
      "username": "<customer_username>",
      "password": "<customer_password>"
    }
    ```

### Login Endpoints
- **Login Restaurant:** `POST /login/restaurant/`
  - Payload:
    ```json
    {
      "username": "<restaurant_username>",
      "password": "<restaurant_password>"
    }
    ```

- **Login Customer:** `POST /login/customer/`
  - Payload:
    ```json
    {
      "username": "<customer_username>",
      "password": "<customer_password>"
    }
    ```

### Order and Menu Management
- **Restaurant Home (Upload Menu):** `POST /home/`
  - Payload: Form data for menu details

- **Retrieve Customer Orders:** `GET /customer/<order_id>/`
  - Query Parameter: `order_id` (ID of the order to retrieve)

---

## Common Issues and Troubleshooting

### 1. CORS Errors
- Ensure `CORS_ALLOWED_ORIGINS` in Django settings is configured properly to allow frontend requests.

### 2. PostgreSQL Connection Issues
- Verify that PostgreSQL is running on `localhost:5432` or update the connection settings to match your setup.

### 3. React Routing Issues
- Ensure React Router is properly set up and paths match backend endpoints.

### 4. Module Not Found Errors
- For backend:
  ```bash
  pip install <missing_package>
  ```
  For frontend:
  ```bash
  npm install <missing_package>
  ```

---

This README provides the setup and usage instructions for the food delivery app project. Let me know if additional information is required.
