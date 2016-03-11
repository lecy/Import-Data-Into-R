# IMPORTING DATA FROM STATA - Foregin Package

In order to import data form diffrent versions of data manipulation software like Stata, SPSS, Minitab and similar there is "foregin" package available for R 
	
Package can support only specified versions of each software. For stata it would be versions 5–12. default file format for Stata 13, format-115, is substantially different from those for Stata 5–12.
	
		### Stata uses similar command inputs as R, although more user friendly. In order to summarize data from a file, user would enter "summarize" on the command screen and hit enter. 
		### In order to regress variables from the file, user would enter command: regress name.variable1 name.variable2
	
## Reading Stata files with read.dta function example
	
```
library( foreign )

read.dta( file, 
	       convert.dates = TRUE, 
	       convert.factors = TRUE,
	       missing.type = FALSE, 
	       convert.underscore = FALSE, 
	       warn.missing.labels = TRUE  )

	### file 				         a filename or URL as a character string.
	### convert.factors	     Use Stata value labels to create factors
	### missing.type		     store information about different types of missing data
	### convert.underscore	 Convert "_" in Stata variable names to "." in R names
	### warn.missing.labels	 Warn if a variable is specified with value labels and those value labels are not present 
	
```



	

## IMPORTING DATA FROM STATA - Memisc Package

Another way to import Stata or SPSS files is through using "memisc" package
	
Data are actually imported by ‘translating’ an importer file into a data.set using as.data.set or subset.The importer mechanism is more flexible and extensible than read.spss and read.dta of pack- age "foreign", as most of the parsing of the file headers is done in R. It is also adapted to efficiently load large data sets. Most importantly, importer objects support the labels, missing.values, and descriptions, provided by this package.
	
In this packager we would use importers function 
	
```
Stata.file(file)

	###  Arguments
  #### x				     an object that inherits from class "importer".
  #### file			     character string
  #### columns.file	 character string; the path to an SPSS/PSPP syntax file with a DATA LIST FIXED statement
  #### varlab.file	 character string; the path to an SPSS/PSPP syntax file with a VARIABLE LABELS statement
  #### codes.file		 character string; the path to an SPSS/PSPP syntax file with a VALUE LABELS statement
  #### missval.file	 character string; the path to an SPSS/PSPP syntax file with a MISSING VALUES statement
```
