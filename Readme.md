INSERT INTO influencers_clean
SELECT
    rank,
    channel_info,
    influence_score,

    -- Convert posts
    CASE
        WHEN posts LIKE '%k' THEN CAST(REPLACE(posts, 'k','') AS DECIMAL(12,2)) * 1000
        WHEN posts LIKE '%m' THEN CAST(REPLACE(posts, 'm','') AS DECIMAL(12,2)) * 1000000
        WHEN posts LIKE '%b' THEN CAST(REPLACE(posts, 'b','') AS DECIMAL(12,2)) * 1000000000
        ELSE CAST(posts AS DECIMAL(12,2))
    END AS posts,

    -- Followers
    CASE
        WHEN followers LIKE '%k' THEN CAST(REPLACE(followers, 'k','') AS DECIMAL(12,2)) * 1000
        WHEN followers LIKE '%m' THEN CAST(REPLACE(followers, 'm','') AS DECIMAL(12,2)) * 1000000
        WHEN followers LIKE '%b' THEN CAST(REPLACE(followers, 'b','') AS DECIMAL(12,2)) * 1000000000
        ELSE CAST(followers AS DECIMAL(12,2))
    END AS followers,

    -- Avg likes
    CASE
        WHEN avg_likes LIKE '%k' THEN CAST(REPLACE(avg_likes, 'k','') AS DECIMAL(12,2)) * 1000
        WHEN avg_likes LIKE '%m' THEN CAST(REPLACE(avg_likes, 'm','') AS DECIMAL(12,2)) * 1000000
        ELSE CAST(avg_likes AS DECIMAL(12,2))
    END AS avg_likes,

    -- Engagement rate (% to decimal)
    CAST(REPLACE(`60_day_eng_rate`, '%','') AS DECIMAL(6,4)) / 100 AS eng_rate,

    -- New post avg likes
    CASE
        WHEN new_post_avg_like LIKE '%k' THEN CAST(REPLACE(new_post_avg_like, 'k','') AS DECIMAL(12,2)) * 1000
        WHEN new_post_avg_like LIKE '%m' THEN CAST(REPLACE(new_post_avg_like, 'm','') AS DECIMAL(12,2)) * 1000000
        ELSE CAST(new_post_avg_like AS DECIMAL(12,2))
    END AS new_post_avg_like,

    -- Total likes
    CASE
        WHEN total_likes LIKE '%k' THEN CAST(REPLACE(total_likes, 'k','') AS DECIMAL(20,2)) * 1000
        WHEN total_likes LIKE '%m' THEN CAST(REPLACE(total_likes, 'm','') AS DECIMAL(20,2)) * 1000000
        WHEN total_likes LIKE '%b' THEN CAST(REPLACE(total_likes, 'b','') AS DECIMAL(20,2)) * 1000000000
        ELSE CAST(total_likes AS DECIMAL(20,2))
    END AS total_likes,

    COALESCE(country, 'Unknown') AS country

FROM influencers_raw;
