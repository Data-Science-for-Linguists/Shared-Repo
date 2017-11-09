## Todo 11: Dan

## Step 1: Preparation, exploration

5.
```
rw-r--r-- 1 dan dan 127M Aug 25 18:00 business.json
-rw-r--r-- 1 dan dan  58M Aug 25 18:04 checkin.json
-rw-r--r-- 1 dan dan  24M Aug 25 17:57 photos.json
-rw-r--r-- 1 dan dan 3.6G Aug 25 18:05 review.json
-rw-r--r-- 1 dan dan 177M Aug 25 18:06 tip.json
-rw-r--r-- 1 dan dan 1.5G Aug 25 18:04 user.json
```
6. While `head` printed out a few lines, using python, we can read 1 line from each file and grab the keys used.
```
photos.json keys: caption, photo_id, business_id, label
review.json keys: funny, user_id, review_id, text, business_id, stars, date, useful, cool
business.json keys: city, neighborhood, name, business_id, longitude, hours, state, postal_code, categories, stars, address, latitude, review_count, attributes, is_open
tip.json keys: date, text, user_id, likes, business_id
checkin.json keys: business_id, time
user.json keys: yelping_since, useful, compliment_photos, compliment_list, compliment_funny, funny, review_count, friends, fans, compliment_note, compliment_plain, compliment_writer, compliment_cute, average_stars, user_id, compliment_more, elite, compliment_hot, cool, name, compliment_profile, compliment_cool
```
7.
```
$ wc -l review.json
4736897 review.json
```
8.
```
$ grep 'horrible' review.json | wc -l
78181
```
9. Generally bad reviews. For example: "This place is NOT Caribbean food! It's terrible. You must ask for a drink separate from the combo even though you've ordered a combo. They're not going to offer it to you either. The food tastes horrible. I wish I could sit outside and turn people around to save their souls. But unfortunately this is all I can do. Take heed and go elsewhere!!!!!" Stars: 1
10. Generally good reviews. For example: "Healthy and delicious doesn't always go together but at the Fresh Mint it describes most if not all of the menu.  I ordered the Rainbow Veggies with brown rice along with the sweet and sour soup.  Both were scrumptious.  Will definitely be back to visit whenever I am in or near Scottsdale." Stars: 5

## Step 2: Processing
1. My Computer:
  - 1TB Hard Drive + 500GB SSD
  - 16GB RAM
  - Intel Core i5-7600K CPU
  - Relatively new, built earlier this year
2. I was able to read up to 1500000 lines, at which point my RAM usage was about 14.5GB and one CPU core was running at 100%. The problem here can be addressed by using the `chunksize` parameter when opening files. Modifying `process_reviews.py` :

```python
import pandas as pd
import sys
from collections import Counter

filename = sys.argv[1]

parts = pd.read_json(filename, lines=True, chunksize=10000, encoding='utf-8')
wfreq = Counter()
for df in parts:
    wtoks = ' '.join(df['text']).split()
    temp = Counter(wtoks)
    wfreq.update(temp)


print(wfreq.most_common(20))

```
to use chunksize makes it much more manageable. Though it took a while, I was able to read all of `review.json` into the dataframe and produce the top 20 words:
```
$ python process_reviews.py review.json
[('the', 22108652), ('and', 17929876), ('I', 13709652), ('a', 13378568), ('to', 12840088), ('was', 9248521), ('of', 7767234), ('is', 6412057), ('for', 6067512), ('in', 5665929), ('The', 4677120), ('it', 4639074), ('with', 4270917), ('that', 4204770), ('my', 4167027), ('but', 3618753), ('on', 3516987), ('you', 3357511), ('have', 3273060), ('this', 3153958)]
```
while keeping my memory use to about 4GB.

With this kind of work, time and space complexity are extremely important. Writing inefficient code is much more costly at this scale, and some ways of doing things just won't work at all. Distributed computing and efficient code are the way to go.
