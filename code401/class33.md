[Home](README.md)

<br>

# Authentication & Production Server

<br>

## Readings from [Introduction to JSON Web Tokens](https://jwt.io/introduction/)

<br>

### What is JSON Web Token?

<br>

> JSON Web Token (`JWT`) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

> This information can be verified and trusted because it is digitally signed.

> JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using `RSA` or `ECDSA`.

> Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens.

> Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties.

<br>

### When should you use JSON Web Tokens?

<br>

- `Authorization`
  - This is the most common scenario for using JWT.
  - Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.
  - Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.

- `Information Exchange`
  - JSON Web Tokens are a good way of securely transmitting information between parties.
  - Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are.
  - Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

<br>

### What is the JSON Web Token structure?

<br>

- In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:
  - Header
  - Payload
  - Signature

<br>

- Header

> The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

<br>

- Payload

> The second part of the token is the payload, which contains the claims.

>Claims are statements about an entity (typically, the user) and additional data.

> There are three types of claims: registered, public, and private claims.

<br>

- `Registered claims` 

> These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. 

> Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.

<br>

- `Public claims` 

> These can be defined at will by those using JWTs.

>  But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.

<br>

- `Private claims`

> These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

<br>

- `Signature`

> To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

<br>

- `Putting all together`

> The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.

<br>

### How do JSON Web Tokens work?

<br>

> In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned.

> Since tokens are credentials, great care must be taken to prevent security issues.

> Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the `Bearer schema`.

<br>

- If the token is sent in the Authorization header, Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.
  - The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows.
  - When the authorization is granted, the authorization server returns an access token to the application.
  - The application uses the access token to access a protected resource (like an API).

<br>

### Why should we use JSON Web Tokens?

<br>

> As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML.

> This makes JWT a good choice to be passed in HTML and HTTP environments.

> Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC algorithm.

<br>

## Readings from [How to Use JWT Authentication with Django REST Framework](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)

<br>

### How JWT Works?

<br>

> The JWT is acquired by exchanging an username + password for an access token and an refresh token.

> The access token is usually short-lived (expires in 5 min or so, can be customized though).

> The refresh token lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an authentication session. After it expires, you need a full login with username + password again.

> It’s a security feature and also it’s because the JWT holds a little bit more information. If you look closely the example I gave above, you will see the token is composed by three parts `xxxxx.yyyyy.zzzzz`.

> Those are three distinctive parts that compose a JWT `header.payload.signature`.

<br>

### Installation & Setup

<br>

- settings.py

```py
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```

<br>

- urls.py

```py
from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Your URLs...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
```

<br>

### Usage

<br>

> I will be using HTTPie to consume the API endpoints via the terminal. But you can also use cURL (readily available in many OS) to try things out locally.

- Obtain Token

> First step is to authenticate and obtain the token. The endpoint is /api/token/ and it only accepts POST requests. `http post http://127.0.0.1:8000/api/token/ username=vitor password=123`

> After that you are going to store both the access token and the refresh token on the client side, usually in the localStorage.

> In order to access the protected views on the backend (i.e., the API endpoints that require authentication), you should include the access token in the header of all requests.

<br>

- Refresh Token

> To get a new access token, you should use the refresh token endpoint `/api/token/refresh/` posting the refresh token:

<br>

### What’s The Point of The Refresh Token?

<br>

> At first glance the refresh token may look pointless, but in fact it is necessary to make sure the user still have the correct permissions.

> If your access token have a long expire time, it may take longer to update the information associated with the token.

> That’s because the authentication check is done by cryptographic means, instead of querying the database and verifying the data.

> So some information is sort of cached.

<br>

## Readings from [Django Runserver Is Not Your Production Server](https://vsupalov.com/django-runserver-in-production/)

<br>

### Overview

<br>

> So the server started with runserver is not guaranteed to be performant (it’s very slow), and it hasn’t been built with security concerns in mind.

> Not a good fit for production use.

<br>

### A Production Stack

<br>

> A production setup usually consists of multiple components, each designed and built to be really good at one specific thing.

> When a request arrives at your server, it should be passed to a dedicated web server.

> If the request is not for a static file, but should be processed by your application, the webserver is configured to pass this request to the next component.

> It gets those fancy requests and uses them to construct Python objects which are usable by Django.

> WSGI is a specification which people agreed on, which describe how that happens.

<br>

### How Does Django Fit In?

<br>

> Django app does not actually run as you would think a server would - waiting for requests and reacting to them.

> Django project provides a `uwsgi.py` file, which contains a function to be called by the application server.

> This function gets a Python object representing the incoming request.

> This function calls code, and produces a response object which is passed to the WSGI server.

> There the response is translated into a `HTTP` response and is passed back to the web server, which finally delivers it to the user.
