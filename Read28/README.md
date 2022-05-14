# Read28 - Django CRUD and Forms

## Django Forms

### Overview

An HTML Form is a group of one or more fields/widgets on a web page,
Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site requests forgery protection.

---

### HTML Form

First, a brief overview of HTML Forms. Consider a simple HTML form, with a single text field for entering the name of some "team", and its associated label:

!["form"](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_example_name_field.png)

```HTML
<form action="/team_name_url/" method="post">
    <label for="team_name">Enter name: </label>
    <input id="team_name" type="text" name="name_field" value="Default name for team.">
    <input type="submit" value="OK">
</form>
```

The submit input will be displayed as a button by default. This can be pressed to upload the data in all the other input elements in the form to the server (in this case, just the team_name field). The form attributes define the HTTP method used to send the data and the destination of the data on the server (action):

action: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
method: The HTTP method used to send the data: post or get.
The POST method should always be used if the data is going to result in a change to the server's database because it can be made more resistant to cross-site forgery request attacks.
The GET method should only be used for forms that don't change user data (for example, a search form). It is recommended when you want to be able to bookmark or share the URL.

---

### Django form handling process

Django's form handling uses all of the same techniques that we learned about in previous tutorials (for displaying information about our models): the view gets a request, performs any actions required including reading data from the models, then generates and returns an HTML page (from a template, into which we pass a context containing the data to be displayed). What makes things more complicated is that the server also needs to be able to process data provided by the user, and redisplay the page if there are any errors.

A process flowchart of how Django handles form requests is shown below, starting with a request for a page containing a form (shown in green).

!['handling-process'](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png)

Based on the diagram above, the main things that Django's form handling does are:

Display the default form the first time it is requested by the user.
The form may contain blank fields if you're creating a new record, or it may be pre-populated with initial values (for example, if you are changing a record, or have useful default initial values).
The form is referred to as unbound at this point because it isn't associated with any user-entered data (though it may have initial values).
Receive data from a submitted request and bind it to the form.
Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
Clean and validate the data.
Cleaning the data performs sanitization of the input fields, such as removing invalid characters that might be used to send malicious content to the server, and converting them into consistent Python types.
Validation checks that the values are appropriate for the field (for example, that they are in the right date range, aren't too short or too long, etc.)
If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
If all data is valid, perform required actions (such as save the data, send an email, return the result of a search, upload a file, and so on).
Once all actions are complete, redirect the user to another page.

---

## Django Templates

### Overview 
After we defined our models and created some initial library records to work with, it's time to write the code that presents that information to users. The first thing we need to do is determine what information we want to display on our pages and define the URLs to use for returning those resources. Then we'll create a URL mapper, views, and templates to display the pages.

The following diagram describes the main data flow, and the components required when handling HTTP requests and responses. As we already implemented the model, the main components we'll create are:

URL mappers to forward the supported URLs (and any information encoded in the URLs) to the appropriate view functions.
View functions to get the requested data from the models, create HTML pages that display the data, and return the pages to the user to view in the browser.
Templates to use when rendering data in the views.
!['CRUD'](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page/basic-django.png)

---

### Defining the resource URLs

As this version of LocalLibrary is essentially read-only for end-users, we just need to provide a landing page for the site (a home page), and pages that display lists and detailed views for books and authors.


The URLs that we'll need for our pages are:

catalog/ — The home (index) page.
catalog/books/ — A list of all books.
catalog/authors/ — A list of all authors.
catalog/book/<id> — The detail view for a particular book, with a field primary key of <id> (the default). For example, the URL for the third book added to the list will be /catalog/book/3.
catalog/author/<id> — The detailed view for the specific author with a primary key field. For example, the URL for the 11th author added to the list will be /catalog/author/11.
The first three URLs will return the index page, books list, and authors list. These URLs do not encode any additional information, and the queries that fetch data from the database will always be the same. However, the results that the queries return will depend on the contents of the database.
By contrast, the final two URLs will display detailed information about a specific book or author. These URLs encode the identity of the item to display (represented by the above). The URL mapper will extract the encoded information and pass it to the view, and the view will dynamically determine what information to get from the database. By encoding the information in the URL we will use a single set of URL mapping, a view, and a template to handle all books (or authors).

---

Note: With Django, you can construct your URLs however you require — you can encode information in the body of the URL as shown above, or include GET parameters in the URL, for example,/book/?id=6. Whichever approach you use, the URLs should be kept clean, logical, and readable, as recommended by the W3C. The Django documentation recommends encoding information in the body of the URL to achieve better URL design.

---

### Creating the index page

The first page we'll create is the index page (catalog/). The index page will include some static HTML, along with generated "counts" of different records in the database. To make this work we'll create a URL mapping, a view, and a template.

---

Note: It's worth paying a little extra attention to this section. Most of the information also applies to the other pages we'll create.

#### URL Mapping 

When we created the skeleton website, we updated the locallibrary/urls.py file to ensure that whenever a URL that starts with catalog/ is received, the URLConf module catalog. URLs will process the remaining substring.

The following code snippet from locallibrary/urls.py includes the catalog.urls module:

```python
urlpatterns += [
    path('catalog/', include('catalog.urls')),
]

```

urlpatterns += [
    path('catalog/', include('catalog.urls')),
]


We also created a placeholder file for the URLConf module, named /catalog/urls.py. Add the following lines to that file:

```python
urlpatterns = [
    path('', views.index, name='index'),
]

```

The path() function defines the following:

A URL pattern, which is an empty string: ''. We'll discuss URL patterns in detail when working on the other views.
A view function that will be called if the URL pattern is detected: views. index, which is the function named index() in the views.py file.

---
