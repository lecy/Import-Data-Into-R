# Load Data Files from Dropbox

Dropbox is an easy way to store and share files. If you want to share R code with colleagues, but not send large data files back and fourth, you can link to files stored in your Dropbox account. This is a good option if the files are sensitive, so you don't want to post them to a public account like GitHub.

If you right-click on a file in a Dropbox folder it will give you the option to create a public link to the file:

![alt text](http://www.soundsupport.biz/wp-content/uploads/2012/04/Screen-Shot-2014-10-06-at-4.21.40-PM.png)

Grab this link, but note that it cannot be used directly. You need to change the _dl=0_ to _dl=1_ for it to work. Then you are off to the races:


```{r}

# link provided by Dropbox:
# https://www.dropbox.com/s/gi5xia1b2r11bez/311%20Calls%20for%20Disorderly%20Youth.csv?dl=0

# change dl=0 to dl=1

dat <- read.csv( "https://www.dropbox.com/s/gi5xia1b2r11bez/311%20Calls%20for%20Disorderly%20Youth.csv?dl=1" )

```

If you would rather download a local copy:

```{r}

download.file("https://www.dropbox.com/s/gi5xia1b2r11bez/311%20Calls%20for%20Disorderly%20Youth.csv?dl=1", 
              "problemyutes.csv" )

dat <- read.csv( "problemyutes.csv" )

```



If you want to keep things clean, just download the files into a subdirectory and remove when done:


```

dir.create( "dropbox" )

download.file("https://www.dropbox.com/s/gi5xia1b2r11bez/311%20Calls%20for%20Disorderly%20Youth.csv?dl=1", 
              "./dropbox/problemyutes.csv" )

dat2 <- read.csv( "./dropbox/problemyutes.csv" )


# deletes downloaded file

file.remove( "./dropbox/problemyutes.csv" )


# deletes entire directory

unlink( "dropbox", recursive = TRUE )

```

