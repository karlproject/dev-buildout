=============================
Get Started Quickly With Karl
=============================

Check out the buildout from github::

  $ git clone git://github.com/karlproject/dev-buildout.git karl
  $ cd karl

Create a virtual environment and run the buildout::

  $ virtualenv -p python2.6 --no-site-packages .
  $ bin/python bootstrap.py
  $ bin/buildout

Karl is now built and ready to run.  Run Karl using Paste HTTP server in the
foreground::

  $ bin/karlserve serve

Visit the filesystem ZODB based test instance of Karl at::

  http://localhost:6543/fs

Default login and password are admin/admin.

Create the user and database for the PostgreSQL/Relstroage based instance of
Karl::

  $ createuser -P karltest
    (Enter 'test' for password.  Repeat.  Answer 'n' to next three questions.)
  $ createdb -O karltest karltest

Visit the Relstorage instance at::

  http://localhost:6543/pg

Both instances are 'vanilla' instances of Karl which do not use any
customization package. Most customers that are not OSI, going forward, will
not use any customization package. To make the pg instance use the 'osi'
customization package::

  $ bin/karlserve settings set pg package osi
  $ bin/karlserve serve (restart if already running)

To revert back to vanilla::

  $ bin/karlserve settings remove pg package

To hack on some source code::

  $ bin/develop co karl
  $ bin/buildout -No

Source code will now be in src/karl and src/karlserve.

Enjoy!
