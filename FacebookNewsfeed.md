# Designing Facebook’s Newsfeed

## 1. What is Facebook’s newsfeed?
It is a compilation of a complete scrollable version of your friends’ and your life story from photos, videos, locations, status updates, and other activities.

For any social media site you design - Twitter, Instagram, or Facebook - you will need some newsfeed system to display updates from friends and followers.

## 2. Requirements and Goals of the System
### Functional requirements:
1. Newsfeed will be generated based on the posts from the people, pages, and groups that a user follows.
2. A user may have many friends and follow a large number of pages/groups.
3. Feeds may contain images, videos, or just text.
4. Our service should support appending new posts as they arrive to the newsfeed for all active users.

### Non-functional requirements:
1. Our system should be able to generate any user’s newsfeed in real-time - maximum latency seen by the end user would be 2s.
2. A post shouldn’t take more than 5s to make it to a user’s feed assuming a new newsfeed request comes in.

## 3. Capacity Estimation and Constraints
### Traffic estimates:
### Storage estimates:

## 4. System APIs
getUserFeed(api_dev_key, user_id, since_id, count, max_id, exclude_replies)

## 5. Database Design

## 6. High Level System Design
### Feed generation
### Feed publishing

## 7. Detailed Component Design
### a. Feed generation
### b. Offline generation for newsfeed

## 8. Feed Ranking
A better ranking system can significantly improve itself by constantly evaluating if we are making progress in user stickiness, retention, ads revenue, etc.

## 9. Data Partitioning