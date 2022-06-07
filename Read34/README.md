# API Deployment

## Table Of Content

- [API Deployment](#api-deployment)
  - [Table Of Content](#table-of-content)
  - [Configuring Django Settings](#configuring-django-settings)
    - [Managing Django Settings: Issues](#managing-django-settings-issues)
    - [Setting Configuration: Different Approaches](#setting-configuration-different-approaches)
    - [Separate settings file for each environment](#separate-settings-file-for-each-environment)
    - [Environment variables](#environment-variables)
    - [12 Factors](#12-factors)
  - [SSH](#ssh)
    - [What is SSH](#what-is-ssh)
    - [How Does SSh Work](#how-does-ssh-work)
    - [Understanding Different Encryption](#understanding-different-encryption)
      - [Symmetric Encryption](#symmetric-encryption)
      - [Asymmetric Encryption](#asymmetric-encryption)
      - [Hashing](#hashing)


## Configuring Django Settings

This section is intended for engineers who use the Django framework.

### Managing Django Settings: Issues

*Different Environments.* Each environment can have its own specific settings (for example DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.

Sensitive data. You have `Secret_Key` in each Django project. On top of this, there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.

*Sharing settings between team members* You need a general approach to eliminate human error when working with the settings. For example, a developer may add a third-party app or some API integration and fail to add specific settings. On large (or even mid-size) projects, this can cause real issues.

*Django settings are a Python code.* This is a curse and a blessing at the same time. It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, settings.py can have a very tricky logic.

### Setting Configuration: Different Approaches

**settings_local.py**
This is the oldest method. I used it when I was configuring a Django project on a production server for the first time. I saw a lot of people use it back in the day, and I still see it now.

The basic idea of this method is to extend all environment-specific settings in the `settings_local.py` file, which is ignored by VCS. Here’s an example:

`settings.py` file:
```code
ALLOWED_HOSTS = ['example.com']
DEBUG=False
```

`settings_local.py` file:
```code
ALLOWED_HOSTS = ['localhost']
DEBUG = True
```

**Pros:**
* Secrets not in VCS.
**Cons:**
* `settings_local.py` is not in VCS, so you can lose some of your Django environment settings.
* The Django settings file is a Python code, so `settings_local.py` can have some non-obvious logic.
* You need to have `settings_local.example` (in VCS) to share the default configurations for developers.

### Separate settings file for each environment

This is an extension of the previous approach. It allows you to keep all configurations in VCS and to share default settings between developers.

In this case, you make a `settings` package with the following file structure:

```tree
settings/
   ├── __init__.py
   ├── base.py
   ├── ci.py
   ├── local.py
   ├── staging.py
   ├── production.py
   └── qa.py
```

settings/local.py:

```code
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
To run a project with a specific configuration, you need to set an additional parameter:

```code
python manage.py runserver --settings=settings.local
```

**Pros:**

- All environments are in VCS.
- It’s easy to share settings between developers.

**Cons:**

- You need to find a way to handle secret passwords and tokens.
- “Inheritance” of settings can be hard to trace and maintain.

### Environment variables

To solve the issue with sensitive data, you can use environment variables.

```code
import os


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

This is the simplest example using Python os.environ and it has several issues:

1- You need to handle KeyError exceptions.
2- You need to convert types manually (see DATABASE_PORT usage).

To fix KeyError, you can write your own custom wrapper. For example:

```import os

from django.core.exceptions import ImproperlyConfigured


def get_env_value(env_variable):
    try:
      	return os.environ[env_variable]
    except KeyError:
        error_msg = 'Set the {} environment variable'.format(var_name)
        raise ImproperlyConfigured(error_msg)


SECRET_KEY = get_env_value('SECRET_KEY')
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': get_env_value('DATABASE_NAME'),
        'HOST': get_env_value('DATABASE_HOST'),
        'PORT': int(get_env_value('DATABASE_PORT')),
    }
}
```

Also, you can set default values for this wrapper and add type conversion. But actually, there is no need to write this wrapper, because you can use a third-party library (we’ll talk about this later).

**Pros:**
* Configuration is separated from code.
* Environment parity – you have the same code for all environments.
* No inheritance in settings, and cleaner and more consistent code.
* There is a theoretical grounding for using environment variables – 12 Factors.
**Cons:**
* You need to handle sharing default config between developers.

### 12 Factors

12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud. It was created by Heroku, a well-known Cloud hosting provider.

As the name suggests, the collection consists of twelve parts:

1- Codebase
2- Dependencies
3- Config
4- Backing services
5- Build, release, run
6- Processes
7- Port binding
8- Concurrency
9- Disposability
10- Dev/prod parity
11- Logs
12- Admin processes

Each point describes a recommended way to implement a specific aspect of the project. Some of these points are covered by instruments like Django, Python, pip. Some are covered by design patterns or the infrastructure setup. In the context of this article, we are interested in one part: the Configuration.

Its main rule is to store configuration in the environment. Following this recommendation will give us strict separation of config from code.

You can read more on [12factor.net.](https://12factor.net/)

## SSH 

### What is SSH

SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.

SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

### How Does SSh Work

f you’re using Linux or Mac, then using SSH is very simple. If you use Windows, you will need to utilize an SSH client to open SSH connections. The most popular SSH client is PuTTY, which you [can learn more about here.](https://www.hostinger.com/tutorials/how-to-use-putty-ssh)

### Understanding Different Encryption

The significant advantage offered by SSH over its predecessors is the use of encryption to ensure a secure transfer of information between the host and the client. Host refers to the remote server you are trying to access, while the client is the computer you are using to access the host. There are three different encryption technologies used by SSH:

1- Symmetrical encryption
2- Asymmetrical encryption
3- Hashing

#### Symmetric Encryption

Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host. Effectively, anyone possessing the key can decrypt the message being transferred.![Symmentic](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/symmetric-encryption-ssh-tutorial.webp)


#### Asymmetric Encryption

Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. These two keys are known as the public key and the private key. Together, both these keys form a public-private key pair.
![Assyemantic](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/asymmetric-encryption.webp)

#### Hashing

One-way hashing is another form of cryptography used in Secure Shell Connections. One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted. They generate a unique value of a fixed length for each input that shows no clear trend which can be exploited. This makes them practically impossible to reverse. 
![Hashing](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/ssh-tutorial-hash.webp)