# Todo 11: Working with Yelp Data
 Chris Lagunilla  
 Due Nov 9 2017

## Part 1:

#### How big are the files?
| File          | Size |
| ------------- | ---- |
| business.json | 126M |
| checkin.json  | 57M  |
| photos.json   | 23M  |
| review.json   | 3.6G |
| tip.json      | 176M |
| user.json     | 1.5G |

#### What does the data look like?
The data is organized into JSON files, which look like dictionaries with key:value pairs.

#### How many reviews are there?
4,736,897 reviews

#### How many reviews use the word 'horrible'? Do they seem to have high or low stars?
78,181. Most seem to have low (1) stars.

#### How many reviews use the word 'scrumptious'? Do they seem to have high stars this time?
5,668. Most seem to have high (4-5) stars.

---

## Part 2:

#### Take stock of your computer hardware.
| Property      | Value |
| ------------- | ----- |
| Avail. Disk Space    | 34.16G |
| Memory               | 8G     |
| Age of System        | Early 2015 Model |

#### How many lines of data can your system reasonably handle?
My computer was able to handle 1,000,000 in 2m, 42.24s.

#### What sorts of resources would it take to successfully process this dataset in its entirety and through more computationally demanding processes? What considerations are needed?
Lots of RAM would need to be available in order to manage such a large amount of data, as well as hard disk space if the data set is to constant grow larger. Some considerations needed in processing such a large data set is the kinds of operations being performed, and if they can be performed simultaneously. Also minimizing context switching into the OS will decrease time considerably. Also a dedicated computer for processing this data would be best so that the CPU need not switch between processes that are unrelated to the script.
