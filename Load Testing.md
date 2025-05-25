Great! Let's move forward with **PHASE 3 – PART 4: YouTube System Design**.

---

# ✅ **PHASE 3 – PART 4: Designing YouTube (Video Streaming Platform)**

---

## 🎯 Objective

Design a scalable platform like **YouTube** that supports:

* Video uploads & processing
* Video streaming (adaptive bitrate)
* Search & recommendations
* Like, comment, and subscribe
* Monetization (ads)
* User management and analytics

---

## 🧩 1. Functional Requirements

| Feature                       | Description                                             |
| ----------------------------- | ------------------------------------------------------- |
| 🎥 Upload videos              | Users upload videos                                     |
| 📺 Stream videos              | On-demand video playback                                |
| 📡 Adaptive bitrate streaming | High, medium, low resolution options based on bandwidth |
| 🔍 Search videos              | By title, tags, description                             |
| ❤️ Like, dislike, comment     | Engagement tools                                        |
| 🔔 Subscribe                  | Follow channels and get notified                        |
| 🧠 Recommendations            | Based on history, trending, and subscriptions           |

---

## 📈 2. Non-Functional Requirements

* **Scalability** – millions of uploads & streams daily
* **High Availability** – global access to content
* **Latency** – low startup latency on playback
* **Durability** – no data loss (video backups)
* **CDN support** for streaming
* **Security** – DRM, access controls

---

## 🏗️ 3. High-Level Architecture

```
         [Client Devices]
                |
                |<----> [CDN] <------+
                |                   |
          [Frontend Web/Mobile]     |
                |                   |
                |             [Streaming Servers]
                |                   |
         [Upload Service]-----------+
                |
         [Video Processing Service]
                |
         [Storage: S3 / Blob Store]
                |
         [Metadata DB]     [User DB]    [Search Index]
                |             |             |
         [Recommendation Engine]       [Analytics Engine]
```

---

## 📤 4. Video Upload & Processing Flow

1. **User uploads** a raw video file.
2. Video stored temporarily in blob storage (e.g., S3).
3. Asynchronously triggers **video processing pipeline**:

   * Transcode video to multiple resolutions (240p, 480p, 720p, 1080p)
   * Extract thumbnails
   * Generate metadata (duration, size, codec)
   * Store video chunks in storage/CDN
4. Update metadata DB and notify user upload is complete.

---

## 🛠 5. Transcoding

* Convert video to HLS/DASH format (chunked + adaptive bitrate)
* Example using FFMPEG:

```bash
ffmpeg -i input.mp4 -map 0 -preset fast -g 48 -sc_threshold 0 \
  -b:v:0 800k -b:v:1 300k -b:v:2 1200k \
  -s:v:0 640x360 -s:v:1 426x240 -s:v:2 1280x720 \
  -var_stream_map "v:0,a:0 v:1,a:1 v:2,a:2" \
  -master_pl_name master.m3u8 -f hls \
  -hls_time 6 -hls_playlist_type vod \
  output_%v.m3u8
```

---

## 🗃️ 6. Metadata Storage (Relational DB)

| Table: `videos`        |                         |
| ---------------------- | ----------------------- |
| video\_id              | UUID                    |
| user\_id               | Owner                   |
| title, description     | Metadata                |
| upload\_date           | Timestamp               |
| resolutions\_available | 240p, 480p, 720p, 1080p |
| views, likes, etc.     | Counters                |

---

## 📡 7. Video Streaming

* HLS/DASH protocol for streaming
* Segment length: 6 seconds
* CDN caches chunks closer to user
* Fallback: prefetching next segments

---

## 📂 8. Storage Strategy

| Type   | Storage                    | Use Case                   |
| ------ | -------------------------- | -------------------------- |
| Object | Amazon S3 / GCP Blob       | Original video, thumbnails |
| CDN    | Cloudflare, Akamai, Fastly | Serve HLS chunks to users  |
| DB     | PostgreSQL / MySQL         | Video metadata             |
| Search | Elasticsearch              | Title, tags, description   |
| Cache  | Redis / Memcached          | Hot videos, recent uploads |

---

## 🔍 9. Search and Recommendations

### Search

* Use **Elasticsearch** or Solr for full-text search
* Index title, description, tags, transcript (if available)

### Recommendation Engine

* Use ML models to suggest based on:

  * User watch history
  * Similar channel subscriptions
  * Trending videos
* Use collaborative filtering + content-based filtering

---

## 💰 10. Ads & Monetization

* Ad service to serve pre-roll, mid-roll ads
* Users eligible for ads after certain subscribers/views
* Integrate with 3rd-party ad networks (Google AdSense)

---

## 🧠 11. Analytics (Big Data)

* Track:

  * Views, likes, duration watched
  * Geo, device, user demographics
* Store in data lake (e.g., Amazon Redshift)
* Use for:

  * Improving recommendations
  * Revenue calculations
  * Detecting fraud or bot traffic

---

## 📦 12. Key Scalability Features

| Feature          | Solution                                 |
| ---------------- | ---------------------------------------- |
| Video processing | Distributed workers (Lambda, Kubernetes) |
| Storage          | S3 with tiered backups                   |
| Search           | Elasticsearch cluster                    |
| Delivery         | CDN with geo-distribution                |
| DB scaling       | Read replicas, sharding                  |
| Caching          | Redis layer for hot videos               |

---

## ⚖️ 13. Trade-offs & Challenges

| Concern                  | Design Trade-off                        |
| ------------------------ | --------------------------------------- |
| Cost vs Performance      | CDN is expensive, but essential for UX  |
| Video Quality vs Latency | Adaptive bitrate, pre-buffering         |
| Storage Growth           | Use cold storage for old, unused videos |
| Transcoding Time         | Use GPU-accelerated clusters            |

---

## 🛡️ 14. Security & Compliance

* DRM encryption
* Content moderation (auto + manual)
* Copyright detection using **Content ID**
* GDPR & COPPA compliance for user data

---

## 🧪 15. Testing & Monitoring

* Load test streaming servers
* Monitor latency and error rates
* AB testing new recommendation models
* Health checks and fallback for CDN failures

---

## ✅ Summary Cheatsheet

```
📥 Upload --> 🎞 Transcode --> 📦 Store in S3/CDN --> 📡 Stream via HLS/DASH
📚 Metadata in SQL, 🔎 Search in Elasticsearch
🧠 Recommendation Engine + Analytics in Data Warehouse
```

---

