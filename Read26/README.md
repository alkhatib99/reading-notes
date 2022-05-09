# class 26 - **Django**

## What is Django?

Django is a Python-based web framework used by millions of developers and billions of consumers through popular apps like Instagram.
 It is open-source, (meaning the code is available for free on Github and can be downloaded onto any developer’s).

---

## Where did it come from?

Django was initially developed between 2003 and 2005 by a wen team who were responsibile for creating and maintaining newspaper websites. 

---

## What Django code looks like?

In a traditional data-driven website.

* A web application waits for HTTP requests from the web browser (or other client).
* When a request is received the application works out what is needed based on the URL and possibly information in POST data or GET data.
* Depending on what is required it may then read or write information from a database or perform other tasks required to satisfy the request.
* Then return a response to the web browser, often dynamically creating an HTML page for the browser to display by inserting the retrieved data into placeholders in an HTML template.

Django web applications typically group the code that handles each of these steps into separate files:

!["WRRC"](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction/basic-django.png)

* **Urls**: A URL mapper is used to redirect HTTP requests to the appropriate view based on the request URL.
  The URL mapper can also match particular patterns of strings or digits that appear in a URL and pass these to a view function as data.

* **View**: A view is a request handler function, which receives HTTP requests and returns HTTP responses. Views access the data needed to satisfy requests via models, and delegate the formatting of the response to templates.

* **Models**: Models are Python objects that define the structure of an application's data, and provide mechanisms to manage (add, modify, delete) and query records in the database.

* **Templates**: A template is a text file defining the structure or layout of a file (such as an HTML page), with placeholders used to represent actual content. A view can dynamically create an HTML page using an HTML template, populating it with data from a model. A template can be used to define the structure of any type of file; it doesn't have to be HTML!

---

## Getting Started With Django

### Install Django

Before you can use Django, you’ll need to install it.

[**Installation Guide**](https://docs.djangoproject.com/en/4.0/intro/install/)

---

### Write your first Django app

Installed Django already? Good. Now[* try this tutorial*](https://docs.djangoproject.com/en/4.0/intro/tutorial01/), which walks you through creating a basic poll application.

---
