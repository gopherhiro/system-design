## 1. Why do we need URL shortening?
Short links save a lot of space when displayed, printed, messaged, or tweeted. Additionally, users are less likely to mistype shorter URLs.


## 2. Requirements and Goals of the System
You should always clarify requirements at the beginning of the interview. Be sure to ask questions to find the exact scope of the system that the interviewer has in mind.

##### Functional Requirements:
1. Given a URL, our service should generate a shorter and unique alias of it. This is called a short link. This link should be short enough to be easily copied and pasted into applications.
2. When users access a short link, our service should redirect them to the original link.
3. Users should optionally be able to pick a custom short link for their URL.
4. Links will expire after a standard default timespan. Users should be able to specify the expiration time.

##### Non-Functional Requirements:
1. The system should be highly available. This is required because, if our service is down, all the URL redirections will start failing.
2. URL redirection should happen in real-time with minimal latency.
3. Shortened links should not be guessable (not predictable).

##### Extended Requirements:
1. Analytics; e.g., how many times a redirection happened?
2. Our service should also be accessible through REST APIs by other services.

## 3. Capacity Estimation and Constraints
Our system will be read-heavy. There will be lots of redirection requests compared to new URL shortenings. Let’s assume a 100:1 ratio between read and write.

Assuming, we will have 500M new URL shortenings per month, with 100:1 read/write ratio

##### Traffic estimates:

##### Storage estimates: 

##### Bandwidth estimates: 

##### Memory estimates: 

##### High-level estimates:

###### 数字单位
- 1T = 1000B
- 1B = 1000M
- 1M = 1000K

###### 容量单位
- 1PB = 1024TB
- 1TB = 1024GB
- 1GB = 1024MB
- 1MB = 1024KB
- 1KB = 1024 Bytes
- 1Bytes = 8 Bits

###### Tips
可以使用 Capacity Estimation and Constraints 对之前的项目进行复盘评估。

## 4. System APIs
Once we’ve finalized the requirements, it’s always a good idea to define the system APIs. This should explicitly state what is expected from the system.

createURL(api_dev_key, original_url, custom_alias=None, user_name=None, expire_date=None)
deleteURL(api_dev_key, url_key)

## 5. Database Design
Defining the DB schema in the early stages of the interview would help to understand the data flow among various components and later would guide towards data partitioning.

A few observations about the nature of the data we will store:

1. We need to store billions of records.
2. Each object we store is small (less than 1K).
3. There are no relationships between records—other than storing which user created a URL.
4. Our service is read-heavy.

###### Database Schema:
We would need two tables: one for storing information about the URL mappings and one for the user’s data who created the short link.


## 6. Basic System Design and Algorithm
The problem we are solving here is how to generate a short and unique key for a given URL.

##### a. Encoding actual URL

##### b. Generating keys offline


## 7. Data Partitioning and Replication

##### a. Range Based Partitioning
##### b. Hash-Based Partitioning

## 8. Cache
How much cache memory should we have? 
Which cache eviction policy would best fit our needs?
How can each cache replica be updated?

## 9. Load Balancer (LB)
1. Between Clients and Application servers
2. Between Application Servers and database servers
3. Between Application Servers and Cache servers

## 10. Purging or DB cleanup

we can slowly remove expired links and do a lazy cleanup.

渐进式数据清理

## 11. Telemetry
数据指标监控

## 12. Security and Permissions
Can users create private URLs or allow a particular set of users to access a URL?