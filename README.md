Woromedia-take_home_assignment
===============

The project provides user authentication for users with email verification using the django-rest-authemail package (internally uses Django rest framework) and also using Google OAuth. A simple frontend has been designed to show the following functionalities. The django-rest-authemail api guide which inculdes endpoints, response, requests, etc is [here](https://www.django-rest-framework.org/api-guide/authentication/).


Installation
------------

Create a virtual environment and activate it.

Clone the repo.

```python
git clone https://github.com/Shriramu2002/woromedia-take_home_assignment.git
```

Install the required packages into your virtual environment.

```python
pip install -r requirements.txt
```

Either add your email settings to your environment or enter them directly at the bottom of the `settings.py` file.  The setting `AUTH_EMAIL_VERIFICATION` (default: True) can be set to False, if you don't want email verification to be performed. Also, update the `EMAIL_HOST_USER` and `EMAIL_HOST_PASSWORD` fields to relevant values.


```python
vim wmtha_project/settings.py
```

Create the database tables with Django's `migrate` and create a superuser with `createsuperuser`.

```python
python manage.py migrate
python manage.py createsuperuser
```

Check your setup by starting a Web server on your local machine.

```python
python manage.py runserver
```

Begin by going to the `/landing` page.

```python
http://127.0.0.1:8000/landing
```

Click on the `Signup` link, or go to the `/signup` page directly.

```python
http://127.0.0.1:8000/signup
```

Enter your signup details.  A verification email will be sent to the email address you enter, so include an email address to which you have access (but not the superuser email you entered earlier).  If you don't see the email in your inbox, check your spam folder.

Once you have entered your signup information and submitted the form, open up a new tab in your browser and go to the `Django /admin`.  Click on `Signup codes` to see the newly issued code. A new `User` will have been created with the email address, but will not yet appear under `Verified users`.

Go to the inbox for the email address and click on the link in the verification email.  The `code` in the email should match that in the database.

Go back to the `Django /admin` and check that the `Signup code` has been removed and that your email address appears on the `Verified users` list.

Now, go back to the `Email Verified` page and click on the `Login` link, or go to the `/login` page directly.

```python
http://127.0.0.1:8000/login
```

Login with your credentials.  Go back to the `Django /admin` and click on `Tokens` to see your newly issued authorization token.

Go back to your `Home` page and click on the `Logout` button.  You will be returned to the `/landing` page.

You can also log in using your Google account both on the signup and login page. It has been implemented by using django-allauth library.
