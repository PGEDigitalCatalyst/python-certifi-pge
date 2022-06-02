Certifi: Python SSL Certificates
================================

Certifi provides Mozilla's carefully curated collection of Root Certificates for
validating the trustworthiness of SSL certificates while verifying the identity
of TLS hosts. It has been extracted from the `Requests`_ project.

Installation
------------

``certifi`` is available on PyPI. Simply install it with ``pip``::

    $ pip install certifi

Usage
-----

To reference the installed certificate authority (CA) bundle, you can use the
built-in function::

    >>> import certifi

    >>> certifi.where()
    '/usr/local/lib/python3.7/site-packages/certifi/cacert.pem'

Or from the command line::

    $ python -m certifi
    /usr/local/lib/python3.7/site-packages/certifi/cacert.pem

Enjoy!

1024-bit Root Certificates
~~~~~~~~~~~~~~~~~~~~~~~~~~

Browsers and certificate authorities have concluded that 1024-bit keys are
unacceptably weak for certificates, particularly root certificates. For this
reason, Mozilla has removed any weak (i.e. 1024-bit key) certificate from its
bundle, replacing it with an equivalent strong (i.e. 2048-bit or greater key)
certificate from the same CA. Because Mozilla removed these certificates from
its bundle, ``certifi`` removed them as well.

In previous versions, ``certifi`` provided the ``certifi.old_where()`` function
to intentionally re-add the 1024-bit roots back into your bundle. This was not
recommended in production and therefore was removed at the end of 2018.

.. _`Requests`: https://requests.readthedocs.io/en/master/

Addition/Removal of Certificates
--------------------------------

PG&E Certifi adds support for overriding the root certificate bundle using the
``CERT_PATH`` environment variable, for example:

    $ export CERT_PATH=~/etc/CombinedCA.cer
    $ python -c "import certifi; print(certifi.where())"
    /Users/K0SF/etc/CombinedCA.cer