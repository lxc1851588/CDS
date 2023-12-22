---
layout: default
---

## Category analysis
<div style="display: flex; align-items: flex-start;">
  <div style="flex: 1; padding-right: 20px;">
    <p style="font-size: 20px;"><br>There are a lot of different styles of beers. Actually, in our dataset, all reviews are regrouped into 180 different styles which we decide was too much for analysis. Therefore we decided, based on the following chart, to embed the different styles into 9 categories: Browns, Pale ales, wheats, stouts, Belgians, sours, lagers, porters and others.<br> Those labels correspond to the main categories that we can find in the beer world and the category
    others is containing all sorts of fancy mixtures (fruits beers, barleywines beers, sake-based beers,
    smoked beers, …)<br> The embedding is done as the following table. Now that the categorization of the beers has been narrowed, it is time to look at some regional
    trends.</p>
    <br>
    {% include beer_type.html %}
  </div>
  <div style="flex: 1;">
    <br><br>
    <img src="/data/beer_type.jpg" alt="Taxonomy of Beer Types" style="width: 100%; height: 100%;">
  </div>
</div>

<br><br>
### Preferred category per country
<div style="display: flex; align-items: flex-start;">
  <div style="flex: 1; padding-right: 20px;">
    <p style="font-size: 20px;">Now that we have the categories per beer, we can look at different geographical trends. The first one consist in analysing what is the preferred category per region. In order to do so, we split the data by
    region and did a multivariate linear regression with the different categories. We then kept the one
    with the highest coefficient.</p>
    <br>
    <img src="/data/prefered_cat_byCountry.png" style="width: 100%; height: 100%;">
    <br>
    <p style="font-size: 20px;"><br>How we can see, North america and Australia tends to prefer stouts beers (black beers) while China, India and South America tends to prefer Belgian beers and Europe is more on the sour side. It might
    be surprising to see that Belgians don’t prefer the Belgian beer. An explanation would be that since
    they have so many, they tend to have higher standards and therefore are more severe with this
    category than others. In grey are the countries that are not represented in the dataset.<br> <br> Another question that comes to mind is to find out if the local production is influenced by those preferences. In order to find it out, we first selected local breweries. The index that we chose to say if a brewery was local or not was to see if more than 50% of the reviews where made by local users. Then, we computed the average fraction for each category in each region and compared it to the
    global distribution:</p>
    <br>
    <img src="/data/tendancy_localBrew.png" style="width: 100%; height: 100%;">
    <br>
    <p style="font-size: 20px;"><br> The map shows different trends. The North and Central America, as well as China have a positive zscore while Europe’s brewery seems to be less interested by the preferred type of beer.<br> Another interesting comparison can be made between the local production and the most reviewed categories.</p>
    <br>
    <img src="/data/most_reviewed.png" style="width: 100%; height: 100%;">
    <br>
    <p style="font-size: 20px;"><br> With this indicator, the vast majority of the regions show now a positive z-index. The country with the lowest z-index is Island, which makes sense since it is, for physical reasons, a big importer of products.<br> Those results seem to show a correlation between the local breweries production and the local preferences but is there causality? And if yes, which side is influencing which side?</p>
    <p style="font-size: 20px;">To find answer to those questions, we decided to compare the time series of the following:</p>
    <ul>
        <li style="font-size: 20px;">&bull; The fraction of the different categories produced by breweries</li>
        <li style="font-size: 20px;">&bull; The fraction of the different categories of beer appearance on the market</li>
    </ul>
    <p style="font-size: 20px;"><br>The idea of such comparison is to find if on the global scale, we can find that the trend of one of the timeseries is following the trend of the other. <br> However, a problem appeared with this task: We don’t have the date of creation for each beer in our dataset. Therefore, we decided to take instead the date of the first review for each beer as an indicator of the period of creation. We then computed the time series by averaging the results on each quarter of year (for visual purposes) between the year 2002 and 2017 (due to highly unbalanced data outside of this timespan).</p>
    <p style="font-size: 20px;">As it can be seen on the different graphs, the trends are behaving very differently from one category to the other. It is then very difficult to see a general tendency of one fraction to follow the other and we might not have the means to tell with enough confidence that one fraction is causing the evolution of the other.<br> On a non-regional-related side, it is interesting to see that the more traditional categories (Brown, Wheat, Belgian, Lager) have been decreasing in attractiveness during the years 2010 while the Pale ales and sours have been on the rising. This could be explain by the explosion of small artisanal breweries that has been happening during the last decade.</p>
    <br>
    <img src="/data/time_series.jpg" style="width: 100%; height: 100%;">
    <br>
  </div>
</div>



