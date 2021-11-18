[Home](README.md)

<br>

# Django CRUD and Forms

<br>

## Readings from [Django Tutorial Part 9: Working with forms](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)

<br>

### Overview

<br>

> An HTML Form is a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server.

> Forms are a flexible mechanism for collecting user input because there are suitable widgets for entering many different types of data, including text boxes, checkboxes, radio buttons, date pickers and so on.

> Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.

> Working with forms can be complicated! Developers need to write HTML for the form, validate and properly sanitize entered data on the server (and possibly also in the browser), repost the form with error messages to inform users of any invalid fields, handle the data when it has successfully been submitted, and finally respond to the user in some way to indicate success.

> Django Forms take a lot of the work out of all these steps, by providing a framework that lets you define forms and their fields programmatically, and then use these objects to both generate the form HTML code and handle much of the validation and user interaction.

<br>

### HTML Forms

<br>

> The field's type attribute defines what sort of widget will be displayed.

> The `name` and `id` of the field are used to identify the field in JavaScript/CSS/HTML, while value defines the initial value for the field when it is first displayed.

> The matching team `label` is specified using the label tag, with a `for` field containing the id value of the associated `input`.

> The `submit` input will be displayed as a button (by default) that can be pressed by the user to upload the data in all the other input elements in the form to the server.

- The form attributes define the HTTP method used to send the data and the destination of the data on the server (`action`).
  - `action`: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
  - `method`: The HTTP method used to send the data: `post` or `get`.
    - The `POST` method should always be used if the data is going to result in a change to the server's database because this can be made more resistant to cross-site forgery request attacks.
    - The `GET` method should only be used for forms that don't change user data (e.g. a search form). It is recommended for when you want to be able to bookmark or share the URL.

> The role of the server is first to render the initial form state — either containing blank fields or pre-populated with initial values. After the user presses the submit button, the server will receive the form data with values from the web browser and must validate the information.

> If the form contains invalid data, the server should display the form again, this time with user-entered data in "valid" fields and messages to describe the problem for the invalid fields.

<br>

### Django form handling process

<br>

> The view gets a request, performs any actions required including reading data from the models, then generates and returns an HTML page (from a template, into which we pass a context containing the data to be displayed).

> What makes things more complicated is that the server also needs to be able to process data provided by the user, and redisplay the page if there are any errors.

- The main things that Django's form handling does are:
  - Display the default form the first time it is requested by the user.
    - The form may contain blank fields, or it may be pre-populated with initial values.
    - The form is referred to as unbound at this point, because it isn't associated with any user-entered data (though it may have initial values).
  - Receive data from a submit request and bind it to the form.
    - Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
  - Clean and validate the data.
    - Cleaning the data performs sanitization of the input (e.g. removing invalid characters that might be used to send malicious content to the server) and converts them into consistent Python types.
    - Validation checks that the values are appropriate for the field (e.g. are in the right date range, aren't too short or too long, etc.)
  - If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
  - If all data is valid, perform required actions (e.g. save the data, send an email, return the result of a search, upload a file, etc.)
  - Once all actions are complete, redirect the user to another page.

<br>

### Renew form using a Form and function view

<br>

- Form
  
> The Form class is the heart of Django's form handling system.

> It specifies the fields in the form, their layout, display widgets, labels, initial values, valid values, and (once validated) the error messages associated with invalid fields.

> The class also provides methods for rendering itself in templates using predefined formats (tables, lists, etc.) or for getting the value of any element (enabling fine-grained manual rendering).

<br>

- Declaring a Form

> The declaration syntax for a Form is very similar to that for declaring a Model, and shares the same field types (and some similar parameters).

> This makes sense because in both cases we need to ensure that each field handles the right types of data, is constrained to valid data, and has a description for display/documentation.

<br>

- Form fields

- The arguments that are common to most fields are listed below (these have sensible default values):
  - required
  - label
  - label_suffix
  - initial
  - widget
  - help_text
  - error_messages
  - validators
  - localize
  - disabled

<br>

- Validation

> Django provides numerous places where you can validate your data.

> The easiest way to validate a single field is to override the method `clean_<fieldname>()` for the field you want to check. 

> So for example, we can validate that entered renewal_date values are between now and 4 weeks by implementing `clean_renewal_date()` as shown below.

<br>

### URL configuration

<br>

> We can name our captured URL data "pk" anything we like, because we have complete control over the view function (we're not using a generic detail view class that expects parameters with a certain name).

> However, pk short for "primary key", is a reasonable convention to use!

<br>

### View

<br>

> As discussed in the Django form handling process above, the view has to render the default form when it is first called and then either re-render it with error messages if the data is invalid, or process the data and redirect to a new page if the data is valid.

> In order to perform these different actions, the view has to be able to know whether it is being called for the first time to render the default form, or a subsequent time to validate data.

> For forms that use a `POST` request to submit information to the server, the most common pattern is for the view to test against the `POST` request type (if `request.method` == '`POST`':) to identify form validation requests and `GET` (using an else condition) to identify the initial form creation request.

> If you want to submit your data using a `GET` request, then a typical approach for identifying whether this is the first or subsequent view invocation is to read the form data (e.g. to read a hidden value in the form).

<br>

- A number of other useful objects/methods used in the body of the view function:
  - get_object_or_404()
  - HttpResponseRedirect
  - reverse()
  - datetime

<br>

> After creating the form, we call render() to create the HTML page, specifying the template and a context that contains our form.

> However, if this is a `POST` request, then we create our form object and populate it with data from the request.

> The final step in the form-handling part of the view is to redirect to another page, usually a "success" page. In this case, we use HttpResponseRedirect and `reverse()` to redirect to the corresponding view.

<br>

### The template

<br>

>  First, we declare the form tags, specifying where the form is to be submitted (action) and the method for submitting the data (in this case an "`HTTP POST`") — if you recall the HTML Forms overview at the top of the page, an empty action as shown, means that the form data will be posted back to the current URL of the page (which is what we want!). 

> Inside the tags, we define the submit input, which a user can press to submit the data. The liquid tag added just inside the form tags is part of Django's cross-site forgery protection.