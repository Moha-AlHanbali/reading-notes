[Home](README.md)

<br>

# Django Models

<br>

## Readings from [Django Tutorial Part 3: Using models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

<br>

### Overview

<br>

> Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc..

<br>

### Designing the LocalLibrary models

<br>

> When designing your models it makes sense to have separate models for every "object" (a group of related information). In this case, the obvious objects are books, book instances, and authors.

> You might also want to use models to represent selection-list options (e.g. like a drop down list of choices), rather than hard coding the choices into the website itself — this is recommended when all the options aren't known up front or may change.

> Once we've decided on our models and field, we need to think about the relationships. Django allows you to define relationships that are one to one `(OneToOneField)`, one to many `(ForeignKey)` and many to many `(ManyToManyField)`.

<br>

### Model primer

<br>

> Models are usually defined in an application's models.py file. They are implemented as subclasses of d`jango.db.models.Model`, and can include fields, methods and metadata.

> The code fragment below shows a "typical" model, named MyModelName.

> A model can have an arbitrary number of fields, of any type — each one represents a column of data that we want to store in one of our database tables.

> Each database record (row) will consist of one of each field value

> The field types are assigned using specific classes, which determine the type of record that is used to store the data in the database, along with validation criteria to be used when values are received from an HTML form (i.e. what constitutes a valid value).

> The field types can also take arguments that further specify how the field is stored or can be used.

<br>

- Common field arguments
  - help_text
  - verbose_name
  - default
  - null
  - blank
  - choices
  - primary_key

- Common field types
  - CharField
  - TextField
  - IntegerField
  - DateField and  DateTimeField
  - EmailField
  - FileField and ImageField
  - AutoField
  - ForeignKey
  - ManyToManyField

<br>

- Metadata

> You can declare model-level metadata for your Model by declaring class Meta

> One of the most useful features of this metadata is to control the default ordering of records returned when you query the model type.

<br>

- Methods

> Minimally, in every model you should define the standard Python class method `__str__()` to return a human-readable string for each object.

> This string is used to represent individual records in the administration site (and anywhere else you need to refer to a model instance). Often this will return a title or name field from the model.

> Another common method to include in Django models is` get_absolute_url()`, which returns a URL for displaying individual model records on the website (if you define this method then Django will automatically add a "View on Site" button to the model's record editing screens in the Admin site).

<br>

### Model management

<br>

> To create a record you can define an instance of the model and then call `save()`.

<br>

- Searching for records

> You can search for records that match certain criteria using the model's objects attribute (provided by the base class).

> We can get all records for a model as a QuerySet, using `objects.all()`.

> The QuerySet is an iterable object, meaning that it contains a number of objects that we can iterate/loop through.

> Django's `filter()` method allows us to filter the returned QuerySet to match a specified text or numeric field against particular criteria.

<br>

### Defining the LocalLibrary Models

<br>

> The boilerplate at the top of the page imports the models module, which contains the model base class `models.Model` that our models will inherit from.

<br>

### Re-run the database migrations

<br>

> All your models have now been created. Now re-run your database migrations to add them to your database.

<br>

## Readings from [Django Tutorial Part 4: Django admin site](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)

<br>

### Overview

<br>

> The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records.

> This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data.

> All the configuration required to include the admin application in your website was done automatically when you created the skeleton project (for information about actual dependencies needed.

> As a result, all you must do to add your models to the admin application is to register them.

<br>

### Registering models 

<br>

> First, open `admin.py` in the application.

> It currently looks like this — note that it already imports `django.contrib.admin`.

> Register the models by copying the following text into the bottom of the file.

> This code imports the models and then calls admin.site.register to register each of them.

<br>

### Creating a superuser

<br>

> In order to log into the admin site, we need a user account with Staff status enabled.

> In order to view and create records we also need this user to have permissions to manage all our objects.

>  You can create a "superuser" account that has full access to the site and all needed permissions using `manage.py`.

> Call the following command, in the same directory as `manage.py`, to create the superuser.

> You will be prompted to enter a username, email address, and strong password.

> `python3 manage.py createsuperuser`.

<br>

### Logging in and using the site

<br>

> To login to the site, open the /admin URL `(http://127.0.0.1:8000/admin`) and enter your new superuser userid and password credentials.

> You can also directly click the Add link next to each model to start creating a record of that type.

> Enter values for the fields. You can create new authors or genres by pressing the + button next to the respective fields (or select existing values from the lists if you've already created them).

> When you're done you can press SAVE, Save and add another, or Save and continue editing to save the record.

> The edit page is almost identical to the "Add" page.

> The main differences are the page title and the addition of Delete, HISTORY and VIEW ON SITE buttons (this last button appears because we defined the `get_absolute_url()` method in our model.

