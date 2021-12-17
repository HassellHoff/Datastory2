# Impact of Elon Musk quotes on Tesla's stock


## Abstract

Elon Musk is the world's richest person and is famous for gaining attention for his tweets that according to him half are generated while sitting on his toilet. During the recent years his tweets have gathered much attention by their impact on markets which has left investors worried. From jumping the value of cryptocurrencies such as bitcoin and dogecoin to small companies such as Gamestop Elon Musk's tweets have undeniably played a huge impact on moving stock prices of companies. It has been claimed that Elon Musk's twitter account could be Tesla's primary marketing tool since Tesla does not invest in marketing at all. The hypothesis of our analysis definately backs this theory. 

The purpose of our project is to find correlations between the stock price of Tesla and the quotes that Elon Musk has said. Our research is based on the time period between 2015 - 2020. In addition, we want to create a model that can predict future stock price based on historic stock and quotation data. 



## Phase one and two: Loading the datasets and creating the dataframes


### Quote data


***Basic info:*** The data with the quotes from different speakers are from QuoteBank from 2015 to 2020. From the QuoteBank data we filtered quotes that were mentioned by Mr Elon Musk himself and wrote the it on a new file.

<img width="1638" alt="Screenshot 2021-12-17 at 8 51 32" src="https://user-images.githubusercontent.com/92207222/146501806-c1558819-3296-4a2e-b20f-a08bae2853a5.png">

***Figure 1:*** The number of Elon Musk quotes in respective to time. 




### Tesla stock data

***Basic info:*** The Tesla stock price data was imported from Yahoo Finance. The data has the high, low, open, close, volume and adj close values.

***Preprocessing:*** The dataset's start and end dates were adjusted to match with the quote data

<img width="385" alt="Screenshot 2021-12-17 at 9 22 11" src="https://user-images.githubusercontent.com/92207222/146505557-6a81ea89-fe1b-43e6-af6c-87f6fa03b0de.png">

***Figure 2:*** Tesla's stock price through the years



## Phase three: Quotations preprocessing

***The process consisted of the following steps:***

1. Remove punctuation: to reduce the sparsity of data
2. Casefolding: due to the small size of the dataset it was necessary to reduse the sparsity of the data by using 'removed_punctuation'. This returns lowercased strings
3. Tokenization: using the function 'word_tokenize' to determine the 10 most common words of the quotes
4. Removing stop words: a method that drops some unnecessary values that are on the 'stopwords list' -> gives us quotes with more meaningful words for our analysis
5. Lemmatization: method that maps all forms of a single word to a single form -> benefits us in future analysis



## Phase Four: Analysing Elon Musk's quotation


Elon Musk's quotations to get an insight of our data and to which extent we can use this data for our goal project. First we will find the most common words in order to determine what are the predominant topics of Elon Musk's quotations. The quality of each quote was examined by parsing each quote into separate words and by tokenizing the words. Each word played a signifficant role in shifting the stock market price. In addition, another factor that we believe impacts the stock price of Tesla is the volume of posts made by Musk each day he posted. The first thing to do is to put all the quotes in a single string in to all_words_list and to calculate the frequency of each word in this string.


<img width="952" alt="Screenshot 2021-12-17 at 20 45 53" src="https://user-images.githubusercontent.com/92207222/146593076-64376432-be9c-44ce-95c6-ce95dc413e4f.png">

***Figure 3:*** Most popular words

We see that the first two words are Tesla and cars, which seems to be the proheminents topic and agrees with our basic hypothesis which highlights the interest of Elon Musk towards Tesla and the automotive industry among others.


