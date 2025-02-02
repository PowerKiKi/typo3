.. include:: /Includes.rst.txt

=======================================================
Breaking: #98032 - Serializable Interface fully removed
=======================================================

See :issue:`98032`

Description
===========

The :php:`Serializable` interface has been deprecated, and is
slated for removal entirely in PHP 9. The preferred
serialization tool is the :php:`__serialize`/:php:`__unserialize`
method pair.

All serializable classes in TYPO3 core already implement
:php:`__serialize`/:php:`__unserialize`, which is automatically
used by PHP in place of :php:`Serializable`. The now-vestigial
:php:`Serializable` references have been removed.

Impact
======

Generally none, unless a text string of an object serialized in v10
or earlier (using :php:`Serializable`) is deserialized in v12, in
which case it will not deserialize correctly due to the different
string format used by :php:`Serializable`. That is extremely unlikely
to happen.

The use of :php:`Serializable` in extensions is already not recommended,
as it will be removed from PHP in version 9.

Affected Installations
======================

None.

Migration
=========

None needed.

.. index:: PHP-API, NotScanned, ext:core
