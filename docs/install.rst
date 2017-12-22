.. _install:

Download and Install
====================

Use ``pip install rpyc`` to fetch and install rpyc into the current
environment. If you don't want to bother with virtualenvs, consider using
``pip install --user rpyc``.

You can also manually download the latest releases of RPyC from the project's
`github page <https://github.com/tomerfiliba/rpyc/releases>`_ or
its `PyPI page <http://pypi.python.org/pypi/rpyc>`_.

You should always read the :ref:`change log <changelog>` before installing
new versions and always link your own applications against a specific major
version of rpyc!

Platforms and Interpreters
--------------------------
RPyC is a pure-python library, and as such can run on any architecture and
platform that runs python (or one of its other implementations), both 32-
and 64-bit. This is also true for a client and its server, which may run on
different architectures. The latest release supports:

* **Python** (CPython) 2.7-3.7
* May also work on py2.6
* May also work with **Jython** and **IronPython**. However, these are not
  primary concerns for me. Breakage may occur at any time.

Cross-Interpreter Compatibility
-------------------------------
You can

- connect a Python **2.x** interpreter to a Python **2.y** one, as long as you
  only use types/modules/features supported by both; and
- connect a Python **3.x** interpreter to a Python **3.y** one, under the same
  assumption.

However,

- you **cannot** connect a Python **2.x** interpreter **to a 3.y** one, or
  vice-versa. Trying to do so will results in all kinds of `strange exceptions
  <https://github.com/tomerfiliba/rpyc/issues/54>`_, so beware.

- **do not** try to **mix different versions of RPyC** (e.g., connecting
  a client machine running RPyC 3.1.0 to a server running RPyC 3.2.0). The
  wire-protocol has seen little changes since the release of RPyC 3.0, but the
  library itself has changed drastically. This might work, but don't count on it.

Development
===========

.. _mailing-list:

Mailing List
------------
There is an old `mailing list <http://groups.google.com/group/rpyc>`_ that may
contain useful information and that you should search before asking questions.
Nowadays however, do not count on getting any answers for new questions there.

Repository
----------
RPyC is developed on `github <http://github.com/tomerfiliba/rpyc>`_, where you
can always find the latest code or fork the project.

.. _bugs:

Bugs and Patches
----------------
We're using github's `issue tracker <http://github.com/tomerfiliba/rpyc/issues>`_
for bug reports, feature requests, and overall status.

Patches are accepted through github `pull requests <http://help.github.com/pull-requests/>`_.

.. _dependencies:

Dependencies
------------
The core of RPyC has no external dependencies, so you can use it out of the
box for "simple" use. However, RPyC integrates with some other projects to
provide more features, and if you wish to use any of those, you must install
them:

* `PyWin32 <http://sourceforge.net/projects/pywin32/files/pywin32/>`_ - Required
  for ``PipeStream`` on Windows

* SSH client - Required for :ref:`RPyC-over-SSH <ssh-tunneling>` (``ssh_connect``)

* `zlib for IronPython <https://bitbucket.org/jdhardy/ironpythonzlib>`_ - Required
  for IronPython prior to v2.7
