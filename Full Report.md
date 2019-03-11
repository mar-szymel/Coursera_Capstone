# Coursera Capston Full Report:

## >> Introduction - business problem.

Assume you are a global investor in field of gastronomy and you are looking to open a chain of restaurants in biggest cities in Europe. Many cities...

Obviously you don not know every single city, and actually don't know where to locate your restaurants. Whether it's good idea to invest only in city centers, or maybe most of restaurants are hidden in some specific districts.

The aim of this analysis if to automatically find area of city with biggest density of restaurants and nightlife facilities using segmentation. I'll be profiling districts of Warsaw (capital city of Poland) as a small prof of concept because I know the city and can verify whether findings from segmentation looks reasonable or not.



## >> Data used to solve the problem and the source of the data.

Scraped list of postal codes in Warsaw: http://www.kody-pocztowe.dokladnie.com/ There are more than 4k of them, so I used sample of them.

After we get postal codes we can geocode them and get latitudes and longitutes for map visualisation.

Finally Foursquare location data - via Foursqare API we can obtain POI with categories, like restaurants, shops, parks etc..



## >> Methodology.

1st I have geocoded postal codes (small districts) and puted them on a Warsaw map:

![map1](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/map1.png)

Having data obtained from Foursqare API (list of nearby venues with their categories), I've used mainly Pandas to prepare data - wrangle them, join, make one-hote encoding:

![df1](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/one_hot.png)

Then aggregating:

![df2](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/one_hot_grouped.png)

And finding most common venues in each district/postal code:

![df2](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/one_hot_grouped2.png)


After that preprocessing stage I've used K-means algorythym from scikit to find similar clusters - districts /(postal codes) similar to each other inside clusters, and as much as possible different among clusters.

![map2](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/map2_clusters.png)

Then I'll profile each cluster and look at percentage of categories among 1st most common vanues - see wether cluster contains a lot of restaurants etc, or other types of venues prevail.



## >> Results - findings about clusters:

Cluster 0 - busy places. Lots of people. Good for fastfood/snacks places like "Subway" or others "takeaway's".

![bar0](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/bar_c0.png)

Cluster 1 - best for restaurant. Mainly in downtown, but not always.

![bar1](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/bar_c1.png)

Cluster 2 - small one... Perhaps shoud be merged with some other cluster...

Cluster 3/4/5 - remote districts. Good for pizza/burger, rather than elegant restaurant/drink bar.

Cluster 6 - not in very city center, but good for sam cafe's, inexpensive food places. MIGHT BE BEST TO INVEST MONEY THERE!

![bar6](https://github.com/mar-szymel/Coursera_Capstone/blob/master/files/bar_c6.png)

Cluster 7 - stores, gym, etc.

Cluster 8 and 9 - recreation areas.



## >> Discussion - observations / recommendations based on the results.

Perhaps the most interesting cluster for investing money in food restauranst might by cluster no 6 - not in very city center (so not so pricy), but still with lot of gastro-venus and cafes!

But also as a global investor we may think about some cheap/fastfood chain in places like in cluster no 0 - buzy places with lot of people.

And if we want to open some posh-pricey elegant place, cluster no 1 would be the best.


## >> Conclusion.

**The analysis shows that clustering districts look reasonable (I know Warsaw), so we can conduct similar analysis for other cities all over the world without knowing them and in automatic manner find some similar clusters, profile them and take decisions as a investor.**

**THANKS FOR READING!**
