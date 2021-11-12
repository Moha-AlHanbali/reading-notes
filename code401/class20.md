[Home](README.md)

<br>

# Intro to Django

<br>

## Readings from [Getting started with Django](https://www.djangoproject.com/start/)

<br>

### Object-relational mapper

<br>

#### Models

<br>

> A model is the single, definitive source of information about your data.

> It contains the essential fields and behaviors of the data you’re storing.

> Generally, each model maps to a single database table.

<br>

- The basics:
  - Each model is a Python class that subclasses django.db.models.Model.
  - Each a  ttribute of the model represents a database field.
  - With all of this, Django gives you an automatically-generated database-access API.

<br>

#### Using models

<br>

> Once you have defined your models, you need to tell Django you’re going to use those models.

> Do this by editing your settings file and changing the INSTALLED_APPS setting to add the name of the module that contains your models.py.

> When you add new apps to INSTALLED_APPS, be sure to run manage.py migrate, optionally making migrations for them first with manage.py makemigrations.

<br>

#### Fields

<br>

> The most important part of a model – and the only required part of a model – is the list of database fields it defines.

> Fields are specified by class attributes. Be careful not to choose field names that conflict with the models API like clean, save, or delete.

<br>

- Field types
  - The column type, which tells the database what kind of data to store `(e.g. INTEGER, VARCHAR, TEXT)`.
  - The default HTML widget to use when rendering a form field `(e.g. <input type="text">, <select>)`.
  - The minimal validation requirements, used in Django’s admin and in automatically-generated forms.

<br>

- Field options
  - Each field takes a certain set of field-specific arguments (documented in the model field reference).
  - There’s also a set of common arguments available to all field types. All are optional.

<br>

- Automatic primary key fields
  - By default, Django gives each model an auto-incrementing primary key with the type specified per app in AppConfig.default_auto_field or globally in the DEFAULT_AUTO_FIELD setting.

<br>

- Verbose field names
  - Each field type, except for ForeignKey, ManyToManyField and OneToOneField, takes an optional first positional argument – a verbose name. If the verbose name isn’t given, Django will automatically create it using the field’s attribute name, converting underscores to spaces.

<br>

- Relationships
  - Clearly, the power of relational databases lies in relating tables to each other. Django offers ways to define the three most common types of database relationships: many-to-one, many-to-many and one-to-one.

<br>

#### Meta options

<br>

> Give your model metadata by using an inner class Meta.

> Model metadata is “anything that’s not a field”, such as ordering options (ordering), database table name (db_table), or human-readable singular and plural names (verbose_name and verbose_name_plural).

> None are required, and adding class Meta to a model is completely optional.

<br>

- Model attributes
  - The most important attribute of a model is the Manager.
  - It’s the interface through which database query operations are provided to Django models and is used to retrieve the instances from the database.
  - If no custom Manager is defined, the default name is objects. Managers are only accessible via model classes, not the model instances.

<br>

- Model methods
  - Define custom methods on a model to add custom “row-level” functionality to your objects.
  - Whereas Manager methods are intended to do “table-wide” things, model methods should act on a particular model instance.

<br>

### URL dispatcher

<br>

#### Overview

<br>

> To design URLs for an app, you create a Python module informally called a URLconf (URL configuration). This module is pure Python code and is a mapping between URL path expressions to Python functions (your views).

> This mapping can be as short or as long as needed. It can reference other mappings. And, because it’s pure Python code, it can be constructed dynamically.

<br>

#### How Django processes a request

<br>

- When a user requests a page from your Django-powered site, this is the algorithm the system follows to determine which Python code to execute:
  - Django determines the root URLconf module to use. Ordinarily, this is the value of the ROOT_URLCONF setting, but if the incoming HttpRequest object has a urlconf attribute (set by middleware), its value will be used in place of the ROOT_URLCONF setting.
  - Django loads that Python module and looks for the variable urlpatterns. This should be a sequence of django.urls.path() and/or django.urls.re_path() instances.
  - Django runs through each URL pattern, in order, and stops at the first one that matches the requested URL, matching against path_info.
  - Once one of the URL patterns matches, Django imports and calls the given view, which is a Python function (or a class-based view). The view gets passed the following arguments:
    - An instance of HttpRequest.
    - If the matched URL pattern contained no named groups, then the matches from the regular expression are provided as positional arguments.
    - The keyword arguments are made up of any named parts matched by the path expression that are provided, overridden by any arguments specified in the optional kwargs argument to django.urls.path() or django.urls.re_path().
  - If no URL pattern matches, or if an exception is raised during any point in this process, Django invokes an appropriate error-handling view. See Error handling below.

<br>

#### Path converters

<br>

- The following path converters are available by default:
  - `str` - Matches any non-empty string, excluding the path separator, `'/'`. This is the default if a converter isn’t included in the expression.
  - `int` - Matches zero or any positive integer. Returns an `int`.
  - `slug` - Matches any slug string consisting of ASCII letters or numbers, plus the hyphen and underscore characters. For example, building-your-1st-django-site.
  - `uuid` - Matches a formatted UUID. To prevent multiple URLs from mapping to the same page, dashes must be included and letters must be lowercase.
  - `path` - Matches any non-empty string, including the path separator, `'/'`. This allows you to match against a complete URL path rather than a segment of a URL path as with `str`.

<br>

### Templates

<br>

> Being a web framework, Django needs a convenient way to generate HTML dynamically.

> The most common approach relies on templates.

> A template contains the static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted.

<br>

#### The Django template language

<br>

> A Django template is a text document or a Python string marked-up using the Django template language.

> Some constructs are recognized and interpreted by the template engine. The main ones are variables and tags.

> A template is rendered with a context. Rendering replaces variables with their values, which are looked up in the context, and executes tags. Everything else is output as is.

