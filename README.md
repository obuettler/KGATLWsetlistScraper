# KGATLWsetlistScraper
A simple webscraper to get all setlists of King Gizzard and the Lizard Wizard's 2019 world tour.

The setlists will be saved in a directory of lists in the following form

`{"city" :
  [{"date1": "date", "setlist": ["song1", "song2",...], "venue1": "venue"}]
  [{"date2": "date", "setlist": ["song1", "song2",...], "venue2": "venue"}]
  }`

The whole directory will then be saved at your preferred location as setlistCollection.py file and can be imported with

`import setlistCollection.py`

Don't forget to set your Path at the end of the script.


