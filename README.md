# Crypto News Dataset

**135k Cryptocurrency news fetched from Cryptopanic.com**
Perfect for Data Analysis projects.

Using their Api you can only fetch 200 news for each filter.

News are provided both in Excel and MySQL dump

These news are related to 400 highest ranked coins from coinmarketcap.com. News are labled with positive, negative, important and ... by users. Some news are related to 1 coins, some are related to multiple coins and some of them are not related to any specific coin.

Daily candlestick price data is also provided for most of currencies (not all). Fetched from https://www.alphavantage.co/

---
**News Count for high ranked coins:**
| code | count | minDatetime | maxDatetime |
| :-- | :-- | :-- | :-- |
| BTC | 8575 | 9/29/2017 13:30 | 12/8/2023 5:35 |
| ETH | 6368 | 9/23/2017 10:00 | 12/8/2023 5:09 |
| ADA | 3217 | 1/11/2018 21:35 | 12/7/2023 21:00 |
| XRP | 3136 | 12/13/2017 16:00 | 12/7/2023 19:00 |
| SHIB | 2668 | 5/10/2021 10:02 | 12/7/2023 23:00 |
| DOGE | 2598 | 2/18/2018 10:00 | 12/8/2023 2:54 |
| SOL | 2586 | 2/10/2021 20:02 | 12/8/2023 4:56 |
| MATIC | 1751 | 5/22/2019 19:06 | 12/8/2023 0:00 |
| BNB | 1430 | 11/27/2018 17:17 | 12/7/2023 19:54 |
| USDT | 1415 | 1/27/2018 23:43 | 12/8/2023 2:00 |
| LINK | 1404 | 2/28/2020 13:00 | 12/7/2023 15:00 |
| AVAX | 1367 | 1/24/2021 22:15 | 12/8/2023 0:00 |
| DOT | 1349 | 8/29/2020 8:39 | 12/7/2023 11:39 |
| TRX | 1336 | 1/8/2018 6:00 | 12/7/2023 10:24 |
| FTT | 1246 | 4/16/2020 5:02 | 12/7/2023 14:27 |
```
SELECT t3.code, COUNT(t1.id) AS cnt, MIN(t1.newsDatetime) AS minDatetime, MAX(t1.newsDatetime) AS maxDatetime
FROM cryptopanic_news t1
         JOIN news__currency t2 ON t1.id = t2.newsId
         JOIN currency t3 ON t2.currencyId = t3.id
GROUP BY t3.code
ORDER BY cnt DESC;
```

---
Database Diagram:

![image](https://user-images.githubusercontent.com/38767606/179568621-dfb1e10a-db7a-4a11-8e20-220747c1d616.png)

---
News Example:

![image](https://user-images.githubusercontent.com/38767606/179569521-e1cef289-49f8-4ede-9548-6d0937bb318f.png)
