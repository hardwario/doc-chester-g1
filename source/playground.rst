##########
Playground
##########

.. topic:: Your Topic Title

   Subsequent indented lines comprise
   the body of the topic, and are
   interpreted as body environment elements.

what
   Definition lists associate a term with
   a definition.


:Authors:
    Tony J. (Tibs) Ibbs,
    David Goodger

:Version: ``TEST`` 1.0 of 2001/08/08
:Dedication: To my father.

.. sidebar:: Sidebar Title

 Subsequent indented lines comprise
 the body of the sidebar, and are
 interpreted as body elements.

.. glossary::

   environment
      A structure where information about all documents under the root is
      saved, and used for cross-referencing.  The environment is pickled
      after the parsing stage, so that successive runs only need to read
      and parse new and changed documents.

   source directory
      The directory which, including its subdirectories, contains all
      source files for one Sphinx project.

.. code-block:: json

   {"test": "value"}

.. warning:: Test

.. danger:: Test

.. hint:: Test

.. note:: Test

This is a normal text paragraph. The next paragraph is a code sample::

   It is not processed in any way, except
   that the indentation is removed.

   It can span multiple lines.

This is a normal text paragraph again.
