# Visitor's Log
## Kyle's Project

A Study of the Lancaster Corpus of Mandarin Chinese
The project can be found at https://github.com/Data-Science-for-Linguists/project_KyleLandin


### Dan's Visit, 11/6/2017
#### Something you learned
  - I've never seen a Chinese dataset before. Very cool!
  - I didn't know about `pd.merge`, which will definitely come in handy.

#### Something else that came to your mind.
  - To further verify that you've made the dataframe correctly, maybe you can use some kind of API to convert pinyin to characters or vice versa?
  - When you have 全国 -> quan2guo2, what do the 2s mean?


### Katherine's visit, 11/7/2017
This seems like a really interesting (and intricate) data set, and I think that trying to combine all of the information into one data frame could be really useful.
It seemed that you were almost ready to start analyzing the data, but you weren't really sure where to start. My first thought was using the different topics in your corpus. You could select some categories that you think would have some important differences, and look into how exactly they differ (e.g. are certain words more common in specific contexts?). For example, news reports are probably a lot more formal than articles about hobbies and humor, so you could try to pick categories that would let you look at differences between formal and informal writing.

### Ben's Visit Nov 15, 2017  
#### Something I learned  
    - Very interesting project that seems to have clearly worthwhile goals. I can imagine all people will appreciate being able to access this data in a usable and clear format like your data frames. I learned more about using cat instead of merge - an issue I encountered as well (I still used merge but found a way to keep the shape I wanted, but it is not efficient).

#### Something that came to mind  
    -  It is beyond the scope of our class project, but it would be great to also have a couple more columns - English meaning of the words, and the IPA script as Pinyin is only somewhat phonetic despite its intentions.

### Chris's Visit 11/16/2017
#### Something I learned
	- I never used BeautifulSoup before, so seeing that being done was really interesting 

#### Something that came to mind
	- Since you said in your project plan that your corpus is similar to the FLOB and FROWN corpus, perhaps you could look further into some comparisons between Chinese and English using your data?

### Alicia's Visit 11/19/17
#### Something I learned:
	- The pd.mmerge was a very useful command that I would not have thought of using!
		- see my last "something that came to mind" bullet
#### Something that came to mind:
	- Your README.txt and project_report.md were very helpful at giving a good overview of the project and why the work matters!
	- Your beautifulSoup_Practice.ipynb currently runs into an error at the 10th block.
	- LCMC_Testing.ipynb: 
		- I would recommend not printing the entire read in file - it makes your file larger, less efficient, and harder to read.
			- It took a noticeably longer amount of time for me to open this file than any other's I've opened.
		- I think you should add markdown cells and comments to explain what your cells are doing. Your LCMC_Testing.ipynb will much easier to read.

** Andrew's Visit Nov 20th **
I was having trouble loading your Jupyter notebook for a while. I believe it's because the file size is fairly large. You flashed a lot of data on the screen, and on Github, this makes the file difficult to look through.

Have you decided on what your analysis will be on yet? It might be interesting to see how the different categories like Popular_Lore and News_Editorial would compare.