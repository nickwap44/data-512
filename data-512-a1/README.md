# Data 512 - Assignment 1: Data Curation
Nicholas Wapstra

## Goal

The goal of this assignment was to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1st, 2008 to August 30th, 2020. The purpose was to practice working in the Jupyter Notebook environment using best practices for open research in design and implementation. This assignment has been designed to be fully reproducible by others, end-to-end.

## Data Sources
Data was collected from two API endpoints, the Legacy Pagecounts API and the Pageviews API.

1. The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from December 2007 through July 2016.
2. The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

The Wikimedia REST API terms of use can be found at this [location](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions).

## Data and Code for Replication
Source data from API queries (in .json format):
1. legacy_desktop-site_200801-201607.json
2. legacy_mobile-site_200801-201607.json
3. pageviews_desktop_201507-202008.json
4. pageviews_mobile-app_201507-202008.json
5. pageviews_mobile-web_201507-202008.json

Compiled dataset used for analysis:
en-wikipedia_traffic_200801-202008.csv

Code for data acquisition and analysis:
data-512-a1.ipynb

Final visualization:
data-512-a1.png

## Fields
The value of the fields from the final compiled dataset are as follows:
- year (int64): Provides the year of data collection
- month (int64): Provides the month of data collection
- pagecount_all_views (float64): Total views (desktop and mobile) from Legacy API
- pagecount_desktop_views (float64): Desktop views from Legacy API
- pagecount_mobile_views (float64): Mobile views from Legacy API
- pageview_all_views (float64): Total views (desktop, mobile app, and mobile web) from Pageviews API
- pageview_desktop_views (float64): Desktop views from Pageviews API
- pageview_mobile_views (float64): Mobile (app and web) views from Pageviews API

## Special Considerations
Data collected from the Pageviews API excludes crawlers, while data collected from the Legacy API does not. Mobile views data was not collected until 2014. Missing (or 0) values were listed as 0 in the dataset.
