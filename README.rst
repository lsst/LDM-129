#######
LDM-129
#######

=====================================
Data Management Infrastructure Design
=====================================

This is a working repository for *LDM-129: Data Management
Infrastructure Design*.

* Read the living document on the web: https://ldm-129.lsst.io 
* Read the officially-approved document: https://ls.st/ldm-129

Working with this document
--------------------------

.. code::

   git clone git@github.com:lsst/LDM-129.git
   cd LDM-129
   pip install -r requirements.txt
   make html

The built site can be viewed by opening ``_build/html/index.html`` in
your web browser.

Whenever you push to ``master``, LSST the docs will build and host the
document at https://ldm-129.lsst.io

Editing metadata
----------------

Metadata, such as document version, title, date of last edit, and
authors, are maintained in the ``metadata.yaml`` file
