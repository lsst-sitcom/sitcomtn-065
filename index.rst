:tocdepth: 1

.. sectnum::

.. Metadata such as the title, authors, and description are set in metadata.yaml

.. TODO: Delete the note below before merging new content to the main branch.


.. note::

   **This technote is a work-in-progress.**

Checks the performance of the TMA under 3.5 degree random offsets tracking for 32 seconds (and back to original position) in the full range of azimuth and elevation (another az-el grid). 
In particular, we analyse the repeatability of a target.
Requirements that must be met are documented in LTS 103.

For the full analysis notebook see: 
https://nbviewer.org/github/estevesjh/ComScratchStuff/blob/summit2023/starTracker/slewSettleTests/LVV-T2732_analysis_repeatability.ipynb

Executive Summary
=============================================
**Goal**: Study the TMA (RA, DEC) repeatability precision for a single target. 

**Method**: The precision is the standard deviation of the sky residuals, (RA,DEC) - Target(RA,DEC). 
To be robust against outliers I use :math:`\sigma_{68}` as std metric.

**Main findings:**

- The overall coordinate dispersion is :math:`\sigma_{68}(RA)=0.16` arcsec and :math:`\sigma_{68}(DEC)=0.15` arcsec. 

- There is no significant trend of the sky precision with elevation or azimuth.

- For some snakes movements the rms error was higher than 0.2 arcsec (required precision).

Further tests should look at the dependence with elevation. 

Snake Description
================================================
For a given target (RA,DEC) acquire three images move 3.5 deg away acquire three more images, then slew back to the initial target.
Repeat the process five times. This exercise is called snake.

.. figure:: /_static/snake.png
    :name: fig-snake

    Fig. 1: A sample set of points with the center position and 5 points offset by 3.5 degrees in a random direction. Credits Elana Urbach.

The above circle illustrates the snake for a given target. 
The snake exercise was repeated for a grid of Az/Alt.

Residuals
================================================
The residual for each slew is:

.. math:: \delta RA = Ra - <Ra> 

The mean is taken over the three images acquired per slew.
The same opperation was applied for DEC.

.. figure:: /_static/residual_snake1.png
   :name: snake-sky-residual

   Fig. 3: Residual sky coordinates for one snake exercise. 

To compute the sky precision we compute the standard deviation of the sky residuals.

Results
================================================
The overall sky residual for 510 exposures is presented below.

.. figure:: /_static/jitter_histogram.png
   :name: overall-sky-residual

   Fig. 3: Residual sky distribution of single targets

The typical offset is :math:`\sigma_{68}(RA) = 16` arcsec and :math:`\sigma_{68}(DEC) = 15` arcsec. 
We see some outliers, probably they are sequences images that I mis-grouped. 

Elevation And Azimuth
================================================
For each snake I show the RA, DEC precision on a specified target.

There is no clear trend with elevation or azimuth.
However, there are some points higher than specified requirement.

.. figure:: /_static/jitter_azalt.png
   :name: residual-alt-az

   Fig. 4: Sky precision as a function of elevation and azimuth. 

In addition, we see a slight trend with elevation.
Further should probe this structure. 

.. Add content here.
.. See the `reStructuredText Style Guide <https://developer.lsst.io/restructuredtext/style.html>`__ to learn how to create sections, links, images, tables, equations, and more.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
