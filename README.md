Django Gravatar
===============

django-gravatar is a Django application that exports template tags to convert
email addresses to Gravatar-stored avatars, as dynamically generated hyperlinks.

This repo is intended to have some customizations, like gravatar profile support and caching.
Go to end of doc to see some interesting coplementary info & links :)

By including the app, `django_gravatar`, in your settings module, you can
load a custom templatetags module, `gravatar_tags`, to generate a Gravatar URL
from an input of an email address and a set of optional parameters.

To load the custom tags into your template, include the following:

    {% load gravatar_tags %}

Currently, this will enable the following tags:

    {% gravatar_url <email> <params> %}
    {% gravatar_url <email> %}

Where `<email>` is either a string variable or a string literal of an email
address, and `<params>` is either an object or dictionary variable of the
following set of parameters:

* `size` -- corresponding to Gravatar parameter `s`, the value must be between
1 and 512, inclusive. The default is 80.
* `rating` -- corresponding to Gravatar parameter `r`, the value must be in
`('g', 'pg', 'r', 'x')`. The default is `'g'`.
* `default` -- corresponding to Gravatar parameter `d`, the value must be in
`('identicon', 'monsterid', 'wavatar', '404')` or a valid URI.
The default is nothing.

For `size` and `rating`, when the given value is already default (i.e., 80 or
`'g'`, respectively), it will be omitted in the generated URL parameters.

If no `<params>` argument is supplied, the defaults will be used (that is,
omitted to rely on Gravatar's default fallback values).

Example
=======

Besides the `django_gravatar` directory, where the app logic is that you should
include or point to in your project, this directory also includes a dummy project
harness to demonstrate and/or test the app.

To demonstrate the example harness:

    # from this directory
    $ python example/manage.py runserver --pythonpath='.' \
      --settings='example.settings'

Then browse to:

    http://localhost:8000/email/<some@email.address>

To run unit tests (one is included with the django_gravatar app), use the 
harness:

    # from this directory
    $ python example/manage.py test --pythonpath='.'

TODO
====

- Add profile support
- Add caching support
- Add some pre-validation to know if avatar/profile exists

Links
=====

Visit the main Mercurial [repository](http://bitbucket.org/santa4nt/django-gravatar)
at bitbucket.

Visit the original (not my) mirror Git [repository](http://github.com/santa4nt/django-gravatar)
at github.

Visit [DrMegahertz repo](http://github.com/DrMegahertz/django-gravatar/tree/cache) for some local file caching implemented.

Visit [Lance McNearney article](http://1l.to/md3/) to check some validation if is a valid gravatar.
