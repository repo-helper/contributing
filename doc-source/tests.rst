=========
Testing
=========

tox_ is used to automate testing, with the tests themselves run with pytest_.

Start by installing ``tox`` and `tox-envlist`_ if you don't already have them:

.. prompt:: bash

	python3 -m pip install tox tox-envlist


To run tests for a specific Python version, such as Python 3.6:

.. prompt:: bash

	tox -e py36


or, to test all Python versions:

.. prompt:: bash

	tox -n test


.. _pytest: https://docs.pytest.org
.. _tox: https://tox.readthedocs.io
.. _tox-envlist: https://tox-envlist.readthedocs.io


Type Annotations
-------------------

Type annotations are checked using mypy_:

.. prompt:: bash

	tox -e mypy


.. _mypy: https://mypy.readthedocs.io/en/stable/


Code Quality
-------------------

Run flake8_ with ``tox`` to ensure your changes don't introduce any issues:

.. prompt:: bash

	tox -e flake8


.. _flake8: https://flake8.pycqa.org/en/latest/


Coverage
------------

.. TODO:: this section
.. TODO:: coverage measurements in pull requests
