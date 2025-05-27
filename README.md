# Crypto News Dataset

**216k Cryptocurrency news fetched from Cryptopanic.com**

News are provided both in CSV (Excel-friendly) and MySQL dump

These news are related to 660 highest ranked coins from coinmarketcap.com. News are labled with positive, negative, important and ... by users. Some news are related to 1 coins, some are related to multiple coins and some of them are not related to any specific coin.

**Update**

Full description and real source URL are provided for news after 2021 with more than 3 votes. Full description for all news is comming soon!

---
**News Count for high-ranked coins:**
| code | cnt | minDatetime | maxDatetime |
| :--- | :--- | :--- | :--- |
| BTC | 26065 | 2017-09-29 13:30:08 | 2025-05-24 07:07:14 |
| ETH | 18097 | 2017-09-23 10:00:42 | 2025-05-24 06:27:01 |
| SOL | 10564 | 2021-02-10 20:02:39 | 2025-05-24 04:35:18 |
| XRP | 7718 | 2017-12-13 16:00:22 | 2025-05-24 07:38:26 |
| ADA | 6482 | 2018-01-11 21:35:52 | 2025-05-23 18:07:00 |
| DOGE | 6378 | 2018-02-18 10:00:05 | 2025-05-24 06:06:07 |
| USDT | 6172 | 2018-01-27 23:43:00 | 2025-05-24 05:42:55 |
| SHIB | 5750 | 2021-05-10 10:02:46 | 2025-05-23 21:16:42 |
| BNB | 3415 | 2018-11-27 17:17:02 | 2025-05-24 01:00:34 |
| LINK | 3034 | 2020-02-28 13:00:30 | 2025-05-23 18:07:00 |
| MATIC | 3011 | 2019-05-22 19:06:25 | 2025-05-23 22:22:33 |
| TRX | 2953 | 2018-01-08 06:00:21 | 2025-05-24 02:20:36 |
| AVAX | 2848 | 2021-01-24 22:15:44 | 2025-05-23 21:35:18 |
| USDC | 2608 | 2019-01-25 15:14:37 | 2025-05-23 21:27:00 |
| UNI | 2512 | 2020-09-21 08:58:52 | 2025-05-23 23:00:12 |

```
SELECT t3.code, COUNT(t1.id) AS cnt, MIN(t1.newsDatetime) AS minDatetime, MAX(t1.newsDatetime) AS maxDatetime
FROM cryptopanic_news t1
         JOIN news__currency t2 ON t1.id = t2.newsId
         JOIN currency t3 ON t2.currencyId = t3.id
GROUP BY t3.code
ORDER BY cnt DESC;
```

---
### Database Diagram
![CryptoNewsDataset (1)](https://github.com/user-attachments/assets/eda48fcc-c944-429f-9416-f8ebc6309af5)

---
### News Example

![image](https://github.com/user-attachments/assets/94937ac1-3be7-4197-9fd1-96bce3dce647)

---
### Projects Using This Dataset
**Crypto AI Assist RAG with Cassandra**

A Retrieval-Augmented Generation (RAG) application that integrates **Spring AI** and **Apache Cassandra**'s Vector Search to enable semantic search over crypto news.
This project uses the news and vote data from this dataset to generate embeddings, perform natural language queries, and rerank results based on user sentiment.

[View the project on GitHub](https://github.com/soheilrahsaz/crypto-news-rag)

[Read the blog post](https://medium.com/@soheilrahsaz.sr/building-a-rag-application-with-crypto-news-apache-cassandra-and-spring-ai-6115ad5ca75e)
