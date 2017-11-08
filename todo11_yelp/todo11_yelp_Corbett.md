## Robert Corbett
## Todo 11 yelp
## 11/09/2017

## Step 1:

I downloaded the .tar file and extracted it using the command 'tar -xvf yelp_dataset.tar dataset'
	-x has the tar command extract instead of compress
	-v "verbose mode" displays progress
	-f allows me to specify the directory name	'dataset'

The 'ls -l dataset' command lists the files in the directory dataset as well as other info
	-h in combination with -l makes the sizes of the files human readable
	-a includes all files including hidden files
	-F adds '/' to the end of directorys
	
	In the dataset directory, there are two hidden directories that are both empty
	business.json is 127M 
	checkin.json is 58M
	photos.json is 24M
	review.json is 3.6G
	tip.json is 177M
	user.json is 1.5G
	
Using 'head business.json", the data is in json format.  So each entry is surrounded by curly brackets.
	The fomat is {"label_1":"data_1", "label_2":"data_2", ...}
	The labels in business are
		business_id
		name
		neighborhood
		address
		city
		state
		postal_code
		latitude
		longitude
		stars
		review_count
		is_open
		attributes - is followed by nested curly braces
			RestaurantPriceRange2
			BusinessParking - is followed by nested curly braces
				garage
				street
				validated
				lot 
				valet - close curly braces
			BikeParking
			WheelchairAccessible - close curly braces
		categories
		hours - is followed by nested curly braces
			Monday
			Tuesday
			Friday
			Wednesday
			thursday
			Sunday
			Saturday - close curly braces
		- close curly braces
	The other files have different data organized in the same format
	
Using the 'wc -l review.json' command, '4736897' review.json is returned.
	Since the json entries are kept on one line in the file, there are 4,736,897 entries in review.json

'grep 'horrible' review.json | wc -l' I used grep to search for all instances of the word 'horrible'
	and then piped that through wc -l to count how many lines grep returned
	the result was 78,181 lines
	
'grep 'horrible' review.json | head' looking at these reviews, the first 7 all recieved a 1 star rating.
	the eighth review had a 4 star rating.  Looking at the body of the review, the user said they were afraid to 
		try the restaurant because of its 'horrible reputation', but they enjoyed the food.
'grep 'horrible' review.json | tail' is all over the place.  Of the ten reviews, three have 1 star, two have 2 stars,
	two have 3 stars, two have 4 stars, and one has 5 stars.
	
'grep 'scrumptious' review.json | head' and
'grep 'scrumptious' review.json | tail' returned one 2 star, one 3 star, six 4 star, and twelve 5 star reviews.

## Step 2:

My Laptop:
	disk space: 359GB free of 698GB
	memory: 16G
	processor: Intel Core i7-4700HQ 2.40GHz
	Windows 10
	
Created process_reviews.py and FOO.json in data_science directory
	ran the script on FOO.json with only 10 reviews and it worked fine
	
Looking at my computers base line resource usage
	about 1-2% CPU 
	about 27% memory (I think I have too much open)
	about 1-2% Disk
	
FOO.json - 100 reviews
	CPU usage jumped up to 8% while everything else stayed the same
	
FOO.json - 1,000 reviews
	same as with 100 reviews
	
FOO.json - 10,000 reviews
	CPU usage jumped up to 15% while everything else stayed the same
	
FOO.json - 100,000 reviews
	CPU usage jumped to 19%
	Memory usage jumped up to 30%
	took a couple seconds to run

FOO.json - 1,000,000 reviews
	it took about 10 seconds for FOO.json to be created
	took just over one minute to run
	CPU usage peaked at 28% 
	memory usage peaked at 78%
	disk usage siked for a short period to 35%
	
FOO.json - 10,000,000 reviews
	it took much longer to create FOO.json
	I tried to run proces_reviews on the 10,000,000 reviews
		My memory and disk usage jumped to 99% while CPU usage remained low
	I had to force stop the process

The process does not seem to be CPU intensive, CPU usage never went above 30%
The biggest restraint seems to be memory.  Even though my laptop has 16G of ram, that amount
	is not close to being adequate for dealing with the extremely large data structures python 
	needs to create to handle the data.
A system built to process this amount of data would need huge amounts of memory.