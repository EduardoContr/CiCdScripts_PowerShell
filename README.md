Create yourself one script to create a variable (string) holding a path for the desired location of data such as a given hour of the day:  July 6, 2026 hour 1
Parent:  July (month), Child1: (day) 6, Child2: (hour) 0 (premarket or hour "one", first record or reading for price, volume, change in Price from yesterday, for example).

PS C:\Users\edcon> cd "C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\6\0

Call this variable from another script which moves data into it (copying):

Copy-Item -Path C:\Users\edcon\Downloads\* -Include "* Jul 06 2026.csv"