![Screenshot 2021-12-16 at 12 51 25](https://user-images.githubusercontent.com/92207222/146358193-db438f2d-9e85-464b-9c4a-8af4fbd1d26f.png)

***Picture 1:*** The process of the data handling

For the analysis we used two different pre-trained machine learning methods of sentiment analysis, which were Valder and Textblob sentiment analysis models. The programming portion of our project consisted of three primary steps: data filtering, performing sentiment analysis to the filtered data, and creating a correlation from Tesla's stock price data. Additionally, we wanted to create a model that can predict future stock price based on quotes. The two models that were used to process the quotes said by Musk were the Vader and the Textblob methods. 


## Phase five: Sentiment analysis

The sentiment analyses are done on the quotation without any preprocessing. Indeed, the punctuation or the uppercase can be informative in our case to predict the sentiment of a quote.


### The Vader method

The Vader sentimental analysis model returns the compound score that informs if the quote is positive (compound>=0.05), neutral(-0.5>compound>0.05) or negative(compound >= -0.05). It is a great open-source tool designed to sentiments expressed in social media. It has a MIT License. In our project we specifically used the Vader tool to analyse the text from the quotes. The tool can recognise typical negations, such as "Tesla is not good" or "Model S wasn't very good". In addition, it spots punctuations such as exclamation marks and is thus capable. ofgiving these words more sentiment intesity. An example could the following "Tesla is Good!!!". The Vader tool can also recognize words written with caps lock to give them more sentimental intesity.


### The Textblob method

For the second model, we used TextBlob, another pretrained model to do the sentiment analysis. This model returns two values: the polarity (ie how much a quote is positive or negative) in a range between -1 and 1, and the subjectivity (ie how much the content of a quote is objective or not) in a range between 0 and 1. 

As before, we create the function decide_subjectivity that gives a categorized return: either subjective if the subjectivity > 0,5, objective if subjectivity < 0,5 and neutral if the subjectivity = 0.5. Then, we can keep both categorized and continuous variables in df_sentiment dataframe for both the polarity and subjectivity.

<img width="787" alt="Screenshot 2021-12-16 at 0 53 33" src="https://user-images.githubusercontent.com/92207222/146277634-dd383f9b-d49d-4fb2-9280-5216e70996ac.png">

***Figure 4:*** Classification results of the quotes



## Comparison between Textblob and Vader

### Do the two methods return the same results?

We can see that both analysis indicate similar results. The quotes consisted mostly of positive words (words that have a value above zero), but we should keep in mind that roughly 70% of the quotes are greater than zero. This means that majority of the quotes contain words that are neutrally positive rather than over positive. 



<img width="1661" alt="Screenshot 2021-12-16 at 11 16 07" src="https://user-images.githubusercontent.com/92207222/146342895-e4ce48b8-0772-40a5-a414-9d50ddaffce6.png">

***Figure 5:*** Comparison results between the two pre-trained models Textblob and Vader

Based on t-tests conducted the difference between the two models was statistically signifficant. meaning that we can definately see the quotes and stocks having a relationship.


## The impact of the quotes on the stock price


*"I was always crazy on Twitter" - Elon Musk *

https://www.dontdiewondering.com/elon-musks-most-controversial-tweets/


<img width="1616" alt="Screenshot 2021-12-16 at 12 17 18" src="https://user-images.githubusercontent.com/92207222/146352961-00c2a1e3-08fd-418a-982a-a03dad7e3141.png">

***Figure 6:*** Correlation between the stock price and words used by Elon Musk


Generally speaking we can see that when the quotes had a value of -0.2 to 0.4 the returns had a general turnover rate between -0.05 and 0.05. We could state that while the quotes were on a neutral level, the impact on the returns of the stocks was also on a controlled level. However some interesting exceptions linger in the correlation. For example, the stock price didn't ever drop signifficantly when the quote consisted of majourly of negative quotes. The chart can be easily misleading if we don't keep in mind the fact that each negative quote only tells the average of the score of words that it consisted of. This does not necessarily mean that something bad was said about Tesla. However, as picture 4 indicates, Elon Musk has provenly been giving quotes with a negative ringing which have inreturn impacted negatively on the stock price.

*First Tesla crush in June 2016 raised the amount of quotes significantly for the following few months*




![Screenshot 2021-12-16 at 14 29 54](https://user-images.githubusercontent.com/92207222/146372340-16b61c55-e632-4c43-a91e-799d91153ac6.png)
***Picture 4:*** The impact of Elon Musk's quotes on the stock price of Tesla








```markdown
Syntax highlighted code block
