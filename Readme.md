# 📊 Instagram Influencers Dashboard (Tableau / Business Analyst Project)

### 🧠 Overview
This project analyzes top Instagram influencers using Tableau to visualize engagement trends, influencer rankings, and country-wise performance metrics.  
It provides insights into engagement rates, growth in post likes, and influencer reach across various regions.

### 🛠️ Tools Used
- **Tableau Public**
- **SQL**

### 📂 Dataset
The dataset contains information about top Instagram influencers, including:
| Column | Description |
|---------|--------------|
| rank | Rank of the influencer |
| channel_info | Username of the influencer |
| influence_score | Calculated influence score |
| posts | Number of posts |
| followers | Total followers |
| avg_likes | Average likes per post |
| 60_day_eng_rate | Engagement rate for the last 60 days |
| new_post_avg_like | Average likes on new posts |
| total_likes | Total likes on all posts |
| country | Influencer’s country |

---

### 📈 Key KPIs
- Total Followers
- Average Engagement Rate
- Average Likes per Post
- Growth Rate in New Post Likes
- Like-to-Follower Ratio

---

### 📊 Dashboard Insights
- **Engagement Rate per Country:** Highlights the countries with the highest influencer engagement.
- **Top 10 Influencers:** Lists the top accounts by influence score.
- **Growth in Post Likes:** Visualizes changes in audience engagement.
- **Geographical Analysis:** Displays influencer density across countries.


---

### 🧮 Calculated Fields (Tableau)
```tableau
// Engagement Rate
([avg_likes] / [followers]) * 100

// Growth Rate in New Post Likes
([new_post_avg_like] - [avg_likes]) / [avg_likes] * 100

// Like-to-Follower Ratio
[total_likes] / [followers]


<img width="1918" height="994" alt="Instagram Influencers Dashboard" src="https://github.com/user-attachments/assets/f519cf45-a02f-4ded-8188-933c1a995125" />

