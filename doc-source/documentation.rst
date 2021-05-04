================
Documentation
================

Most projects have documentation generated with Sphinx_ and hosted on ReadTheDocs_.

.. _Sphinx: https://www.sphinx-doc.org/en/master/
.. _ReadTheDocs: https://readthedocs.org/

The documentation source is located in the ``doc-source`` directory.
A local copy of the documentation can be built with ``tox``:

.. prompt:: bash

	tox -e docs

The built documentation can be found in the ``doc-soure/build/html`` directory.

.. TODO:: changing the documentation configuration
