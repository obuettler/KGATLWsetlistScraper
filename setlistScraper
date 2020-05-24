"""
setlistScraper.py
some code to get all the setlists from King Gizzard's 2019 tour
"""

import requests
import bs4
import os
import pprint

#initiate dictionary
setlistCollection = {}

for i in range(1,7): #there are 6 pages, so I use range(1,7) to iterate through all of them
    WorldTourURL = f"https://www.setlist.fm/search?artist=23de1823&page={i}&query=tour:%28World+Tour+%E2%80%9819%29"
    res = requests.get(WorldTourURL)
    soup = bs4.BeautifulSoup(res.content, "html.parser")
    gigsOnPage = soup.select("h2 > a")

    gigURL = []

    for x in range(len(gigsOnPage)):
        gigURL.append(gigsOnPage[x].get("href"))

    for url in gigURL:
        res = requests.get(f"https://www.setlist.fm/{url}")
        soup = bs4.BeautifulSoup(res.content, "html.parser")

        date = soup.select("li > span > em")[0].text[:-8]

        venue = soup.select("h1 span > span")
        venueCityCountry = venue[0].text
        venueCityCountryList = venueCityCountry.split(", ")
        venue = venueCityCountryList[0]
        city = venueCityCountryList[1]

        songTitels = soup.select(".songLabel")
        howMany = len(songTitels)
        setlist = []

        for x in range(howMany):
            setlist.append(songTitels[x].text)
        print(f"On {date}, they did a concert in {city} at {venue} where they played setlist {setlist}")

        event = {}
        event["venue"] = venue
        event["date"] = date
        event["setlist"] = setlist
        
        print("Current event saved - adding it to the main dictionary now...")
            
        setlistCollection.setdefault(city, []).append(event)

os.chdir(r"Path\to\directory")

myFile = open("setlistCollection.py", "w", encoding = 'utf-8')
myFile.write("setlistCollection = " + pprint.pformat(setlistCollection) + "\n")
myFile.close()

print("All done!")
