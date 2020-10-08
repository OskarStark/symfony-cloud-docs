Memcached
=========

`Memcached`_ is a simple in-memory object store well-suited for application level
caching.

Both Memcached and Redis can be used for application caching. As a general
rule, Memcached is simpler and thus more widely supported while Redis is more
robust. We recommend using Redis if possible but Memcached is fully supported
if an application favors that cache service.

To use it in your application, add it to ``.symfony/services.yaml``:

.. code-block:: yaml

    memcached:
        # supported versions: 1.4, 1.5, 1.6
        type: memcached:1.6

And wire it in ``.symfony.cloud.yaml`` (don't forget to enable the
``memcached`` PHP extension):

.. code-block:: yaml

    relationships:
        cache: "memcached:memcached"

    runtime:
        extensions:
            - memcached

Environment Variables
---------------------

The configuration is exposed via the following environment variables (where
``CACHE`` is the upper-cased version of the key defined in the relationship
above):

* ``CACHE_HOST``
* ``CACHE_PORT``
* ``CACHE_IP``

.. _`Memcached`: https://en.wikipedia.org/wiki/Memcached
