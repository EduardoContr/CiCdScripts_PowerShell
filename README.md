Create yourself one script:
a)  use a variable (type: string) for holding a path which is to say a location where data was stored as a grouped (files) such as companies which sell telecommunications products, will be stored of a given hour of the day:  
C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\6\0
(path shows:  July 6, 2026 hour 1; meta data (description of path):  
Parent:  July (month), 
Child1: (day) 6, 
Child2: (hour) 0 (early morning, or hour "one", first record or entry, eg., price, volume, change in Price from yesterday, for example for a set of stocks in a portfolio!)

The script contained in this repo. with full explication, the author, "Ed Contreras" presents below: 

PS C:\Users\edcon> cd "C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\6\0
-chage directory!  switch to this directory where we will be path to import data from, 

Call this variable from another script which moves data into it (copying):

Copy-Item -Path C:\Users\edcon\Downloads\* -Include "* Jul 06 2026.csv"
note, subsequent hours are stored in separate files with extension (1), (2) etc

..use M Language to do some transformations
Set a path where files are for that given day and hour to a variable:

In PowerBI select transform (Powerquery), then select source, new query, advanced editor:
[note at end of each hour or period choose the approriate stored value, hour1, hour2, hour3, which variable stores the local folder where the day's company info is stored by hour, updated by hour for as many hours as needed.  .. for this example we take opening, first and second hour..

let 
    vara = ("C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\30\0"),
    varb = ("C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\30\1"),
    varc = ("C:\Users\edcon\Documents\05data\powerb\watchlists\2026\July\30\2"),
    Source = Folder.Files(vara),
    #"Filtered Hidden Files1" = Table.SelectRows(Source, each [Attributes]?[Hidden]? <> true),
    #"Invoke Custom Function1" = Table.AddColumn(#"Filtered Hidden Files1", "Transform File (21)", each #"Transform File (21)"([Content])),
    #"Renamed Columns1" = Table.RenameColumns(#"Invoke Custom Function1", {"Name", "Source.Name"}),
    #"Removed Other Columns1" = Table.SelectColumns(#"Renamed Columns1", {"Source.Name", "Transform File (21)"}),
    #"Expanded Table Column1" = Table.ExpandTableColumn(#"Removed Other Columns1", "Transform File (21)", Table.ColumnNames(#"Transform File (21)"(#"Sample File (21)"))),
    #"Changed Type" = Table.TransformColumnTypes(#"Expanded Table Column1",{{"Source.Name", type text}, {"Symbol", type text}, {"Last Price", Currency.Type}, {"Change $", type number}, {"Change %", type number}, {"Bid", type text}, {"Ask", type text}, {"Day's Range", type text}, {"52 Week Range", type text}, {"Volume", type text}, {"Last Trade (ET)", type time}}),
...
#"Sorted Rows7" = Table.Sort(#"Replaced Value4",{{"Custom", Order.Ascending}})
in
    #"Sorted Rows7"

    
    
