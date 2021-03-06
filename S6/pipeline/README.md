# S6D Pipeline Configuration files

This directory contains the necessary PyCBC workflow configuration files to
reproduce the S6D Big Dog result, as well as the original ihope configuration
file as reference.

## s6d_lowmass_ihope.ini ##

This file is the ihope configuration file used for the final S6D runs documented on the [S6 low-mass re-run page](https://www.lsc-group.phys.uwm.edu/ligovirgo/cbcnote/S6Plan/101104075619AnalysisS6ABC%20low%20mass%20re-runs). The specific file came from <file://sugar.phy.syr.edu/home/spxiwh/S6/all_sky/S6_reruns/S6d_chunk3/968543943-971622087/s6d_lowmass_ihope.ini>

## s6_run_pycbc_er8_pre_release.ini ##

The configuration file is designed as a rerun over the bigdog analysis period. It uses the up to date PyCBC code and HDF5 coincidence code.

To generate a workflow to run the analysis from the latest version of the ini files:

 1. Make a new directory for running the analysis and cd into it
 2. Generate the workflow with the command
```
pycbc_make_coinc_search_workflow --workflow-name s6d_chunk3 --output-dir output \
--config-files \
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-config/download/master/S6/pipeline/s6_run_pycbc_er8_pre_release.ini \
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-config/download/master/S6/pipeline/executables.ini \
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-config/download/master/S6/pipeline/injections.ini \
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-config/download/master/S6/pipeline/data_S6.ini \
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-config/download/master/S6/pipeline/gps_times_s6d_big_dog_two_weeks.ini \
--config-overrides \
"results_page:output-path:${HOME}/public_html/s6/s6d-big-dog-weeks"
```
changing the output-path for the results page as appropriate.

For production runs replace the executables.ini line with

```
https://code.pycbc.phy.syr.edu/ligo-cbc/pycbc-software/download/master/v1.2.0/x86_64/composer_xe_2015.0.090/executables.ini \
```

### Some differences between original S6 run and this one

 1.  exact-match coincidence
 2.  vastly increased PSD samples (15 -> 253)
 3.  higher density injections, and different injection sets