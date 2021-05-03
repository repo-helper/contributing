===========
Style
===========

`formate <https://formate.readthedocs.io>`_ is used for code formatting.
It can be run manually via `pre-commit`_:

.. prompt:: bash

	pre-commit run formate -a


or, to run the complete autoformatting suite:

.. prompt:: bash

	pre-commit run -a


The general formatting rules are based on :pep:`8`, but with some differences:

.. _pre-commit: https://pre-commit.com/

Indentation
------------

Tabs are used instead of spaces.

Function signatures
-----------------------

Function signatures should be laid out like this:

.. code-block:: python

	def long_function_name(
        var_one: str,
        var_two: int,
        var_three: List[str],
        var_four: Dict[str, Any],
        ) -> Iterable[Tuple[str, int]]:
		...

with each argument on its own line, and the function name and return annotatons on separate lines.
Ensure to include the trailing comma after the last argument's annotation.
If the signature is short enough it may be placed on one line:

.. code-block:: python

	def function_name(var_one: str, var_two: int) -> bool:
		...

Functions should always be type annotated. ``*args`` and ``**kwargs`` need not be annotated, but other use of ``*`` (e.g. ``**children``) should be annotated.
Annotations may be omitted in tests, but are strongly encouraged.

Type Annotations
------------------

String annotations should be avoided.
Exceptions include :py:obj:`TypeVars <typing.TypeVar>` and where the object is imported using ``with TYPE_CHECKING:`` to resolve a circular dependency.
:pep:`563` (``from __future__ import annotations``) must not be used.

Type hints should be valid with the earliest supported Python version for the project, typically Python 3.6.
This includes the use of :class:`typing.Dict`\[...] etc. rather than :class:`dict`\[...], and importing certain objects from `typing-extensions`_.

.. _typing-extensions: https://pypi.org/project/typing-extensions/


Long :keyword:`if` Statements
-------------------------------

Long :keyword:`if` statements should be formatted with ``if (`` on one line, the conditions on the following lines and the ``):`` on the final line.
The operator should be at the start of the lines, not at the end.

Where possible such long statements should be avoided,
for example by splitting it into multiple if statements
or calculating the value in advance.


Long Sequences
------------------

Long sequences should be written with each element on its own line and a trailing comma after the last element:

.. code-block:: python

	# Bad
	my_list = [
	    1, 2, 3,
	    4, 5, 6
	    ]

	# Good
	my_list = [
	    1,
	    2,
	    3,
	    4,
	    5,
	    6,
	    ]


Maximum Line Length
-----------------------

Limit all lines to a maximum of 110 characters.
This also applies to docstrings, expect for long URLs in `explicit hyperlink targets`_.
Converting long, implicit targets to explicit targets improves the readability of the docstring.
This also applies to reStructuredText files in the documentation.

If the summary line of a docstring must exceed 110 characters the line must be wrapped and the docstring marked with ``# noqa: D400`` immediately after the closing quotes.

.. _explicit hyperlink targets: https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html#hyperlink-targets

Blank Lines
--------------

Blank lines must be used:

* After a file's top-level comments.
* Before a comment indicating a group of imports.
* After a group of imports.
* Immediately after a docstring.
* Immediately after a class, function or method signature if there is no docstring.

Blank lines must *not* be used:

* Between a class, function or method signature and its docstring.


Module Level Dunder Names
---------------------------

Module level "dunders" (i.e. names with two leading and two trailing underscores) such as ``__all__``, ``__author__``, ``__version__``, etc. should be placed after the module docstring and any imports.

They should be in the following order:

* ``__author__``
* ``__copyright__``
* ``__license__``
* ``__version__``
* ``__email__``
* <a blank line>
* ``__all__``

``__all__`` should always be included, even for modules with no public API.
Only include the names of public objects.
If the module has no public API write ``__all__ = ()``.
:py:obj:`TypeVars <typing.TypeVar>` may be included if it is necessary to document them, otherwise they should be omitted.

The `flake8-dunder-all`_ ``pre-commit`` hook can be used to automatically generate ``__all__``, although its output should be checked by hand as it can sometimes produce odd results.

.. _flake8-dunder-all: https://flake8-dunder-all.readthedocs.io/en/latest/

String Quotes
-----------------

Strings should use double quotes where possible, except for single characters and empty strings which should use single quotes.
Single quotes may be used where a double quote occurs within the string.

Triple double quotes (``"""``) must be used for docstrings.

Docstrings
-----------

The first line of the docstring must start a new line:

.. code-block:: python

	# Bad:

	"""Return a foobang
	"""

	# Good:

	"""
	Return a foobang
	"""

This rule is enforced even for short one-liner docstrings,
although those should be rare.

Each docstring must document the function's parameters.
For classes, the class docstring should document the arguments of ``__init__`` or ``__new__`` as appropriate.

``__init__`` should not have a docstring.
``__new__`` may have a docstring in certain crcumstances, expecially for :func:`namedtuples <collections.namedtuple>`.


Naming Style
--------------

Function and method names should be written in ``lower_case_with_underscores``.

Class names should use ``CamelCase``.
When using acronyms, capitalize all the letters of the acronym.
``HTTPServerError`` is better than ``HttpServerError``.

Private classes, functions and instance variables should be prefixed with a single underscore.
