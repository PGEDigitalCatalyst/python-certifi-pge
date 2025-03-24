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

.. _`Requests`: https://requests.readthedocs.io/en/master/

Addition/Removal of Certificates
--------------------------------

PG&E Certifi adds support for overriding the root certificate bundle using the
``CERT_PATH`` environment variable, for example::

    $ export CERT_PATH=~/etc/CombinedCA.cer
    $ python -c "import certifi; print(certifi.where())"
    /Users/K0SF/etc/CombinedCA.cer
