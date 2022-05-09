# class 27 - **Django Models**

## Overview

Django web applications access and manage data through Python objects referred to as models.
Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for di=ocumentation, label text for forms, etc.

> brief overview of how a model is defined and some of the more iimportant fields and field arguments.

### Model defintion 

Models are usually defined in an application's *model.py* file 

```python 
from django.db import models
from django.urls import reverse 

```

### Fields

A model can have an arbitrary number of fields, of any type-each one, represents a  column of data that we want to store in one of our database tables. Each database record(row) will consist of one of each field value.
Each database record (row) will consist of one of each field value. Let's look at the example seen below:

```python
my_field _name = models.CharField(max_length=20, help_text=`Enter field documentation`)
```

`my_field_name`, of type `models.CharField`- which means that this field will contain strings of alphanumeric characters.

* `max_length=20` - States that the maximum length of a value in this field is 20 characters.

* `help_text='Enter field doucmentation'` - helpful text that may be displayed in a form to help users understand how the field is used.

#### COMMON FIELD ARGUMENTS

* [**help_text**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#help-text): Provides a text label for HTML forms (e.g. in the admin site), as described above.

* [**verbose_name**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#verbose-name): A human-readable name for the field used in field labels.

* [**default**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#default): The default value for the field. This can be a value or a callable object, in which case the object will be called every time a new record is created.

* [**null**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#null): if `True,` Django will store blank values as `NULL` in the database for fields where this is approprciate (a `CharField` will instead store an empty string). The default is `False`

* [**blank**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#blank): If `True`, the field is allowed to be blank in your forms. The default is `False`, which means that Django's form validation will force you to enter a value.

* [**choices**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#choices):A group of choices for this field. If this is provided, the default corresponding form widget will be a select box with these choices instead of the standard text field.

#### COMMON FIELD TYPES

*  [**CharField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#django.db.models.CharField) is used to define short-to-mid sized fixed-length strings.

*  [**TextField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#django.db.models.TextField) is used for large arbitrary-length strings, You may specify a max_length for the field, but this is used only when the field is displayed in forms (it is not enforced at the database level).

*  [**IntegerField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#django.db.models.IntegerField) is a field for storing integer (whole number) values, and for validating entered values as integers in forms.

*  [**DataField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#datefield) and [**DateTimeField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#datetimefield) are used for storing/representing dates and date/time information (as Python `dateTime.date` in and `datetime.datetime` objects, respectively). These fields can additionally declare the (mutually exclusive) parameters `auto_now=True` (to set the field to the current date every time the model is saved), auto_now_add (to only set the date when the model is first created) , and default (to set a default date that can be overridden by the user).

*  [**EmailField**]()https://docs.djangoproject.com/en/4.0/ref/models/fields/#emailfield is used to store and validate email addresses.

*  [**FileField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#filefield) and **ImageField** are used to upload files and images respectively(the `ImageField` adds additional validation that the uploaded file is an image).

*  [**AutoField**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#autofield) is a special type of `IntegerField` that automatically increaments. A primary key of this type is automatically added to your model if you don't explicitly specify one.

*  [**ForeignKey**](https://docs.djangoproject.com/en/4.0/ref/models/fields/#foreignkey) is used to specify a one-to-many relationship to another database model. 

*  [**ManyToManyField **](https://docs.djangoproject.com/en/4.0/ref/models/fields/#manytomanyfield)is used to specify a many-to-many relationship (e.g. a book can have several genres, and each genre can contain several books). 