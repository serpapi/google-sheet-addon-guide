# Google Sheet Addon Guide
Documentation for Google Sheet Add-on for SerpApi
https://workspace.google.com/marketplace/app/serpapi_search_engine_results_and_ranks/562749385480

Status: This documentation is under development.

## Add-on introduction
This add-on allows to run localized search on Google, Bing and Baidu and more...
It makes easy to search or return the current ranking of your website or extract data from the search engine.

Video tutorial: https://youtu.be/GB0ulLtKQZg

This add-on offers:
 - 2 examples to get started
 - Custom function to return search result from Google, Bing, Baidu and more...
> Find the link the top coffee shop in Austin, TX listed on Google
=SERPAPI_RESULT("coffee", "google", "local_results", "link", "Austin, Texas, United States", "en", "us", 10, 0, "desktop", false)
 - Rank your web site on Google using localized search.
  =SERPAPI_GOOGLE_RANK("yourwebsite.com", "Coffee", "Austin, Texas, United States") returns rank of yourwebsite.com for Coffee.
 - Normalize location for Google and Bing. 
  =SERPAPI_LOCATION("Austin, TX") returns normalize location for Google e.g. "Austin, Texas, United States"

*Status: Production release*

This add-on leverages SerpApi service which provides the capability to search on Google from anywhere in the planet.
You need to obtain an API Key from SerpApi, then register the key. 
We offer a 15-day free trial and 5,000 searches.

## Menu 

The application offers 3 menus to quickly populate your sheet with meaningfull data.

## Custom functions

SerpApi add-on extends existing functions provided by Google Sheet. It enables to process about any data available from the search engine responses.

### SERPAPI_RESULT: Extract data from search engine result supported by SerpApi

This function enables to extract hierachical data from the result and display as a set of rows.
* 
* The selection mecanism works as following: 
* You must define a `query` includes the keywords you're looking for.
*
* The `opt_section` can take: organic_results, local_results, related_questions, people_also_search_for, knowledge_graph and more. Default is organic_results.
* Finally select a `opt_field` depending on the `opt_section`.
*  For `opt_section` == organic_results the posible values: position, title, link, displayed_link, date, snippet and more...
*
*  see the https://serpapi.com/playground for all possible values. 

alias: =SERPAPI_GOOGLE_RESULT(), =SERPAPI_BAIDU_RESULT(), =SERPAPI_BING_RESULT()

#### Example 1: Show the top 10 links for results / Coffee.
```=SERPAPI_RESULT("coffee", "google", "organic_results", "link")```

#### Example 2: Show the title of the top 10 local coffee shop around Austin, Texas.
```=SERPAPI_RESULT("coffee", "google", "local_results", "title", "Austin, Texas, United States")```

#### Example 3: Find the best coffee shop in Austin, TX with all the fields declared
```=SERPAPI_RESULT("coffee", "google", "local_results", "link", "Austin, Texas, United States", "en", "us", 10, 0, "desktop", false)```

### SERPAPI_RANK : Get search engine rank for a domain, a keyword, and an optional location

```
=SERPAPI_RANK("google", "starbuck.com", "Austin, Texas, United States")
```

*alias: SERPAPI_GOOGLE_RANK, SERPAPI_BING_RANK, SERPAPI_YAHOO_RANK*

### SERPAPI_LOCATION: Normalized location name based on Google location system.
```
=SERPAPI_LOCATION('Paris, France')
```
