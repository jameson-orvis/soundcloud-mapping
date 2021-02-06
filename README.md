# soundcloud-mapping

Using web scraping and machine learning to visualize communities on Soundcloud.

This repo contains two jupyter notebooks, soundcloud_landscape_clean.ipynb is the scraper and soundcloud_landscape_plotting_clean.ipynb plots. The records the latest
500 likes, comments, reposts, and follows of the accounts stored in seeds.csv, and writes them to separate dataframes.

To use, save a seeds.csv file in your directory with the artists you want to start pulling data from first

Should look something like this:

name | links | followers

With both name and links populated by the artist's internal soundcloud marker (e.g. the marker that refers to them in the soundcloud url rather than the actual display name)
and followers set to 0. Only need two or three artists here that represents scenes you are interested in.

The scraper will continuously append newly found artists to this list and then move to these artists and scrape them.

To set up for initial use, change references to remaining_seeds in the scraper to seeds. Remaining_seeds was added as an alternate list of accounts to be scraped sorted by 
number of interactions from the first set of accounts. 

I wrote some general stuff about my methods here: https://pswjt1.medium.com/visualizing-the-shape-of-soundcloud-communities-with-web-scraping-and-machine-learning-cc1c5d948f78



