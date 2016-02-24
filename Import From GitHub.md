# Grab Data from GitHub

**Step 1: Load required packages**

~~~
library( RCurl )
~~~

**Step 2: Create an object for the URL where your data is stored**

Make sure to link to the "raw" version of the data. When you click on the dataset in GitHub, the "raw" option will be a toggle at the top right of the page.

~~~
url.faads <- "https://raw.githubusercontent.com/lecy/FAADS-NCCS-Crosswalk/master/Data/FAADS%20Demo%20Data.csv"
~~~

**Step 3: Use getURL from RCurl to download the file contents**

~~~
faads.sample <- getURL( url.faads, ssl.verifypeer = FALSE )
~~~

**Step 4: Let R know that the file is in .csv format so that it can create a data frame**

~~~
faads.sample <- read.csv(textConnection( faads.sample ), stringsAsFactors=FALSE )  
~~~

**Clean-Up**

~~~
rm( url.faads )
~~~
