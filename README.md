# soundcloud-mapping

Using web scraping and machine learning to visualize communities on SoundCloud.

This repo contains two jupyter notebooks, soundcloud_scraper_clean.ipynb is the scraper and soundcloud_landscape_plotting_clean.ipynb makes relevant visualizations. This records the latest 500 likes, comments, reposts, and follows of the accounts stored in seeds.csv, and writes them to a scipy sparse matrix. Likes are assigned a value of one and every otherr type of interaction is given a value of three. It could be modified to collect these interaction types in separate matrices but this ratio works well for data visualization.

The raw data used to produce the original graph with 1,600 artists, where likes, follows, comments, and reposts data are stored separately can be found here: https://www.mediafire.com/folder/z8moaq2vgnbdl/soundcloud_scraped_data

The latest sparse matrix containing combined interaction data for 9,000+ artists is in the sparse_matrix.npz file in this repo.

To use, save a seeds.csv and remaining_seeds.csv file in your directory with the artists you want to start pulling data from. For my data visualization project, the following accounts were used as seeds representing different parts of the SoundCloud underground:

kggn
axxturel
paulonrecords
blackwinterwells
djphat1996
blackkray
danikiyoko
soretsuu
tsarbeg
mysticalmobbing

Initialize both spreadsheets with the same set of seed accounts, fill in both names and links with the marker found in the soundcloud URL and just put zeros for other fields. remaining_seeds is used to label rows of the sparse matrix while seeds is used to label columns, be sure not to alter the order of these files in the middle of scraping. 

The scraper also allows for pausing in the middle of a run. To do this, simply interrupt the kernel while the scraper is still only on the likes page (this is to prevent data from being collected twice). Run the block below the main control loop to save progress. Then when you reopen the scraper run the block labeled "reload an in-progress run."

Once the scraper reaches the end of seed accounts, it will then identify the most interacted with account that hasn't already been scraped and append it to remaining_seeds and then scrape it. You can let it continuously do this, however this has a tendency to eventually only reach more popular accounts which may not be desired. You can avoid this behavior by simply adding more to the remaining_seeds.csv file. 

I wrote some general stuff about my methods here: https://pswjt1.medium.com/visualizing-the-shape-of-soundcloud-communities-with-web-scraping-and-machine-learning-cc1c5d948f78



