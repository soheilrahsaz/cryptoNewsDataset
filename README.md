# Crypto News Dataset

**174k Cryptocurrency news fetched from Cryptopanic.com**
Perfect for Data Analysis projects.

Using their Api you can only fetch 200 news for each filter.

News are provided both in Csv(Excel friendly) and MySQL dump

These news are related to 430 highest ranked coins from coinmarketcap.com. News are labled with positive, negative, important and ... by users. Some news are related to 1 coins, some are related to multiple coins and some of them are not related to any specific coin.


---
**News Count for high ranked coins:**
| code | cnt | minDatetime | maxDatetime |
| :--- | :--- | :--- | :--- |
| BTC | 20576 | 2017-09-29 13:30:08 | 2025-01-07 18:32:36 |
| ETH | 14173 | 2017-09-23 10:00:42 | 2025-01-07 17:21:25 |
| SOL | 7234 | 2021-02-10 20:02:39 | 2025-01-07 18:24:57 |
| XRP | 5691 | 2017-12-13 16:00:22 | 2025-01-07 17:39:29 |
| ADA | 5448 | 2018-01-11 21:35:52 | 2025-01-07 17:03:30 |
| DOGE | 4794 | 2018-02-18 10:00:05 | 2025-01-07 17:14:22 |
| SHIB | 4650 | 2021-05-10 10:02:46 | 2025-01-07 17:14:22 |
| USDT | 4474 | 2018-01-27 23:43:00 | 2025-01-07 17:36:18 |
| MATIC | 2822 | 2019-05-22 19:06:25 | 2025-01-01 06:00:47 |
| BNB | 2608 | 2018-11-27 17:17:02 | 2025-01-07 17:30:00 |
| LINK | 2415 | 2020-02-28 13:00:30 | 2025-01-07 17:05:16 |
| AVAX | 2347 | 2021-01-24 22:15:44 | 2025-01-07 15:34:00 |
| TRX | 2310 | 2018-01-08 06:00:21 | 2025-01-07 17:30:00 |
| DOT | 2139 | 2020-08-29 08:39:09 | 2025-01-06 17:21:39 |
| UNI | 2075 | 2020-09-21 08:58:52 | 2025-01-07 15:30:00 |

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
![CryptoNewsDataset](https://github.com/user-attachments/assets/a95aec3b-d420-489c-9472-6f4d36284366)

---
News Example:

![image](https://user-images.githubusercontent.com/38767606/179569521-e1cef289-49f8-4ede-9548-6d0937bb318f.png)
