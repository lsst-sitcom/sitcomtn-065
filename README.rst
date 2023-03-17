.. image:: https://img.shields.io/badge/sitcomtn--065-lsst.io-brightgreen.svg
   :target: https://sitcomtn-065.lsst.io
.. image:: https://github.com/lsst-sitcom/sitcomtn-065/workflows/CI/badge.svg
   :target: https://github.com/lsst-sitcom/sitcomtn-065/actions/
..
  Uncomment this section and modify the DOI strings to include a Zenodo DOI badge in the README
  .. image:: https://zenodo.org/badge/doi/10.5281/zenodo.#####.svg
     :target: http://dx.doi.org/10.5281/zenodo.#####

############################################
TMA 3.5 degree offset repeatability analysis
############################################

SITCOMTN-065
============

Checks the performance of the TMA when it is subject to 3.5 degree offsets and then returns to the initial position. In particular, the repeatability of a specific target. Requirements are documented in LTS 103.

**Links:**

- Publication URL: https://sitcomtn-065.lsst.io
- Alternative editions: https://sitcomtn-065.lsst.io/v
- GitHub repository: https://github.com/lsst-sitcom/sitcomtn-065
- Build system: https://github.com/lsst-sitcom/sitcomtn-065/actions/


Build this technical note
=========================

You can clone this repository and build the technote locally with `Sphinx`_:

.. code-block:: bash

   git clone https://github.com/lsst-sitcom/sitcomtn-065
   cd sitcomtn-065
   pip install -r requirements.txt
   make html

.. note::

   In a Conda_ environment, ``pip install -r requirements.txt`` doesn't work as expected.
   Instead, ``pip`` install the packages listed in ``requirements.txt`` individually.

The built technote is located at ``_build/html/index.html``.

Editing this technical note
===========================

You can edit the ``index.rst`` file, which is a reStructuredText document.
The `DM reStructuredText Style Guide`_ is a good resource for how we write reStructuredText.

Remember that images and other types of assets should be stored in the ``_static/`` directory of this repository.
See ``_static/README.rst`` for more information.

The published technote at https://sitcomtn-065.lsst.io will be automatically rebuilt whenever you push your changes to the ``main`` branch on `GitHub <https://github.com/lsst-sitcom/sitcomtn-065>`_.

Updating metadata
=================

This technote's metadata is maintained in ``metadata.yaml``.
In this metadata you can edit the technote's title, authors, publication date, etc..
``metadata.yaml`` is self-documenting with inline comments.

Using the bibliographies
========================

The bibliography files in ``lsstbib/`` are copies from `lsst-texmf`_.
You can update them to the current `lsst-texmf`_ versions with::

   make refresh-bib

Add new bibliography items to the ``local.bib`` file in the root directory (and later add them to `lsst-texmf`_).

.. _Sphinx: http://sphinx-doc.org
.. _DM reStructuredText Style Guide: https://developer.lsst.io/restructuredtext/style.html
.. _this repo: ./index.rst
.. _Conda: http://conda.pydata.org/docs/
.. _lsst-texmf: https://lsst-texmf.lsst.io