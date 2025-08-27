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
| Ed Sheeran	| 15460207769 | 
| Katy Perry	| 13120632075 | 
| Charlie Puth	| 12167594191 | 
| Luis Fonsi	| 11627983924 | 
| Justin Bieber	| 10990787061 | 
| Daddy Yankee	| 10868279671 | 
| Bruno Mars	| 10231841530 | 
| Macklemore & Ryan Lewis	| 10122055560 | 
| Coldplay	| 9997277884 | 
| Calvin Harris	| 9758476139 | 

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
| Can't Hold Us (feat. Ray Dalton)	| 5225629104 | 
| The Middle	| 4566882832 | 
| Shallow	| 4008677756 | 
| Feels (feat. Pharrell Williams, Katy Perry & Big Sean)	| 3925148532 | 
| Blinding Lights	| 3386520288 | 
| Shape of You	| 3362005201 | 
| Perfect	| 3239168518 | 
| El Ultimo AdiÃ³s - Varios Artistas Version	| 3225629221 | 
| See You Again (feat. Charlie Puth)	| 3042509108 | 
| Swalla (feat. Nicki Minaj & Ty Dolla $ign)	| 3031746321 | 

## Album Type on Spotify
```sql
SELECT
  Album_type AS Album_Type,
  COUNT(ID_Number) AS Total_Track
FROM youtube_spotify GROUP BY Album_type;
```
| Album_Type | Total_Track |
| -------------------- | -------------------- |
| album	| 11035 | 
| compilation	| 642 | 
| single	| 2567 | 

## Album Type Engagement
```sql
SELECT
  Album_type AS Album_Type,
  AVG(Views) AS Avg_Views,
  AVG(Likes) AS Avg_Likes,
  AVG(Comments) AS Avg_Comments
FROM youtube_spotify GROUP BY Album_type;
```
| Album_Type | Avg_Views | Avg_Likes | Avg_Comments |
| ---------------- | ----------------- | --------------- | --------------- |
| album	| 98481005.95	| 597859.95	| 25645.01 | 
| compilation	| 81727619.43	| 508615.65	| 17708.28 | 
| single	| 84192116.55	| 636878.31	| 25300.12 | 

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