<br>

- Syntax
  - Variables
    - A variable outputs a value from the context, which is a dict-like object mapping keys to values.
  - Tags
    - Tags provide arbitrary logic in the rendering process `{% and %}`.
  - Filters
    - Filters transform the values of variables and tag arguments `{{ django|title }}`.
  - Comments
    - `{# this won't be rendered #}`.

<br>

### Forms

<br>

#### HTML forms

<br>

- `<input>` elements, a form must specify two things:
  - where: the URL to which the data corresponding to the user’s input should be returned
  - how: the HTTP method the data should be returned by

<br>

#### GET and POST

<br>

> Django’s login form is returned using the `POST` method, in which the browser bundles up the form data, encodes it for transmission, sends it to the server, and then receives back its response.

> `GET`, by contrast, bundles the submitted data into a string, and uses this to compose a URL. The URL contains the address where the data must be sent, as well as the data keys and values.

<br>

#### Django’s role in forms

<br>

- Django handles three distinct parts of the work involved in forms:
  - preparing and restructuring data to make it ready for rendering
  - creating HTML forms for the data
  - receiving and processing submitted forms and data from the client

<br>

#### Forms in Django

<br>

- The Django Form class

> At the heart of this system of components is Django’s Form class.

> In much the same way that a Django model describes the logical structure of an object, its behavior, and the way its parts are represented to us, a Form class describes a form and determines how it works and appears.

> In a similar way that a model class’s fields map to database fields, a form class’s fields map to HTML form `<input>` elements.

> (A ModelForm maps a model class’s fields to HTML form `<input>` elements via a Form; this is what the Django admin is based upon.)

<br>

#### Instantiating, processing, and rendering forms

<br>

- When rendering an object in Django, we generally:
  - get hold of it in the view (fetch it from the database, for example)
  - pass it to the template context
  - expand it to HTML markup using template variables

<br>

### User authentication in Django

<br>

#### Overview

<br>

> The Django authentication system handles both authentication and authorization.

> Briefly, authentication verifies a user is who they claim to be, and authorization determines what an authenticated user is allowed to do.

> Here the term authentication is used to refer to both tasks.

<br>

> Authentication support is bundled as a Django contrib module in `django.contrib.auth`.

> By default, the required configuration is already included in the settings.py generated by django-admin startproject, these consist of two items listed in your `INSTALLED_APPS` setting:

<br>

- Installation
  - `'django.contrib.auth'` contains the core of the authentication framework, and its default models.
  - `'django.contrib.contenttypes'` is the Django content type system, which allows permissions to be associated with models you create.

<br>

- And these items in your MIDDLEWARE setting:
  - `SessionMiddleware` manages sessions across requests.
  - `AuthenticationMiddleware` associates users with requests using sessions.

<br>

### The Django admin site

<br>

#### Overview

<br>

> The admin is enabled in the default project template used by `startproject`.

- If you’re not using the default project template, here are the requirements:
  - Add `'django.contrib.admin'` and its dependencies - `django.contrib.auth`, `django.contrib.contenttypes`, `django.contrib.messages`, and `django.contrib.sessions` - to your `INSTALLED_APPS` setting.
  - Configure a DjangoTemplates backend in your `TEMPLATES` setting with `django.template.context_processors.request`, `django.contrib.auth.context_processors.auth`, and `django.contrib.messages.context_processors.messages` in the '`context_processors`' option of `OPTIONS`.
  - If you’ve customized the `MIDDLEWARE` setting, `django.contrib.auth.middleware.AuthenticationMiddleware` and `django.contrib.messages.middleware.MessageMiddleware` must be included.
  - Hook the admin’s URLs into your `URLconf`.

<br>

### Internationalization and localization

<br>

#### Internationalization and localization

<br>

> The goal of internationalization and localization is to allow a single Web application to offer its content in languages and formats tailored to the audience.

- Essentially, Django does two things:
  - It allows developers and template authors to specify which parts of their apps should be translated or formatted for local languages and cultures.
  - It uses these hooks to localize Web apps for particular users according to their preferences.

<br>

### Security

<br>

#### Overbiew

<br>

- Django provides multiple protections against:
  - Clickjacking
  - Cross-site scripting
  - Cross Site Request Forgery (CSRF)
  - SQL injection
  - Remote code execution

<br>

## Readings from [How Django Works Behind the Scenes](https://wsvincent.com/how-django-works-behind-the-scenes/)

<br>

### Overview

<br>

> Django is a Python-based web framework used by millions of developers and billions of consumers through popular apps like Instagram.

> It is open source, meaning the code is available for free on Github and can be downloaded onto any developer’s computer and used alongside the official documentation.

> Django was originally developed at the Lawrence Journal-World newspaper by Adrian Holovaty, Simon Willison, and Jacob Kaplan-Moss.

<br>

- Almost all popular open source packages have some degree of funding involved, typically in one of three forms:
  - Corporate Sponsor
  - Solo 
  - Non-profit

<br>

### Django Software Foundation

<br>

> The `DSF` supports and maintains Django in a number of capacities.

> The largest expense, by far, is the Fellows Program, paid contractors who triage tickets, manage releases, and generally perform the unsexy but necessary work needed to keep Django on track.

<br>

### Technical Organization

<br>

> The `DSF` handles legal, financial, and administrative matters for Django. But there is a separate organizational structure for the technical team.

<br>

### Conclusion

<br>

> Django’s code is open source and available to all.

> Django’s organization is managed by a non-profit, the DSF, with a miniscule budget.

> And Django code is lead by a core team of volunteers, two paid Django Fellows, and a larger group of contributors.

> One of the best ways to become more involved in Django is to attend an annual conference and meet all the contributors in person.
