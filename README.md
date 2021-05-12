# rainfall-rescue

Data made openly available from the RainfallRescue.org project which involved more than 16,000 citizen scientist volunteers transcribing >65,000 pages of monthly rainfall observations taken in the UK and Ireland, covering the period 1677-1960. Each sheet contains up to a decade of observations for a single location. 

All the original PDFs for these '10-year sheets' are available from the [Met Office Digital Archives](https://digital.nmla.metoffice.gov.uk/SO_d383374a-91c3-4a7b-ba96-41b81cfb9d67/) and JPG versions of each page are [also available](https://drive.google.com/drive/folders/17sIgINYhZoniEUr2jUNTp1h4A2bmPw1n). The transcription stage of the project was completed during March and April 2020.

In DATA/ there are >6000 folders for different locations, each of which contains the individual images for that location (as a PDF), along with the originally transcribed data (as individual CSV files) and one or more concatenated series (as CSV files with the same name as the folder). Significant rain guage moves result in different concatenated sequence files. The concatenated series have had several quality aspects examined, including identifiying the locations as precisely as possible, removing many estimated values and resolving disagreements in the transcribed data. These concatenated sheets are the recommended data to be used in subsequent analyses but the original transcribed sheets are made available to aid reproducibility. Please see the [schema](schema.md) page for more details on the file naming and structure.

The ALLSHEETS/ folder includes every transcribed sheet as a CSV file. The filenames for each location indicate which PDF file and page the original page came from. 

The POOR-LOCATIONS/ folder is similar to the DATA/ folder, but contains locations where the data is poor or sparse in time. The UNKNOWN-NGR/ folder contains locations where the data is good, but the location is currently too uncertain.

The SUMMARY-GRAPHICS/ and REGIONAL-TIMESERIES/ folders contain graphics summarising the locations where data is available (from DATA/) and the estimated timeseries of regional rainfall variations across the UK just using this data.

The COMPOSITE-SERIES/ folder contains a few places where several locations can be combined to produce very long timeseries for a small area.

The LOCATION-SHEETS/ folder contains spreadsheets which have been used to identify the places and locations of the individual sheets.

[![DOI](https://zenodo.org/badge/261481817.svg)](https://zenodo.org/badge/latestdoi/261481817)

