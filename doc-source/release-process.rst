================
Release Process
================

New releases are created using a combination of `repo-helper`_ and `GitHub Actions`_.
To start you will need ``repo-helper`` installed:

.. prompt:: bash

	python3 -m pip install repo-helper --upgrade

Then ensure all changes have been committed_ or stashed_:

.. prompt:: bash

	git status

.. parsed-literal::

	On branch master
	Your branch is up-to-date with 'origin/master'.

	nothing to commit, working tree clean


The create a release using `repo-helper release`_:

.. prompt:: bash

	repo-helper release minor

Repleace ``minor`` with ``major`` or ``patch`` as appropriate.

Once the release has been created locally, push to GitHub. Ensure you push the tag too:

.. prompt:: bash

	git push
	git push --tags

Once the tests pass GitHub Actions will take care of building and uploading to PyPI_
and Anaconda_ (if enabled for the project).
You should keep an eye on the tests to ensure they pass.

The release will be automatcally copied to `GitHub Releases`_ within the next two days using OctoCheese_.

.. _repo-helper: https://docs.repo-helper.uk
.. _GitHub Actions: https://github.com/features/actions
.. _committed: https://git-scm.com/docs/git-commit
.. _stashed: https://git-scm.com/docs/git-stash
.. _repo-helper release: https://docs.repo-helper.uk/en/latest/usage/release.html
.. _PyPI: https://pypi.org/
.. _Anaconda: https://anaconda.org/domdfcoding/repo
.. _GitHub Releases: https://docs.github.com/en/github/administering-a-repository/about-releases
.. _OctoCheese: https://octocheese.readthedocs.io/en/latest/
