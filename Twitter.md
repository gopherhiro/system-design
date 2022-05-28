# Designing Twitter
## 1. What is Twitter?
Twitter is an online social networking service where users post and read short 140-character messages called "tweets."

## 2. Requirements and Goals of the System
### Functional Requirements
1. Users should be able to post new tweets.
2. A user should be able to follow other users.
3. Users should be able to mark tweets as favorites.
4. The service should be able to create and display a user’s timeline consisting of top tweets from all the people the user follows.
5. Tweets can contain photos and videos.

### Non-functional Requirements
1. Our service needs to be highly available.
2. Acceptable latency of the system is 200ms for timeline generation.
3. Consistency

### Extended Requirements
1. Searching for tweets.
2. Replying to a tweet.
3. Trending topics – current hot topics/searches.
4. Tagging other users.
5. Tweet Notification.
6. Who to follow? Suggestions?
7. Moments.

## 3. Capacity Estimation and Constraints
## 4. System APIs
## 5. High Level System Design
## 6. Database Schema
## 7. Data Sharding
### Sharding based on UserID
### Sharding based on TweetID
### Sharding based on Tweet creation time

## 8. Cache
## 9. Timeline Generation
## 10. Replication and Fault Tolerance
Since our system is read-heavy, we can have multiple secondary database servers for each DB partition. Secondary servers will be used for read traffic only. All writes will first go to the primary server and then will be replicated to secondary servers. This scheme will also give us fault tolerance, since whenever the primary server goes down we can failover to a secondary server.

## 11. Load Balancing
## 12. Monitoring
1. New tweets per day/second, what is the daily peak?
2. Timeline delivery stats, how many tweets per day/second our service is delivering.
3. Average latency that is seen by the user to refresh timeline. 
   
By monitoring these counters, we will realize if we need more replication, load balancing, or caching.

