# Designing YouTube or Netflix

Let's design a video sharing service like Youtube, where users will be able to upload/view/search videos.

## 1. What is YouTube?

YouTube is one of the most popular video sharing websites in the world. Users of the service can upload, view, share,
rate, and report videos as well as add comments on videos.

## 2. Requirements and Goals of the System

### Functional Requirements:

1. Users should be able to upload videos.
2. Users should be able to share and view videos.
3. Users should be able to perform searches based on video titles.
4. Our services should be able to record stats of videos, e.g., likes/dislikes, total number of views, etc.
5. Users should be able to add and view comments on videos.

### Non-Functional Requirements:

1. The system should be highly reliable, any video uploaded should not be lost.
2. The system should be highly available.
3. Users should have a real time experience while watching videos and should not feel any lag.

### Not in scope:

Video recommendations, most popular videos, channels, subscriptions, watch later, favorites, etc.

## 3. Capacity Estimation and Constraints

## 4. System APIs

## 5. High Level Design

## 6. Database Schema

## 7. Detailed Component Design

## 8. Metadata Sharding

## 9. Video Deduplication

## 10. Load Balancing

## 11. Cache

## 12. Content Delivery Network (CDN)

## 13. Fault Tolerance
We should use Consistent Hashing for distribution among database servers. Consistent hashing will not only help in replacing a dead server, but also help in distributing load among servers.