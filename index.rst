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
https://nbviewer.org/github/estevesjh/ComScratchStuff/blob/summit2023/starTracker/slewSettleTests/LVV-T2732_analysis_repeatability_report.ipynb?flush_cache=true

Executive Summary
=============================================
**Goal**: Study the TMA (RA, DEC) repeatability precision for a single target. 

**Method**: The precision is the standard deviation of the sky residuals, (RA,DEC) - Target(RA,DEC). 
To be robust against outliers I use :math:`\sigma_{68}` as std metric.

**Main findings:**

- The overall on-sky precision is :math:`\sigma_{68}(RA)=0.19` arcsec and :math:`\sigma_{68}(DEC)=0.20` arcsec. 
- The overall on-sky precision in local coordinates (Alt/Az) is :math:`\sigma_{68}(Az)=0.16` arcsec and :math:`\sigma_{68}(Alt)=0.24` arcsec. 
- There is no significant trend of the sky precision with elevation or azimuth.
- The pointing model can have some impact of the precision. 

3.5 Deg Offset Test
================================================
For a given target (RA,DEC) acquire three images move 3.5 deg away (random) acquire three more images, then slew back to the initial target.
Repeat the process five times. This exercise is called snake.

.. figure:: /_static/snake.png
    :name: fig-snake

    Fig. 1: A sample set of points with the center position and 5 points offset by 3.5 degrees in a random direction. Credits Elana Urbach.

The above circle illustrates the snake for a given target. 
The snake exercise was repeated for a grid of Az/Alt.

Data Description
================================================
The data analyzed here was taking in two different nights, 9th and 17th March.
The sequences number of each night were 600-1115 and 292-858,respectively. 
In total, we have 1051 exposures after discarding bad exposures.

The analysis was performed by joining both nights.
Also, plots for each night were generated and the results were quite similar.
To see analysis for a individual night see the nootebook.

Residuals
================================================
The residual for each slew is:

.. math:: \delta RA = Ra - <Ra> 

The mean is taken over the three images acquired per slew.
The same opperation was applied for DEC and the local coordinates Az/Alt. 

.. figure:: /_static/residual_snake1.png
   :name: snake-sky-residual

   Fig. 3: Residual sky coordinates for one snake exercise. 

To compute the sky precision we compute the standard deviation of the sky residuals.

Results
================================================
The overall sky residual for 1016 exposures is presented below. 
Less than 0.5 percent of the data were outliers that we discarded. 

.. figure:: /_static/radec_residual_histogram.png
   :name: overall-sky-residual

   Fig. 3: Residual RADEC sky distribution of single targets

The typical offset is :math:`\sigma_{68}(RA) = 19` arcsec and :math:`\sigma_{68}(DEC) = 20` arcsec. 


.. Below, we show the residual distribution in Az/Alt. 
.. .. figure:: /_static/azalt_residual_histogram.png
..    :name: overall-sky-residual

..    Fig. 4: Residual AzAlt sky distribution of single targets


.. The typical offset is :math:`\sigma_{68}(Az) = 16` arcsec and :math:`\sigma_{68}(Alt) = 24` arcsec. 
.. The offset in elevation is higher than azimuth. 
.. Note, that we lost about 2/3 of the data. 
.. Because of the TMA tracking 2/3 of the exposures had offsets higher than 30 arcsec. 

Elevation And Azimuth Dependence
================================================
For each snake I show the RA, DEC precision on a specified target.

There is no clear trend with elevation or azimuth.
However, there are some points higher than specified requirement.

.. figure:: /_static/scatter_radec_azalt.png
   :name: residual-alt-az

   Fig. 4: Sky precision RADEC as a function of elevation and azimuth. 

We note that DEC precision is consitenly higher than RA. 

.. .. figure:: /_static/jitter_azalt.png
..    :name: residual-alt-az

..    Fig. 4: Sky precision AzAlt as a function of elevation and azimuth. 

Pointing Model
================================================

The pointing model can introduce an error on the residuals.
The level of this effect depends on the tracking. 

.. Add content here.
.. See the `reStructuredText Style Guide <https://developer.lsst.io/restructuredtext/style.html>`__ to learn how to create sections, links, images, tables, equations, and more.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
