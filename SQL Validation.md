Data validation using SQL aims to ensure that the values displayed on the dashboard are accurate and correct. I use SQL Database Management to validation my own dashboard.

## Total Views on Youtube
```sql
SELECT SUM(Views) AS Total_Views FROM youtube_spotify;
```
| Total_Views |
| -------------------- |
| 1355328195506          |

## Total Stream on Spotify
```sql
SELECT SUM(Stream) AS Total_Stream FROM youtube_spotify;
```
| Total_Stream |
| -------------------- |
| 1790600460734          |

## Average Likes on Youtube
```sql
SELECT AVG(Likes) AS Average_Likes FROM youtube_spotify;
```
| Average_Likes |
| -------------------- |
| 600869             |

## Engagement Rate on Youtube
```sql
SELECT (SUM(Likes)+SUM(Comments))/SUM(Views)*100 AS Engagement_Rate FROM youtube_spotify;
```
| Engagement_Rate |
| -------------------- |
| 0.66           |

## Top 10 Artist by Views on Youtube
```sql
SELECT
  Artist AS Artist,
  SUM(Views) AS Total_Views
FROM youtube_spotify GROUP BY Artist
ORDER BY Total_Views DESC
LIMIT 10;
```
| Artist | Total_Views |
| -------------------- | -------------------- |
| Ethiopia| 13053 |


## Top 10 Track by Stream on Spotify
```sql
SELECT
  Track AS Track,
  SUM(Stream) AS Total_Stream
FROM youtube_spotify GROUP BY Track
ORDER BY Total_Stream DESC
LIMIT 10;
```
| Track | Total_Stream |
| -------------------- | -------------------- |
| Ethiopia| 13053 |

## Daily Trend for Total Orders
```sql
SELECT
  day AS Day,
  SUM(transaction_qty) AS Total_Orders
FROM coffee_sales GROUP BY day;
```
| Day | Total_Orders |
| -------------------- | -------------------- |
| Sunday	| 29627  |
| Monday	| 30715 |
| Tuesday	| 29882 |
| Wednesday	| 30051 |
| Thursday	| 30659 |
| Friday	| 30639 |
| Saturday	| 29083 |

## Hourly Trend for Total Orders
```sql
SELECT
  hour AS Hour,
  SUM(transaction_qty) AS Total_Orders
FROM coffee_sales GROUP BY hour;
```
| Hour | Total_Orders |
| -------------------- | -------------------- |
| 6	| 6726 |
| 7	| 19044 |
| 8	| 24675 |
| 9	| 24715 |
| 10	| 26089 |
| 11	| 13835 |
| 12	| 12553 |
| 13	| 12272 |
| 14	| 12748 |
| 15	| 12753 |
| 16	| 12689 |
| 17	| 12554 |

## Sales by Store Location
```sql
SELECT
  store_location AS Store_Location,
  SUM(total_bill) AS Total_Revenue
FROM coffee_sales GROUP BY store_location;
```
| Store_Location | Total_Revenue |
| -------------------- | -------------------- |
| Astoria	| 213373.71 |
| Hell's Kitchen	| 211472.72 |
| Lower Manhattan	| 209060.05 |

## Sales by Product Category
```sql
SELECT
  product_category AS Product_Category,
  SUM(total_bill) AS Total_Revenue
FROM coffee_sales GROUP BY product_category;
```
| Product_Category | Total_Revenue |
| -------------------- | -------------------- |
| Bakery	| 82315.64 |
| Chocolate	| 76823.64 |
| Coffee	| 269952.45 |
| Syrup	| 8408.8 |
| Tea	| 196405.95 |

## Total Orders by Size
```sql
SELECT
  size AS Size_Product,
  SUM(transaction_qty) AS Total_Orders
FROM coffee_sales GROUP BY size;
```
| Size_Product | Total_Orders |
| -------------------- | -------------------- |
| Large	| 82951 |
| Regular	| 91887 |
| Small	| 35818 |


| Brazilian| 13012 |
| Columbian Medium Roast| 12920 |
| Our Old Time Diner Blend| 12891 |
| Jamaican Coffee River| 12431 |

## Bottom 5 Best Seller by Total Orders
```sql
SELECT
  product_detail AS Product_Detail,
  SUM(transaction_qty) AS Total_Orders
FROM coffee_sales GROUP BY product_detail
ORDER BY Total_Orders ASC
LIMIT 5;
```
| Product_Detail | Total_Orders |
| -------------------- | -------------------- |
| Chili Mayan	| 148 |
| Oatmeal Scone	| 1820 |
| Ginger Biscotti	| 1836 |
| Almond Croissant	| 1911 |
| Chocolate Chip Biscotti	| 1924 |
