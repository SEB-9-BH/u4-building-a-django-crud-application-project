<h1>
  <span class="headline">Build a Django CRUD Application Project</span><br/>
  <span class="subhead">Step By Step Project Build</span>
</h1>

## Project Instructions

For your project, you will be building and testing an application using **Django**, with optional testing using **Pytest**, and **HTTPX**. This project will give you the opportunity to build a complete, dynamically templated API with full CRUD functionality, as well as write automated tests to ensure its reliability.

### **Choose Your Theme**

Start by choosing a theme or service that interests you. Consider building a project that aligns with sustainability, community impact, or any area you’re passionate about.

### **What You'll Learn**

By completing this project, you’ll

- Build a modular, well structured Django application following MVT (Model-View-Template) architecture.

- Implement full CRUD operations with authorization restricting access to resources.

- Create a dynamic frontend using Django templates with proper URL Routing and template inheritance for a cohesive UI.

Bonus:

- Write automated tests for your API endpoints using Pytest and HTTPX.

- Develop skills for building and testing real-world APIs.

### **Getting Started**

Follow the provided project outline and reference our in-class lesson materials to create a Django application with a fully functional API and thorough test coverage. This project is your chance to combine coding and testing skills into a valuable, portfolio-worthy application.

## 1. Initialize Django Project

1. Initialize a new virtual environment inside your project directory and install Django:

  ```bash
  pipenv install django
  ```

2. **Start a new Django project within your virtual environment:**
  
  ```bash
  django-admin startproject <myproject>
  ```

3. **Activate the virtual environment:**

  ```bash
  pipenv shell
  ```

4. **Start an application within your project directory, adjacent to the Django project you created in the last step.**
  
  ```bash
  python3 manage.py startapp myproject_app
  ``` 
   
5. Register your application by adding your app to the list of `INSTALLED_APPS` in `settings.py`.

## 2. **Configure your Database**
1. **Create Your Database**: Before adjusting the `settings.py`, ensure you create your database.

   ```bash
   createdb myproject
   ```

2. **Database Settings**: Edit the `settings.py` file to include your local database settings.

   ```python
   DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.postgresql',
          'NAME': 'myproject',
      }
   }
   ```

3. **Install psycopg2-binary to connect your PostgreSQL database to your application.**

    ```bash
    pipenv install psycopg2-binary
    ```

4. **Migrate Models**: After setting up your model classes in `models.py`, make and apply migrations.
   ```bash
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

5. **Start the Server**
   ```bash
   python3 manage.py runserver
   ```

## 3. **Set Up URL Routing**

1. **Create URL Configuration**: Make a new `urls.py` in your app directory to handle app-specific routes.

2. **Include App URLs in Project**: Modify the project’s `urls.py` to include your app’s URL configurations.

   ```python
   from django.urls import path, include

   urlpatterns = [
      path('admin/', admin.site.urls),
      path('', include('myproject_app.urls')), # Mount the app's routes at the root URL
   ]
   ```

## 4. **Implement Full CRUD for a Model**

Develop URL patterns, views, and templates to manage a resource fully. Your application should include views for:

- **Home**: The landing page
- **Index**: List all instances of the model
- **Detail**: Show details of a single instance
- **Create**: Form to create a new instance
- **Update**: Form to update an existing instance
- **Delete**: Handle the deletion of an instance

## 5. **Introduce a Secondary Model with Associations**

1. **Model Association**: Create a **_one-to-many relationship_** with a second model.
2. **Manage Resources**: Implement full CRUD operations for the secondary model, ensuring resources can be created, read, updated, and deleted:

## 6. **Integrate Authentication**

1. **Enable Django Authentication**: Incorporate Django’s built-in authentication system to manage user accounts.
2. **Admin Dashboard**: Utilize Django’s admin to manage user activities.
3. **Protect Resources**: Ensure that routes related to user-owned resources require authentication.

## 7. **Introduce a Third Model with Associations**

1. **Model Association**: Create a **_many-to-many relationship_** with a third model.
2. **Manage Resources**: Implement full CRUD operations for the third model, ensuring resources can be created, read, updated, and deleted.

## 8.  **Create a Templates Directory**: Each Django app should have its own `templates` directory where all its templates will be stored. This keeps your project organized and makes templates easy to find.

Open your terminal and create a `templates` directory inside your `myproject_app` directory:

  ```bash
  mkdir myproject_app/templates
  ```

### **Optional Bonus**
## 9. Writing Tests Using Pytest and HTTPX

1. **Create a `tests` Directory:**

   Store your test files in a `tests/` folder.

2. **Write Test Cases in `tests/test_items.py`:**

   Use `httpx.AsyncClient` to test API endpoints asynchronously.

3. **Write Additional Tests for Full CRUD Operations:**

   - Test creating an item (`POST /api/items`)
   - Test retrieving an item by ID (`GET /api/items/{id}`)
   - Test updating an item (`PUT /api/items/{id}`)
   - Test deleting an item (`DELETE /api/items/{id}`)

## 5. Run the Tests

Execute your tests using Pytest:

```bash
pipenv run pytest
```

You should see results indicating whether your API endpoints work as expected.
