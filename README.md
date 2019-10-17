Tornado CORS [![Build Status](https://travis-ci.org/globocom/tornado-cors.png?branch=master)](https://travis-ci.org/globocom/tornado-cors)
============

Makes it easier to add CORS support to tornado apps.

About Cross-Origin Resource Sharing (CORS)
------------------------------------------

- http://en.wikipedia.org/wiki/Cross-origin_resource_sharing
- http://www.w3.org/TR/cors/


Installing
----------

```
pip install tornado-cors
```

Using
-----

```
from tornado_cors import CorsMixin


class MyHandler(CorsMixin, RequestHandler):
    
    # Value for the Access-Control-Allow-Origin header.
    # Default: None (no header).
    CORS_ORIGIN = '*'
    
    # Value for the Access-Control-Allow-Headers header.
    # Default: None (no header).
    CORS_HEADERS = 'Content-Type'
    
    # Value for the Access-Control-Allow-Methods header.
    # Default: Methods defined in handler class.
    # None means no header.
    CORS_METHODS = 'POST'

    # Value for the Access-Control-Allow-Credentials header.
    # Default: None (no header).
    # None means no header.
    CORS_CREDENTIALS = True
    
    # Value for the Access-Control-Max-Age header.
    # Default: 86400.
    # None means no header.
    CORS_MAX_AGE = 21600

    # Value for the Access-Control-Expose-Headers header.
    # Default: None
    CORS_EXPOSE_HEADERS = 'Location, X-WP-TotalPages'
    
    ...
```

Advanced
--------

By default, CorsMixin defines "options" method using the decorator
"asynchronous" from "tornado.web".

If your project customizes this decorator for some purpose (eg. usage of
greenlets), CorsMixin allows such customization in options wrapper.

Usage:

```
# custom_wrapper was previously defined

from tornado_cors import custom_decorator
custom_decorator.wrapper = custom_wrapper

```

## License

Tornado CORS is licensed under the [MIT license](LICENSE).