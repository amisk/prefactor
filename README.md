# prefactor
## The LOFAR pre-facet calibration pipeline.

Parsets for the genericpipeline that do the first calibration of LOFAR data. Originally in order
to prepare said data for the Factor facet calibration (https://github.com/lofar-astron/factor), but
also useful if you don't plan to run Factor.

It includes:
* applying Ionospheric RM corrections
* clock-TEC separation with transfer of clock from the calibrator to the target
* some flagging and averaging of amplitude solutions
* grouping of subbands by actual frequency
* speed and disk usage improvements by optimized usage of NDPPP
* (optional) wide-band cleaning in Initial-Subtract
* diagnostic plots
* at least some documentation on the [wiki pages](https://github.com/lofar-astron/prefactor/wiki)

The documentation can be found on the GitHub wiki pages: https://github.com/lofar-astron/prefactor/wiki

There are several pipeline parsets in this repository:
* Pre-Facet-Calibrator.parset : The calibrator part of the "standard" pre-facet calibration pipeline.
* Pre-Facet-Target.parset : The target part of the "standard" pre-facet calibration pipeline.
* Pre-Facet-Cal.parset : One parset calling first the calibrator and then the target pipelines. This is deprecated, please have a look at the [pipeline description](https://github.com/lofar-astron/prefactor/wiki/Documentation%3A-Pipelines#pre-facet-cal)
* Initial-Subtract-Fast.parset : A pipeline that generates full FoV images and subtracts the sky-models from the visibilities. (Needed for facet-calibration.)
* Initial-Subtract-IDG.parset : Same as Initial-Subtract.parset, but uses the image domain gridder (IDG) in WSClean
* Initial-Subtract-IDG-LowMemory.parset : Same as Initial-Subtract.parset, but uses the image domain gridder (IDG) in WSClean for high-res imaging
* Initial-Subtract-Deep.parset : Same as Initial-Subtract.parset, but it does only one image of the full bandwidth instead of imaging the bands separately.

Software requirements:
* the full "offline" LOFAR software installation version >= 3.1
* LoSoTo (version >= 2.0 -- see https://github.com/revoltek/losoto)
* LSMTool (see https://github.com/darafferty/LSMTool)
* RMextract (see https://github.com/maaijke/RMextract)
* Python matplotlib
* WSClean (for Initial-Subtract)
  * for Initial-Subtract-Fast.parset : version >= 2.5
  * for Initial-Subtract-IDG(-LowMemory).parset, WSClean must be compiled with IDG support
  * see https://sourceforge.net/projects/wsclean/
* APLpy (for Initial-Subtract)

The Pre-Facet-Calibration pipeline and its scripts where developed by:
* Martin Hardcastle <mjh somewhere extragalactic.info>
* George Heald <heald somewhere astron.nl>
* Andreas Horneffer <ahorneffer somewhere mpifr-bonn.mpg.de>
* Soumyajit Mandal <mandal somewhere strw.leidenuniv.nl>
* David Rafferty <drafferty somewhere hs.uni-hamburg.de>
* Carole Roskowinski <carosko gmail.com>
* Jose Sabater Montes <jsm somewhere iaa.es>
* Timothy Shimwell <shimwell somewhere strw.leidenuniv.nl>
* Sarrvesh Sridhar <sarrvesh somewhere astro.rug.nl>
* Reinout van Weeren <rvanweeren somewhere cfa.harvard.edu>
* Wendy Williams <wwilliams somewhere strw.leidenuniv.nl>

With special thanks to Stefan Froehlich <s.froehlich somewhere fz-juelich.de> for developing the
genericpipeline.

The procedure is also mostly described in these papers:
* van Weeren, R. J., Williams, W. L., Hardcastle, M. J., et al. 2016, ApJS, 223, 2
* Williams, W. L., van Weeren, R. J., Röttgering, H. J. A., et al. 2016, MNRAS,
460, 2385


