# Crypto News Dataset

**155k Cryptocurrency news fetched from Cryptopanic.com**
Perfect for Data Analysis projects.

Using their Api you can only fetch 200 news for each filter.

News are provided both in Csv(Excel friendly) and MySQL dump

These news are related to 430 highest ranked coins from coinmarketcap.com. News are labled with positive, negative, important and ... by users. Some news are related to 1 coins, some are related to multiple coins and some of them are not related to any specific coin.


---
**News Count for high ranked coins:**
| code | cnt | minDatetime | maxDatetime |
| :--- | :--- | :--- | :--- |
| BTC | 14540 | 2017-09-29 13:30:08 | 2024-07-12 08:58:20 |
| ETH | 10299 | 2017-09-23 10:00:42 | 2024-07-12 08:19:33 |
| SOL | 4684 | 2021-02-10 20:02:39 | 2024-07-12 08:19:33 |
| ADA | 4260 | 2018-01-11 21:35:52 | 2024-07-12 07:41:22 |
| XRP | 4202 | 2017-12-13 16:00:22 | 2024-07-12 08:00:00 |
| SHIB | 3640 | 2021-05-10 10:02:46 | 2024-07-12 07:18:35 |
| DOGE | 3628 | 2018-02-18 10:00:05 | 2024-07-12 07:18:35 |
| USDT | 2653 | 2018-01-27 23:43:00 | 2024-07-12 07:00:24 |
| MATIC | 2279 | 2019-05-22 19:06:25 | 2024-07-12 07:39:09 |
| BNB | 1959 | 2018-11-27 17:17:02 | 2024-07-11 21:00:51 |
| LINK | 1849 | 2020-02-28 13:00:30 | 2024-07-11 21:38:51 |
| AVAX | 1784 | 2021-01-24 22:15:44 | 2024-07-11 21:00:00 |
| DOT | 1730 | 2020-08-29 08:39:09 | 2024-07-12 06:24:59 |
| TRX | 1652 | 2018-01-08 06:00:21 | 2024-07-11 23:10:13 |
| UNI | 1580 | 2020-09-21 08:58:52 | 2024-07-12 00:00:27 |

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
