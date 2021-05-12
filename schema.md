# Data File Schema

## Preamble

The dataset contains two types of data file - *source files* and *combined files*. Source files contain the transcriptions of the original 10 year rainfall sheets. Combined files contain the concatenated results from the source files for each identified location.

### Format

The text encoding of the data files is utf-8, with an optional byte order mark. The data files are in csv format with one row per line, and each row divided into fields separated by a comma delimiter. The number of fields per row (the number of columns) is constant within each file. However, the schema is more complicated than that of a conventional csv file, and is described in detail in the following sections.

### Range notation

For the purposes of describing the schema a csv file is considered like a spreadsheet, with ranges of cells given using A1 notation. For example the value in the first row and second column of the csv data is referred to as being in cell A2. The range A3:B7 refers to the block of cells whose upper-left corner is in cell A3 and whose lower-right corner is in cell B7. The range G2: refers to the block of cells whose upper-left corner is in cell G2, and whose lower-right corner is the cell in the last row and last column of the sheet.

### Data types

The following data types are used in the schema.

| name | Description |
| ---- | ---- |
| blank | Indicates the absence of a value. Equivalent to an empty string. |
| string | A string of text |
| integer | A positive whole number |
| float | A floating point number |
| nan | [Not a Number](https://en.wikipedia.org/wiki/NaN) |

Where a value may take more than one type, this is indicated by separating with a vertical bar. For example a value that can either be a float or blank would have the type 'float|blank'.

## Grid references

The grid references are usually given on the [GB OS grid](https://britishnationalgrid.uk), either with 6 digits, 8 digits or 10 digits following the two letter grid code. Stations in the Republic of Ireland use the [Irish grid reference system](https://en.wikipedia.org/wiki/Irish_grid_reference_system) with an additional 'I' letter at the start. Some locations in Northern Ireland use the GB grid and some use the Irish grid.

## Source files

### Naming

The source files names usually start with TYRain_, followed by two years separated by a hyphen which denote the decade for which the data represents. This is followed by either a series of letters or numbers which denote with of the [original PDF files](https://digital.nmla.metoffice.gov.uk/SO_d383374a-91c3-4a7b-ba96-41b81cfb9d67/) the sheet is contained in. This is followed by the page number of that PDF. 

Some of the source files start with ERROR_ - these are sheets for which there has either been disagreement in the original transcriptions, or an identified issue with the data, usually that a set of twelve months does not add up to the transcribed annual total. Some source files start with MISFILED_ which indicates that the page from the PDF was for a different decade than the PDF name indicated. These have been poorly transcribed due to original transcription process.

### Shape

The source csv files each contain 20 rows, and a variable number of columns. Each file can be divided into two groups of rows - *metadata* and *data*.

### Metadata

Rows 1-3 contain the sheet metadata. Each value occupies a single cell. All metadata values may be blank.

| Range | Name | Description | Type | Unit |
| ---- | ---- | ---- | ---- | ---- |
| A1   | LOCATION_NAME | Name of location | string\|blank | |
| B2   | GRID_REFERENCE | UK or Irish grid reference | string\|blank |
| D2   | LONGITUDE | WSG84 longitude | float\|nan\|blank | degrees |
| F2   | LATITUDE | WSG84 latitude | float\|nan\|blank | degrees |
| H2   | ELEVATION | Elevation | integer\|blank | foot |
| B3   | STATION_NUMBER | Station number | string\|blank | |

### Data

Rows 5-20 contain the main data table. Row 5 contains the column year headings, starting in cell B5 at START_YEAR (e.g. 1870) and ending at END_YEAR (e.g. 1910). The heading years are contiguous between START_YEAR and END_YEAR. The column containing END_YEAR (denoted EYC below) should be taken as the last column containing data. The data occupy the range B6:(EYC)20.

| Range | Name | Description | Type | Unit |
| ---- | ---- | ---- | ---- | ---- |
| B5:(EYC)5   | YEAR_HEADINGS | Year headings | integer | |
| B6:(EYC)6   | JANUARY_ROW | Rainfall amounts for January | float\|blank | inch |
| B7:(EYC)7   | FEBRUARY_ROW | Rainfall amounts for February | float\|blank | inch |
| B8:(EYC)8   | MARCH_ROW | Rainfall amounts for March | float\|blank | inch |
| B9:(EYC)9   | APRIL_ROW | Rainfall amounts for April | float\|blank | inch |
| B10:(EYC)10 | MAY_ROW | Rainfall amounts for May | float\|blank | inch |
| B11:(EYC)11 | JUNE_ROW | Rainfall amounts for June | float\|blank | inch |
| B12:(EYC)12 | JULY_ROW | Rainfall amounts for July | float\|blank | inch |
| B13:(EYC)13 | AUGUST_ROW | Rainfall amounts for August | float\|blank | inch |
| B14:(EYC)14 | SEPTEMBER_ROW | Rainfall amounts for September | float\|blank | inch |
| B15:(EYC)15 | OCTOBER_ROW | Rainfall amounts for October | float\|blank | inch |
| B16:(EYC)16 | NOVEMBER_ROW | Rainfall amounts for November | float\|blank | inch |
| B17:(EYC)17 | DECEMBER_ROW | Rainfall amounts for December | float\|blank | inch |
| B18:(EYC)18 | TOTAL_ROW | Annual total rainfall, as transcribed | float\|blank | inch |
| B19:(EYC)19 | CALCULATED_TOTAL_ROW | Annual total rainfall calculated from sum of transcribed values | float\|blank | inch |
| B20:(EYC)20 | DIFFERENCE_ROW | Difference between transcribed and calculated annual total rainfall | float\|nan\|blank | inch |

## Combined files

### Naming

All the combined files start with the same string as the folder name. If there is only a single combined file then it will be the folder name followed by '.csv'. Many folders represent more than one rain gauge, or a rain gauge was moved during the sequence. Additional combined files end with '-X.csv' where X is a value from 2 upwards. 

In addition, some folders contain combined files for which the data is either very limited, duplicates or questionable data. These have additional text strings before the '.csv'. These should not be used in any further analysis unless the issues with them have been understood.

### Shape

The combined csv files each contain a variable number of rows and columns. Each file can be divided into three groups of rows - *metadata*, *data* and *comments*.

### Metadata

Rows 1-3 contain the sheet metadata. Each value occupies a single cell. Other than LOCATION_NAME, all other metadata values may be blank.

| Range | Name | Description | Type | Unit |
| ---- | ---- | ---- | ---- | ---- |
| A1   | LOCATION_NAME | Name of location | string | |
| B2   | GRID_REFERENCE | UK or Irish grid reference | string\|blank |
| D2   | LONGITUDE | WSG84 longitude | float\|blank | degrees |
| F2   | LATITUDE | WSG84 latitude | float\|blank | degrees |
| H2   | ELEVATION | Elevation | integer\|blank | foot |
| B3   | STATION_NUMBER | Station number | string\|blank | |

### Data

Rows 5-18 contain the main data table. Row 5 contains the column year headings, starting in cell B5 at START_YEAR (e.g. 1870) and ending at END_YEAR (e.g. 1910). The heading years are contiguous between START_YEAR and END_YEAR. The column containing END_YEAR (denoted EYC below) should be taken as the last column containing data. The data occupy the range B6:(EYC)18.

| Range | Name | Description | Type | Unit |
| ---- | ---- | ---- | ---- | ---- |
| B5:(EYC)5   | YEAR_HEADINGS | Year headings | integer | |
| B6:(EYC)6   | JANUARY_ROW | Rainfall amounts for January | float\|blank | inch |
| B7:(EYC)7   | FEBRUARY_ROW | Rainfall amounts for February | float\|blank | inch |
| B8:(EYC)8   | MARCH_ROW | Rainfall amounts for March | float\|blank | inch |
| B9:(EYC)9   | APRIL_ROW | Rainfall amounts for April | float\|blank | inch |
| B10:(EYC)10 | MAY_ROW | Rainfall amounts for May | float\|blank | inch |
| B11:(EYC)11 | JUNE_ROW | Rainfall amounts for June | float\|blank | inch |
| B12:(EYC)12 | JULY_ROW | Rainfall amounts for July | float\|blank | inch |
| B13:(EYC)13 | AUGUST_ROW | Rainfall amounts for August | float\|blank | inch |
| B14:(EYC)14 | SEPTEMBER_ROW | Rainfall amounts for September | float\|blank | inch |
| B15:(EYC)15 | OCTOBER_ROW | Rainfall amounts for October | float\|blank | inch |
| B16:(EYC)16 | NOVEMBER_ROW | Rainfall amounts for November | float\|blank | inch |
| B17:(EYC)17 | DECEMBER_ROW | Rainfall amounts for December | float\|blank | inch |
| B18:(EYC)18 | TOTAL_ROW | Annual total rainfall, as transcribed | float\|blank | inch |

### Comments

Rows 19- contain comments left by the concatenator. They are unstructured, and may span an arbitrary number of rows and columns.

The comments may contain information about the observer, where they lived, comments on the original sheets, or station moves. They may also contain remarks about which values have been edited to ensure that the sum of the months add up to the annual totals. Some contain the acronym IDR which stands for 'input difference resolved'. 

| Range | Name | Description | Type | Unit |
| ---- | ---- | ---- | ---- | ---- |
| A19:   | COMMENTS | Comments | string | |
