=======================
Building from source
=======================

The recommended way to build from source is via tox_:

.. prompt:: bash

	tox -e build

As well as building the sdist and wheel this will check them for common errors,
such as missing files or potential rendering issues on PyPI_.

The output files will be in the ``dist`` directory.

If you wish, you may also use `pep517.build`_ or another :pep:`517`-compatible build tool.

.. _tox: https://tox.readthedocs.io
.. _PyPI: https://pypi.org/
.. _pep517.build: https://pypi.org/project/pep517/
