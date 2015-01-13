:title: Proxy Settings
:description: How to set a HTTP Proxy for builder and docker

.. _proxy_settings:

Proxy Settings
===============

In some environments HTTP connections must pass through a HTTP Proxy, Deis supports Proxy by ``http_proxy``, ``https_proxy`` and ``no_proxy`` environment variables.

Configuring Proxy
-----------------

During the instalation just before run ``make discovery``, edit the end of the file ``contrib/coreos/user-data.example`` with your proxy settings:

.. code-block:: console

  - path: /etc/environment_proxy
    owner: core
    content: |
      HTTP_PROXY=http://proxy.example.com:3128
      HTTPS_PROXY=http://proxy.example.com:3128
      ALL_PROXY=http://proxy.example.com:3128
      NO_PROXY="127.0.0.1,localhost,.example.com"
      http_proxy=http://proxy.example.com:3128
      https_proxy=http://proxy.example.com:3128
      all_proxy=http://proxy.example.com:3128
      no_proxy="127.0.0.1,localhost,.example.com"


.. note::

    Proxy behavior depends on each program's implementation, some program may act differently.
    When using custom buildpacks make sure it respects those settings.
