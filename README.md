# Unofficial Parti.com Documentation

## Parti.com API Usage

This portion is dedicated to Parti.com's utilisation of their own API on their official website. 

### Launch Page

[Full Documentation](/zzyil/Unofficial-Parti.com-API-Documentation/Parti.com%20Pages/Home%3AStart%3ALaunch.md)


1. **Get Livestream Event Categories**:
   Fetches categories for livestream events.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/livestream_calendar/events/categories`
   - **Response**: JSON with category data (e.g., `[{"category_id": 7, "name": "Gaming", "display_name": "Gaming"}, {"category_id": 10, "name": "Music", "display_name": "Music"}]`)


2. **Get Live Livestream Channel Info (Limit 100)**:
   Fetches info on up to 100 live livestream channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/live?limit=100&offset=0`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 567503, "user_name": "DBR", "viewers_count": 200}]`)


3. **Get Live Livestream Channel Info (Limit 30)**:
   Fetches info on up to 30 live livestream channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/live?limit=30&offset=0`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 567503, "user_name": "DBR", "viewers_count": 200}]`)
   

4. **Get Livestream Calendar Events**:
   Fetches scheduled livestream events.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/livestream_calendar/events?offset=0&limit=100`
   - **Response**: JSON with event data (e.g., `[{"event_id": 80292, "event_title": "CSRTRS-18 MAY 25raw", "event_start_ts": 1747603500}]`)
 
 
5. **Get Featured Channels**:
   Fetches a list of featured channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/featured_channels`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 463000, "user_name": "SNEAKO"}]`)
 
 
6. **Get Recent Livestream Channel Info (Default)**:
   Fetches recently ended livestreams within a time range, sorted by date. The `from_ts` and `to_ts` parameters specify the time range for filtering livestreams, using Unix timestamps (seconds since epoch). For example, `from_ts=1627948800` corresponds to August 3, 2021, and `to_ts=2229292800` corresponds to August 3, 2040. These parameters can often be omitted, as the API may default to a broad time range that includes all relevant livestreams.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 444522, "user_name": "ElementalMJ", "event_end_ts": 1747436206}]`)
 

7. **Get Recent Livestream Channel Info (Category 10)**:
   Fetches recently ended livestreams for category 10 (Music). See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=10&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 608513, "user_name": "Sourfarmer", "category_name": "Music"}]`)
 

8. **Get Recent Livestream Channel Info (Category 7)**:
   Fetches recently ended livestreams for category 7 (Gaming). See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=7&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 611713, "user_name": "Genxgaming0_1", "category_name": "Gaming"}]`)


9. **Get Recent Livestream Channel Info (Top Views Sort)**:
   Fetches recently ended livestreams, sorted by top views. See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=true`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 348242, "user_name": "Jack Doherty", "total_viewers": 93260}]`)
 

10. **Get Recent Livestream Channel Info (No Category)**:
    Fetches recently ended livestreams without a specific category. See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&offset=0&limit=15&top_views_sort=false`
    - **Response**: JSON with channel data (e.g., `[{"user_id": 444522, "user_name": "ElementalMJ"}]`)


11. **Get Asset Prices Info**:
    Fetches information about asset prices.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/assets_prices/info`
    - **Response**: JSON with asset price data (e.g., `[{"asset_id": 1, "price": 100.50}]`)


12. **Get User Profile**:
    Fetches profile info for a specific user.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/user_profile/{user_id}`
    - **Example Path**: `/parti_v2/profile/user_profile/123456`
    - **Response**: JSON with user data (e.g., `{"user_id": 123456, "user_name": "Inquisitive Mink", "bio": null}`)
