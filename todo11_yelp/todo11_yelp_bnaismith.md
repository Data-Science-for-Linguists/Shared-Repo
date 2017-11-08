##ToDo11 - Poking Yelp Dataset##

#### Step 1 ####

_Q4 - Extract, 'untar', files_  
tar -xvf yelp_dataset.tar  

_Q5 - How big are the files? Find out through ls -laFh._  

Schnazzle-Popps:dataset Benjamin's$ ls -laFh  
total 11315904  
drwxr-xr-x   8 Benjamin's  staff   272B  8 Nov 11:18 ./  
drwxr-xr-x  17 Benjamin's  staff   578B  8 Nov 11:17 ../  
-rw-r--r--@  1 Benjamin's  staff   126M 25 Aug 18:00 business.json  
-rw-r--r--@  1 Benjamin's  staff    57M 25 Aug 18:04 checkin.json  
-rw-r--r--@  1 Benjamin's  staff    23M 25 Aug 17:57 photos.json  
-rw-r--r--@  1 Benjamin's  staff   3.6G 25 Aug 18:05 review.json  
-rw-r--r--@  1 Benjamin's  staff   176M 25 Aug 18:06 tip.json  
-rw-r--r--@  1 Benjamin's  staff   1.5G 25 Aug 18:04 user.json  

_Q6 What do the data look like? Find out using head._  

Lots of meta-data, e.g. times, categories, days, etc.  

Schnazzle-Popps:dataset Benjamin's$ head -1 business.json  

{"business_id": "YDf95gJZaq05wvo7hTQbbQ", "name": "Richmond Town Square", "neighborhood": "", "address": "691 Richmond Rd", "city": "Richmond Heights", "state": "OH", "postal_code": "44143", "latitude": 41.5417162, "longitude": -81.4931165, "stars": 2.0, "review_count": 17, "is_open": 1, "attributes": {"RestaurantsPriceRange2": 2, "BusinessParking": {"garage": false, "street": false, "validated": false, "lot": true, "valet": false}, "BikeParking": true, "WheelchairAccessible": true}, "categories": ["Shopping", "Shopping Centers"], "hours": {"Monday": "10:00-21:00", "Tuesday": "10:00-21:00", "Friday": "10:00-21:00", "Wednesday": "10:00-21:00", "Thursday": "10:00-21:00", "Sunday": "11:00-18:00", "Saturday": "10:00-21:00"}}  

Schnazzle-Popps:dataset Benjamin's$ head -1 checkin.json  

{"time": {"Thursday": {"21:00": 4, "1:00": 1, "4:00": 1, "2:00": 1, "20:00": 2, "22:00": 1, "19:00": 1, "15:00": 2, "13:00": 1, "23:00": 2}, "Wednesday": {"11:00": 2, "13:00": 2, "14:00": 1, "17:00": 1, "6:00": 1, "2:00": 1, "0:00": 2, "1:00": 1, "21:00": 1, "18:00": 1, "19:00": 1, "20:00": 2}, "Sunday": {"18:00": 1, "16:00": 1, "14:00": 1, "19:00": 2, "17:00": 1, "23:00": 1, "21:00": 1, "20:00": 5, "6:00": 1, "0:00": 1, "2:00": 2, "3:00": 3}, "Friday": {"16:00": 1, "14:00": 2, "10:00": 2, "23:00": 1, "19:00": 2, "18:00": 1, "15:00": 1, "21:00": 2, "22:00": 2, "3:00": 1, "0:00": 2}, "Saturday": {"21:00": 1, "23:00": 3, "18:00": 4, "10:00": 1, "12:00": 1, "13:00": 3, "14:00": 1, "15:00": 1, "16:00": 2, "17:00": 3, "2:00": 1, "0:00": 1, "1:00": 2}, "Monday": {"12:00": 1, "11:00": 1, "14:00": 1, "18:00": 1, "19:00": 1, "23:00": 1, "20:00": 1}, "Tuesday": {"18:00": 2, "12:00": 1, "13:00": 2, "16:00": 1, "15:00": 1, "4:00": 1, "21:00": 1, "20:00": 2, "23:00": 2}}, "business_id": "7KPBkxAOEtb3QeIL9PEErg"}  

_Q7 How many reviews are there? Find out using wc -l._  

Schnazzle-Popps:dataset Benjamin's$ wc -l review.json  
 **4736897** review.json  

_Q8 How many reviews use the word 'horrible'? Find out through grep and wc -l. Take a look at the first few through head | less. Do they seem to have high or low stars?_  

Schnazzle-Popps:dataset Benjamin's$ grep "horrible" review.json | wc -l  
  **78181**  

grep "horrible" review.json | head -3 resulted in low stars -> search for reviews with 1 star and horrible reveal a high percentage of all reviews with 'horrible':  

Schnazzle-Popps:dataset Benjamin's$ grep "horrible" review.json | grep '"stars":1' | wc -l  
  **46260**  

_Q9 How many reviews use the word 'scrumptious'? Do they seem to have high stars this time?_  

Schnazzle-Popps:dataset Benjamin's$ grep "scrupmtious" review.json | wc -l  
  **1**  #Why did it return only 1 when head returns more?  

head shows a mix of positive and ambivalent reviews, although mostly positive.  

_Short reflection summary. What sorts of resources would it take to successfully process this dataset in its entirety and through more computationally demanding processes? What considerations are needed?_  

Based on this small example, it is clear that personal computers are not sufficiently powerful for the demands of the data processing. It was a struggle on my mac, both to find the necessary room on the hard drive and to deal with the wait times needed to run even simple searches. The process would also be much faster if I had a greater familiarity with command line syntax.

#### Step 2 ####

atom process_reviews.py #create Python script file

Schnazzle-Popps:dataset Benjamin's$ chmod +x process_reviews.py
Schnazzle-Popps:dataset Benjamin's$ head -10 review.json > FOO.json
Schnazzle-Popps:dataset Benjamin's$ chmod +x process_reviews.py FOO.json

I think I'm doing something wrong here but not sure what. Out of time for ToDo11!
