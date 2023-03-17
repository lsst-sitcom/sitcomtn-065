:tocdepth: 1

.. sectnum::

.. Metadata such as the title, authors, and description are set in metadata.yaml

.. TODO: Delete the note below before merging new content to the main branch.


.. note::

   **This technote is a work-in-progress.**

Checks the performance of the TMA under 3.5 degree random offsets tracking for 32 seconds (and back to original position) in the full range of azimuth and elevation (another az-el grid). 
In particular, we analyse the repeatability of a target.
Requirements that must be met are documented in LTS 103.

For the full analysis notebook see: https://nbviewer.org/github/estevesjh/ComScratchStuff/blob/summit2023/starTracker/slewSettleTests/LVV-T2732_analysis_jitter.ipynb

Executive Summary
================
The TMA RA and DEC repeatability precision for a single target. 

**Goal**: check the TMA sky error to repeat the same target multiple times.

**Method**: The precision is the standard deviation of (RA,DEC) - Mean(RA,DEC) for each snake and the overall sample. 
To be robust against outliers I use $\sigma_{68}$ as std metric.

**Main findings**:

- The overall coordinate dispersion is $\sigma_{68}(RA)=0.16$ arcsec and $\sigma_{68}(DEC)=0.15$ arcsec. 

- There is no significant trend of the sky precision with elevation or azimuth.

- For some snakes movements the rms error was higher than $0.2$ arcsec (required precision).

Sky Residual 
================
The overall sky for 510 exposures is presented below.

.. image:: /_static/jitter_histogram.png

Elevation And Azimuth
================
For each snake I show the dispersion on RA, DEC. 
There is no clear trend with elevation or azimuth.
However, there are some points higher than specified requirement.

.. image:: /_static/jitter_azalt.png


Add content here.
See the `reStructuredText Style Guide <https://developer.lsst.io/restructuredtext/style.html>`__ to learn how to create sections, links, images, tables, equations, and more.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
