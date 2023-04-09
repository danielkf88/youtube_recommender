#YouTube Data Science Video Library
##Problem Statement
Have you ever tried to learn Data Science from YouTube? For me, that is a resounding yes. YouTube has been an important platform for learning Data Science concepts, but it is also a platform for leisure/entertainment. This brings out the first problem I face: distraction. Even if I manage to overcome distraction, there are a vast number of videos on the same topics, which brings out the second problem: quality of video.

Thus, the problem statement is how to avoid distraction and watch high-quality videos when learning Data Science on YouTube. The audience for this project are anyone who uses YouTube as a platform for learning Data Science.

The goal is to create a library of videos published by YouTubers who are data professionals and a scoring system, other than view count, to rank the videos.

##Overview of Approach
The first part of this project was to curate a library of video links. For that purpose, 30 channels of data professionals were identified.

To get all the links from a channel, follow the instructions from this link: https://softexpert.pk/how-to-copy-all-the-titles-and-urls-from-youtube-channel/.
The data was scraped using a Jupyter Notebook (1_yt_stats_scraper.ipynb) that contained steps to scrape the author, title, publish date, views, likes, length, URL, types, keywords, image, and description from YouTube.
To scrape the captions, refer to 2_yt_caption_scraper.ipynb.
After all the data was scraped, 3_yt_data_prep.ipynb was used for data cleaning and feature engineering. Furthermore, n-grams analysis was performed in this notebook.
The second part involved topic modeling using BERTopic on the video titles and captions. Based on the word cloud of the video titles, it was observed that topics were easily recognizable, which means the base BERT model should suffice in the topic modeling. However, for the captions, Count Vectorizer model and Class TFIDF were incorporated into the BERTopic to remove stop words and reduce the impact of frequent words. The topics were then manually renamed to more meaningful and understandable names for both topics generated for title and caption.

The third part involved modeling to determine the quality of videos. The hypothesis is that if the video has a higher actual like count compared to its predicted like count, it is a quality video. K-nearest neighbors were chosen as the base model, and linear regression, random forest regression, decision tree regression, and gradient boosting regression were performed to determine if any model is able to beat the MAE and R-Square of K-nearest neighbors. The linear regression model was chosen as the champion model for predicting likes using views.

Usage
This YouTube Data Science Video Library is a collection of curated videos from data professionals ranked by a scoring system based on the video's actual like count and its predicted like count. The repository includes:

Jupyter Notebooks used for data scraping, cleaning, feature engineering, and modeling
1_yt_stats_scraper.ipynb contain steps in getting info from youtube
2_yt_caption_scraper.ipynb contain steps in getting caption from youtube
3_yt_data_prep.ipynb contain steps in feature engineering and ngrams analysis
4_word_cloud.ipynb contain steps in generating wordcloud using youtube title and caption
5_bert_topic_modelling.ipynb contain steps in using BERTopic modelling
6_modelling.ipynb contain steps in modelling and creation of final csv for building dashboard in PowerBI
A data folder containing the video links: vid_link_final.csv and vid_info_final.csv (end csv file after 1_yt_stats_scraper.ipynb)
A final product as a PowerBI dashboard 
To use this repository, you can clone it to your local machine and run the Jupyter Notebooks to scrape, clean, and model the data for your own project.

Credits
This project was completed by Lee Kah Fai Daniel as part of his Capstone Report and Technical Analysis.
https://softexpert.pk/how-to-copy-all-the-titles-and-urls-from-youtube-channel/ for technique to retrieve links from youtube channels
https://maartengr.github.io/BERTopic/faq.html#how-do-i-remove-stop-words for techique in improving BERTopic modelling results

License
This repository is licensed under the MIT License.
