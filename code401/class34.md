[Home](README.md)

<br>

# Authentication & Production Server

<br>

## Readings from [API Deployment](https://canvas.instructure.com/courses/3575698/discussion_topics/12740406)

<br>

### Managing Django Settings: Issues

<br>

- Different environments
  - Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.
- Sensitive data
  - You have `SECRET_KEY` in each Django project.
  - On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter.
  - This data cannot be stored in `VCS`.
- Sharing settings between team members
  - You need a general approach to eliminate human error when working with the settings.
  - For example, a developer may add a third-party app or some API integration and fail to add specific settings.
  - On large (or even mid-size) projects, this can cause real issues.
- Django settings are a Python code
  - This is a curse and a blessing at the same time.
  - It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, `settings.py` can have a very tricky logic.

<br>

### Setting Configuration: Different Approaches

<br>

#### settings_local.py

<br>

> The basic idea of this method is to extend all environment-specific settings in the `settings_local.py` file, which is ignored by `VCS`.

- Pros:
  - Secrets not in VCS.

- Cons:
  - `settings_local.py` is not in `VCS`, so you can lose some of your Django environment settings.
  - The Django settings file is a Python code, so `settings_local.py` can have some non-obvious logic.
  - You need to have `settings_local.example` (in `VCS`) to share the default configurations for developers.

```py

# settings.py file:

ALLOWED_HOSTS = ['example.com']
DEBUG = False
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'production_db',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db.example.com',
        'PORT': '5432',
        'OPTIONS': {
            'sslmode': 'require'
        }
    }
}

# settings_local.py file:

ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```
<br>

#### Separate settings file for each environment

<br>

> This is an extension of the previous approach. It allows you to keep all configurations in `VCS` and to share default settings between developers.

```py

# settings/local.py:

from .base import *


ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

<br>

- Pros:
  - All environments are in VCS.
  - It’s easy to share settings between developers.

- Cons:
  - You need to find a way to handle secret passwords and tokens.
  - “Inheritance” of settings can be hard to trace and maintain.

<br>

#### Environment variables

<br>

```py
import os

from django.core.exceptions import ImproperlyConfigured


def get_env_value(env_variable):
    try:
      	return os.environ[env_variable]
    except KeyError:
        error_msg = 'Set the {} environment variable'.format(var_name)
        raise ImproperlyConfigured(error_msg)

SECRET_KEY = os.environ['SECRET_KEY']
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ['DATABASE_NAME'],
        'HOST': os.environ['DATABASE_HOST'],
        'PORT': int(os.environ['DATABASE_PORT']),
    }
}
```
<br>

- Pros:
  - Configuration is separated from code.
  - Environment parity – you have the same code for all environments.
  - No inheritance in settings, and cleaner and more consistent code.
  - There is a theoretical grounding for using environment variables – 12 Factors.

<br>

- Cons:
  - You need to handle sharing default config between developers.

<br>

#### django-environ

<br>

> Writing code using os.environ could be tricky sometimes and require additional effort to handle errors. It’s better to use django-environ instead.

```py
settings.py:

import environ


root = environ.Path(__file__) - 3  # get root of the project
env = environ.Env()
environ.Env.read_env()  # reading .env file

SITE_ROOT = root()

DEBUG = env.bool('DEBUG', default=False)
TEMPLATE_DEBUG = DEBUG

DATABASES = {'default': env.db('DATABASE_URL')}

public_root = root.path('public/')
MEDIA_ROOT = public_root('media')
MEDIA_URL = env.str('MEDIA_URL', default='media/')
STATIC_ROOT = public_root('static')
STATIC_URL = env.str('STATIC_URL', default='static/')

SECRET_KEY = env.str('SECRET_KEY')

CACHES = {'default': env.cache('REDIS_CACHE_URL')}
```

<br>

```py
.env file:

DEBUG=True
DATABASE_URL=postgres://user:password@db.example.com:5432/production_db?sslmode=require
REDIS_CACHE_URL=redis://user:password@cache.example.com:6379/1
SECRET_KEY=Some-Autogenerated-Secret-Key
```

<br>

#### Setting Structure

<br>

```py
__init__.py file:

