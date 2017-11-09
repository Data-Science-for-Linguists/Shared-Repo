**Paige Haring**
**peh40@pitt.edu**
**11/8/17**

### Step 1: Preparation and Exploration

1. business.json is 126M, checkin.json is 57M, photos.json is 23M, review.json is 3.6G, tip.json is 176M, and user.json is 1.5G.

2. The data are large json files with tons of information about the user who posted the review and the review itself. Here is just a a little bit of what was returned when I used the head command I believe this is all of the information for a single business that has been reviewed because this json file came from business.json. It includes info like neighborhood, address, parking information, name, hours, etc:

{"business_id": "YDf95gJZaq05wvo7hTQbbQ", "name": "Richmond Town Square", "neighborhood": "", "address": "691 Richmond Rd", "city": "Richmond Heights", "state": "OH", "postal_code": "44143", "latitude": 41.5417162, "longitude": -81.4931165, "stars": 2.0, "review_count": 17, "is_open": 1, "attributes": {"RestaurantsPriceRange2": 2, "BusinessParking": {"garage": false, "street": false, "validated": false, "lot": true, "valet": false}, "BikeParking": true, "WheelchairAccessible": true}, "categories": ["Shopping", "Shopping Centers"], "hours": {"Monday": "10:00-21:00", "Tuesday": "10:00-21:00", "Friday": "10:00-21:00", "Wednesday": "10:00-21:00", "Thursday": "10:00-21:00", "Sunday": "11:00-18:00", "Saturday": "10:00-21:00"}}
{"business_id": "mLwM-h2YhXl2NCgdS84_Bw", "name": "South Florida Style Chicken & Ribs", "neighborhood": "Eastland", "address": "2824 Milton Rd", "city": "Charlotte", "state": "NC", "postal_code": "28215", "latitude": 35.23687, "longitude": -80.7419759, "stars": 4.5, "review_count": 4, "is_open": 0, "attributes": {"GoodForMeal": {"dessert": false, "latenight": false, "lunch": false, "dinner": false, "breakfast": false, "brunch": false}, "HasTV": false, "RestaurantsGoodForGroups": true, "NoiseLevel": "average", "RestaurantsAttire": "casual", "RestaurantsReservations": false, "OutdoorSeating": false, "BusinessAcceptsCreditCards": false, "RestaurantsPriceRange2": 2, "RestaurantsDelivery": true, "Ambience": {"romantic": false, "intimate": false, "classy": false, "hipster": false, "divey": false, "touristy": false, "trendy": false, "upscale": false, "casual": false}, "RestaurantsTakeOut": true, "GoodForKids": true}, "categories": ["Food", "Soul Food", "Convenience Stores", "Restaurants"], "hours": {"Monday": "10:00-22:00", "Tuesday": "10:00-22:00", "Friday": "10:00-22:00", "Wednesday": "10:00-22:00", "Thursday": "10:00-22:00", "Sunday": "10:00-22:00", "Saturday": "10:00-22:00"}}

3. There are 4736897 reviews in review.json

4. 78181 of the reviews include the word 'horrible'. Unsurprisingly they seem to have low stars.

5. 6558 of the reviews include the word "scrumptious". Most of the reviews I saw had 4 our 5 stars.


### Step 2: A Stab at Processing

##### My System: MacBook Pro (13-inch, Mid 2012)
- Disk space: Using 156.59 GB of 498.88 GB
- Memory: 4 GB 1600 MHz DDR3
- Processor: 2.5 GHz Intel Core i5

When I did
head -10 review.json > FOO.json
python process_review.py FOO.json

% CPU for python jumped up to 99.1%, so I think that's the limit???

#### Observations:
This dataset took an hour and a half for me to download. Then, in step 4 when I created the dataset dictionary, that a pretty long time as well. I don't know much about computer hardware, but clearly it would take a much stronger computer than mine to process this dataset for real. Clearly, my computer is capable of downloading, uncompressing, and poking around at this data, but I don't think it can do too much more than that. I guess I would need more memory and a better processor?
