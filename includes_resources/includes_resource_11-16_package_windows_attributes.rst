.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.

This resource has the following attributes:

.. list-table::
   :widths: 200 300
   :header-rows: 1

   * - Attribute
     - Description
   * - ``installer_type``
     - |type package_11-16_string| Possible values: ``msi``.

       .. note:: Starting with |chef client| version 12, this value is a symbol (``:msi``) and not a string.
   * - ``options``
     - |command options|
   * - ``provider``
     - Optional. |provider resource_parameter| |see providers|
   * - ``returns``
     - |returns| This code signals a successful ``:install`` action. Default value: ``0``.
   * - ``source``
     - Optional. |source resource package| Default value: the ``name`` of the resource block. |see syntax|
   * - ``timeout``
     - |timeout| Default value: ``600`` (seconds).








