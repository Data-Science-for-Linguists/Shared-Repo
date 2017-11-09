# Exploration
Trying to use the ```tar``` command gave me the errors:
```bash
- tar: Ignoring unknown extended header keyword 'LIBARCHIVE.creationtime'
- tar: Ignoring unknown extended header keyword 'SCHILY.dev'
- tar: Ignoring unknown extended header keyword 'SCHILY.ino'
- tar: Ignoring unknown extended header keyword 'SCHILY.nlink'
```
on each JSON file, so I have opted to use 7zip to get the untar the file.


The total size once extracted is 5.4GB


The head of the business JSON includes information in brackets such the name of the business, a unique ID, a neighborhood, and many other features of each business. The head of checkin.JSON shows features like the date and time and a business ID. I think the user file contains unique user IDs.


The ```wc -l``` command took longer than I expected to run (~15 seconds) and returned that there are 4,736,897 reviews.


There are 78,181 reviews in the dataset that contain 'horrible' and 6,558 that contain the word 'scrumptious'. The 'scrumptious' seemed to contain a number of 5 stars, and I didn't see anything under 4 stars. In general the 'horrible' reviews were shorter and usually 1 star, although I did find one that was 4 stars.


# Processing
This analysis is being run on a computer with an Intel i5-3330 with 8GB of ram and on a 2TB harddrive. The computer is running Windows 10 and is under five years old.


I started my FOO.json with ```head -10``` and multiplied that number by 10 for each test. The first notice of any stutter was a minor one between 10,000 and 100,000. At ```head -10``` I could not run the script without running into a memory error. Decreasing to 500,000 did not solve this, nor did 250,000. This means that the memory runs out on my computer when the somewhere between ```head -100000``` and ```head -250000```. At 100,000 my memory usage jumped from 63% to 69% which seemed like a smaller jump that I anticipated. When I tried the 250,000 set, the memory jumped from 62% to 71% before the script crashed. I expected it to get much higher before it crashed.

If I were to process all of this data I would either need to split the data into smaller bunches which could be processed seperately before being put back together, or I would need to use a computer with more RAM and a better processor like an i7. With a large enough dataset, the harddrive could become an issue, although this dataset doesn't come close to filling up the harddrives on this computer. As the data size increased so did the time to process the data. Even if a computer may be able to process large ammounts of data, it may take a long time without the proper specs.