from .django import *       # All Django related settings
from .third_party import *  # Celery, Django REST Framework & other 3rd parties
from .project import *      # You custom settings
```

<br>

#### Naming Conventions

<br>

- Follow these simple rules for our custom (project) settings:
  - Give meaningful names to your settings.
  - Always use the prefix with the project name for your custom (project) settings.
  - Write descriptions for your settings in comments.

<br>

#### Django Settings: Best practices

<br>

- Keep settings in environment variables.
- Write default values for production configuration (excluding secret keys and tokens).
- Don’t hardcode sensitive settings, and don’t put them in VCS.
- Split settings into groups: Django, third-party, project.
- Follow naming conventions for custom (project) settings

<br>

<br>

## Readings from [How Does SSH Work](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

<br>

### What is SSH

<br>

> `SSH`, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet.

> The service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner.

> It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

<br>

### How Does SSH Work

<br>

> The `SSH` command consists of 3 distinct parts: `ssh {user}@{host}`.

> The `SSH` key command instructs your system that you want to open an encrypted Secure Shell Connection.

> `{user}` represents the account you want to access. For example, you may want to access the root user, which is basically synonymous for system administrator with complete rights to modify anything on the system.

> `{host}` refers to the computer you want to access. This can be an IP Address or a domain name.

<br>

### Understanding Different Encryption Techniques

<br>

> `Host` refers to the remote server you are trying to access, while the `client` is the computer you are using to access the host.

- There are three different encryption technologies used by `SSH`:
  - Symmetrical encryption
  - Asymmetrical encryption
  - Hashing.

<br>

#### Symmetric Encryption

<br>

> Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host.

> Symmetrical encryption is often called shared key or shared secret encryption.

> Effectively, any one possessing the key can decrypt the message being transferred.

> The process of creating a symmetric key is carried out by a key exchange algorithm.

> What makes this algorithm particularly secure is the fact that the key is never transmitted between the client and the host.

> Instead, the two computers share public pieces of data and then manipulate it to independently calculate the secret key.

<br>

### Asymmetric Encryption

<br>

> Asymmetrical encryption uses two separate keys for encryption and decryption.

> These two keys are known as the public key and the private key.

> Together, both these keys form a public-private key pair.

> The public key, as the name suggest is openly distributed and shared with all parties.

> While it is closely linked with the private key in terms of functionality, the private key cannot be mathematically computed from the public key.

> Unlike the general perception, asymmetrical encryption is not used to encrypt the entire `SSH` session.

> Instead, it is only used during the key exchange algorithm of symmetric encryption.

<br>

#### Hashing

<br>

> One-way hashing is another form of cryptography used in Secure Shell Connections.

> One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted.

> They generate a unique value of a fixed length for each input that shows no clear trend which can exploited.

> This makes them practically impossible to reverse.

> `SSH` uses hashes to verify the authenticity of messages.

> This is done using `HMACs`, or Hash-based Message Authentication Codes.

> This ensures that the command received is not tampered with in any way.

<br>

### How Does SSH Work with These Encryption Techniques

<br>

> The way `SSH` works is by making use of a client-server model to allow for authentication of two remote systems and encryption of the data that passes between them.

> `SSH` operates on TCP port 22 by default (though this can be changed if needed).

> The client must begin the `SSH` connection by initiating the `TCP` handshake with the server, ensuring a secured symmetric connection, verifying whether the identity displayed by the server match previous records (typically recorded in an RSA key store file), and presenting the required user credentials to authenticate the connection.

- There are two stages to establishing a connection: 
  - First both the systems must agree upon encryption standards to protect future communications. 
  - Second, the user must authenticate themselves. If the credentials match, then the user is granted access.

<br>

#### Session Encryption Negotiation

<br>

> the client has a similar matching pair of protocol and version, an agreement is reached and the connection is started with the accepted protocol. 

> Once this is established, the two parties use what is known as a Diffie-Hellman Key Exchange Algorithm to create a symmetrical key.

- Here is how the algorithm works at a very basic level:
  - Both the client and the server agree on a very large prime number, which of course does not have any factor in common. This prime number value is also known as the seed value.
  - Next, the two parties agree on a common encryption mechanism to generate another set of values by manipulating the seed values in a specific algorithmic manner. These mechanisms, also known as encryption generators, perform large operations on the seed. An example of such a generator is AES (Advanced Encryption Standard).
  - Both the parties independently generate another prime number. This is used as a secret private key for the interaction.
  - This newly generated private key, with the shared number and encryption algorithm (e.g. AES), is used to compute a public key which is distributed to the other computer.
  - The parties then use their personal private key, the other machine’s shared public key and the original prime number to create a final shared key. This key is independently computed by both computers but will create the same encryption key on both sides.
  - Now that both sides have a shared key, they can symmetrically encrypt the entire SSH session. The same key can be used to encrypt and decrypt messages (read: section on symmetrical encryption).

<br>

#### Authenticating the User

<br>

> The final stage before the user is granted access to the server is authenticating his/her credentials.

> The user is asked to enter the username, followed by the password.

> These credentials securely pass through the symmetrically encrypted tunnel, so there is no chance of them being captured by a third party.

> Although passwords are encrypted, it is still not recommended to use passwords for secure connections.