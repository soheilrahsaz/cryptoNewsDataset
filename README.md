# Crypto News Dataset

**165k Cryptocurrency news fetched from Cryptopanic.com**
Perfect for Data Analysis projects.

Using their Api you can only fetch 200 news for each filter.

News are provided both in Csv(Excel friendly) and MySQL dump

These news are related to 430 highest ranked coins from coinmarketcap.com. News are labled with positive, negative, important and ... by users. Some news are related to 1 coins, some are related to multiple coins and some of them are not related to any specific coin.


---
**News Count for high ranked coins:**
| code | cnt | minDatetime | maxDatetime |
| :--- | :--- | :--- | :--- |
| BTC | 17745 | 2017-09-29 13:30:08 | 2024-09-24 04:43:45 |
| ETH | 12354 | 2017-09-23 10:00:42 | 2024-09-24 04:43:45 |
| SOL | 6044 | 2021-02-10 20:02:39 | 2024-09-24 04:43:45 |
| ADA | 4865 | 2018-01-11 21:35:52 | 2024-09-23 17:00:07 |
| XRP | 4815 | 2017-12-13 16:00:22 | 2024-09-24 04:43:45 |
| SHIB | 4211 | 2021-05-10 10:02:46 | 2024-09-23 19:44:10 |
| DOGE | 4183 | 2018-02-18 10:00:05 | 2024-09-23 19:44:10 |
| USDT | 3728 | 2018-01-27 23:43:00 | 2024-09-24 00:30:30 |
| MATIC | 2606 | 2019-05-22 19:06:25 | 2024-09-24 00:30:30 |
| BNB | 2262 | 2018-11-27 17:17:02 | 2024-09-23 16:57:47 |
| LINK | 2083 | 2020-02-28 13:00:30 | 2024-09-23 17:55:47 |
| AVAX | 2044 | 2021-01-24 22:15:44 | 2024-09-23 16:15:33 |
| TRX | 2010 | 2018-01-08 06:00:21 | 2024-09-23 17:08:00 |
| DOT | 1936 | 2020-08-29 08:39:09 | 2024-09-23 21:30:11 |
| UNI | 1809 | 2020-09-21 08:58:52 | 2024-09-23 15:02:29 |

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
