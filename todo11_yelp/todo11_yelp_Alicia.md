Alicia Sigmon
als333@pitt.edu
11/08/17

# To Do 11:

## Step 1

Below are the sizes of the files from the yelp challenge:

    - business.json: 127M
    - checkin.json: 58M
    - photos.json: 24M
    - review.json: 3.6G
    - tip.json: 177M
    - user.json: 1.5G

review.json contains 4736897 reviews.


To find the number of reviews containing a word ("horrible" or "scrumptious"), I used to following code:

$ grep -P "horrible" review.json | wc -l
$ grep -P "scrumptious" review.json | wc -l


Lines containing "horrible":
78181

Using head, I noticed that most of of the top couple reviews had low stars, with only 1 star. I did see one high star of 4.


Lines containing "scrumptious":
6558

Scrumptious is indicative of high scores. I saw lots of 5s, some 4s, and a 3.

## Step 2

Space: 204/238 GB

Memory: 53-54%

Processor: 7.87 GB usable


In modifying FOO.json, I discovered that about 125K lines is my limit. I was able to look at 125K lines but not at 150K lines.


This means we would need much more space and memory to process all of the data. To process this data, you need to consider the space and memory of your computer, the age of your processor, and how up-to-date your system is. That said, I'm not sure if our computers can ever process the data in it's entirity, because I do not have a lot of background in computers to know what their processing power is.