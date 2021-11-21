[Home](README.md)

<br>

# Permissions & Postgresql

<br>

## Readings from [Permissions](https://www.django-rest-framework.org/api-guide/permissions/)

<br>

### Oveerview

<br>

> Together with authentication and throttling, permissions determine whether a request should be granted or denied access.

> Permission checks are always run at the very start of the view, before any other code is allowed to proceed.

> Permission checks will typically use the authentication information in the `request.user` and `request.auth` properties to determine if the incoming request should be permitted.

<br>

### How permissions are determined

<br>

> Permissions in REST framework are always defined as a list of permission classes.

> Before running the main body of the view each permission in the list is checked.

> If any permission check fails an `exceptions.PermissionDenied`or `exceptions.NotAuthenticated` exception will be raised, and the main body of the view will not run.

<br>

- When the permissions checks fail either a "`403 Forbidden`" or a "`401 Unauthorized`" response will be returned, according to the following rules:
  - The request was successfully authenticated, but permission was denied. 
    - An `HTTP 403 Forbidden` response will be returned.
  - The request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers.
    - An `HTTP 403 Forbidden` response will be returned.
  - The request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers. 
    - An `HTTP 401 Unauthorized` response, with an appropriate WWW-Authenticate header will be returned.

<br>

### Object level permissions

<br>

> REST framework permissions also support object-level permissioning.

> Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.

> Object level permissions are run by REST framework's generic views when `.get_object()` is called.

> As with view level permissions, an `exceptions.PermissionDenied` exception will be raised if the user is not allowed to act on the given object.

> If you're writing your own views and want to enforce object level permissions, or if you override the `get_object` method on a generic view, then you'll need to explicitly call the `.check_object_permissions(request, obj)` method on the view at the point at which you've retrieved the object.

> For performance reasons the generic views will not automatically apply object level permissions to each instance in a queryset when returning a list of objects.

<br>

### Setting the permission policy

<br>

> The default permission policy may be set globally, using the `DEFAULT_PERMISSION_CLASSES` setting.

> You can also set the authentication policy on a per-view, or per-viewset basis, using the `APIView` class-based views.

> Provided they inherit from `rest_framework.permissions.BasePermission`, permissions can be composed using standard Python bitwise operators.

<br>

### API Reference

<br>

#### AllowAny

<br>

> The `AllowAny` permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.

<br>

#### IsAuthenticated

<br>

> The `IsAuthenticated` permission class will deny permission to any unauthenticated user, and allow permission otherwise.

<br>

#### IsAdminUser

<br>

> The `IsAdminUser` permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.

<br>

#### IsAuthenticatedOrReadOnly

<br>

> The `IsAuthenticatedOrReadOnly` will allow authenticated users to perform any request.

> Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; `GET`, `HEAD` or `OPTIONS`.

<br>

#### DjangoModelPermissions

<br>

> This permission class ties into Django's standard `django.contrib.auth` model permissions.

> This permission must only be applied to views that have a `.queryset` property or `get_queryset()` method.

> Authorization will only be granted if the user is authenticated and has the relevant model permissions assigned.

- `POST` requests require the user to have the add permission on the model.
- `PUT` and PATCH requests require the user to have the change permission on the model.
- `DELETE` requests require the user to have the delete permission on the mode.

> The default behaviour can also be overridden to support custom model permissions.

<br>

#### DjangoModelPermissionsOrAnonReadOnly

<br>

> Similar to `DjangoModelPermissions`, but also allows unauthenticated users to have read-only access to the API.

<br>

#### DjangoObjectPermissions

<br>

> This permission class ties into Django's standard object permissions framework that allows per-object permissions on models.

> In order to use this permission class, you'll also need to add a permission backend that supports object-level permissions, such as django-guardian.

> As with `DjangoModelPermissions`, this permission must only be applied to views that have a .queryset property or .get_queryset() method. Authorization will only be granted if the user is authenticated and has the relevant per-object permissions and relevant model permissions assigned.

<br>

### Custom permissions

<br>

- To implement a custom permission, override `BasePermission` and implement either, or both, of the following methods:
  - `.has_permission(self, request, view)`
  - `.has_object_permission(self, request, view, obj)`

<br>

> The methods should return `True` if the request should be granted access, and `False` otherwise.

> If you need to test if a request is a read operation or a write operation, you should check the request method against the constant `SAFE_METHODS`, which is a tuple containing '`GET`', '`OPTIONS`' and '`HEAD`'.

<br>

> Custom permissions will raise a `PermissionDenied` exception if the test fails.

> To change the error message associated with the exception, implement a message attribute directly on your custom permission.

> Otherwise the default_detail attribute from `PermissionDenied` will be used.

> Similarly, to change the code identifier associated with the exception, implement a code attribute directly on your custom permission - otherwise the `default_code` attribute from `PermissionDenied` will be used.

<br>

### Overview of access restriction methods

<br>

> REST framework offers three different methods to customize access restrictions on a case-by-case basis.

> These apply in different scenarios and have different effects and limitations.

- `queryset/get_queryset()`:
  - Limits the general visibility of existing objects from the database. The queryset limits which objects will be listed and which objects can be modified or deleted.
  - The `get_queryset()` method can apply different querysets based on the current action.
- `permission_classes/get_permissions()`:
  - General permission checks based on the current action, request and targeted object. Object level permissions can only be applied to retrieve, modify and deletion actions.
  - Permission checks for list and create will be applied to the entire object type.
- `serializer_class/get_serializer()`:
  - Instance level restrictions that apply to all objects on input and output. The serializer may have access to the request context.
  - The `get_serializer()` method can apply different serializers based on the current action.

<br>

### Third party packages

<br>

- DRF - Access Policy
- Composed Permissions
- REST Condition
- DRY Rest Permissions
- Django Rest Framework Roles
- Django REST Framework API Key
- Django Rest Framework Role Filters
- Django Rest Framework PSQ
