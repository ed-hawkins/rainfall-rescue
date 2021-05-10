# rainfall-rescue

Data made openly available from the RainfallRescue.org project which used citizen scientist volunteers to transcribe >65,000 pages of monthly rainfall observations. All the original PDFs for these '10-year sheets' are available from the Met Office Digital Archives: https://digital.nmla.metoffice.gov.uk/SO_d383374a-91c3-4a7b-ba96-41b81cfb9d67/

In the DATA/ folder there is a different directory for each location which contains identified sheets of data for a particular decade from that location. The individual images are made available, along with the originally transcribed data and one or more concatenated series. Data filenames with 'ERROR_' at the start indicate that there was a disagreement or incorrect sum in one or more data columns which needed resolving. Filenames with 'MISFILED_' at the start indicate that this sheet was filed in the wrong decade and were often not transcribed completely. Some locations include multiple sheets per decade, indicating potentially different rain gauges being used.

The ALLSHEETS/ folder includes every transcribed sheet as a CSV file. The filenames for each location indicate which PDF file the original page came from. 

The POOR-LOCATIONS/ folder is similar to the DATA/ folder, but contains locations where the data is poor or sparse in time. The UNKNOWN-NGR/ folder contains locations where the data is good, but the location is too uncertain currently.

The SUMMARY-GRAPHICS/ and REGIONAL-TIMESERIES/ folders contain graphics summarising the locations where data is available (from DATA/) and the complete timeseries of regional rainfall variations across the UK.

The COMPOSITE-SERIES/ folder contains a few places where several locations can be combined to produce very long timeseries for a small area.

The LOCATION-SHEETS/ folder contains spreadsheets which have been used to identify the places and locations of the individual sheets.

[![DOI](https://zenodo.org/badge/261481817.svg)](https://zenodo.org/badge/latestdoi/261481817)

