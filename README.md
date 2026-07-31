Create yourself one script:
a)  use a variable (type: string) for holding a path which is to say location where data grouped in files will be stored of a given hour of the day:  
C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\6\0
(July 6, 2026 hour 1; 
meta data (description of path):  
Parent:  July (month), 
Child1: (day) 6, 
Child2: (hour) 0 (early morning, or hour "one", first record or entry, eg., price, volume, change in Price from yesterday, for example for a set of stocks in a portfolio!)

The script contained in this repo. with full explication author presents below: 

PS C:\Users\edcon> cd "C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\6\0
-chage directory!  switch to this directory where we will need to import data 

Call this variable from another script which moves data into it (copying):

Copy-Item -Path C:\Users\edcon\Downloads\* -Include "* Jul 06 2026.csv"
note, subsequent hours are stored in separate files with extension (1), (2) etc

