# Parti.com Backend API Routes for the "Home/Start/Launch" Page

This guide lists the key API routes for the `parti.com` "Home/Start/Launch" page, updated with demo responses.

## HTTP API Routes (api-backend.parti.com)

1. **Get Livestream Event Categories**:
   Fetches categories for livestream events.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/livestream_calendar/events/categories`
   - **Response**: JSON with category data (e.g., `[{"category_id": 7, "name": "Gaming", "display_name": "Gaming"}, {"category_id": 10, "name": "Music", "display_name": "Music"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/livestream_calendar/events/categories' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {"category_id": 7, "name": "Gaming", "display_name": "Gaming"},
      {"category_id": 23, "name": "Crypto", "display_name": "CRYPTO"},
      {"category_id": 10, "name": "Music", "display_name": "Music"},
      {"category_id": 21, "name": "IRL", "display_name": "IRL"},
      {"category_id": 20, "name": "Alternative", "display_name": "Alternative"},
      {"category_id": 24, "name": "Casino", "display_name": "CASINO"},
      {"category_id": 22, "name": "Creative", "display_name": "Creative"},
      {"category_id": 1, "name": "Fitness", "display_name": "Fitness"},
      {"category_id": 25, "name": "AfterParti", "display_name": "AFTER PARTI"},
      {"category_id": 17, "name": "Hip Hop", "display_name": "Hip Hop"},
      {"category_id": 19, "name": "Fashion", "display_name": "Fashion"},
      {"category_id": 16, "name": "", "display_name": "Valorant"},
      {"category_id": 13, "name": "", "display_name": "Axie Infinity"},
      {"category_id": 14, "name": "", "display_name": "Wreck League"},
      {"category_id": 15, "name": "", "display_name": "Farlight 84"},
      {"category_id": 2, "name": "Beauty", "display_name": "Beauty"},
      {"category_id": 3, "name": "", "display_name": "Call of Duty"},
      {"category_id": 5, "name": "Yoga", "display_name": "Yoga"},
      {"category_id": 8, "name": "Podcast", "display_name": "Podcast"},
      {"category_id": 9, "name": "Tattoos", "display_name": "Tattoos"},
      {"category_id": 11, "name": "Other", "display_name": "Other"}
    ]
    ```

2. **Get Live Livestream Channel Info (Limit 100)**:
   Fetches info on up to 100 live livestream channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/live?limit=100&offset=0`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 567503, "user_name": "DBR", "viewers_count": 200}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/live?limit=100&offset=0' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 567503,
        "user_name": "DBR",
        "viewers_count": 200,
        "category_name": "Other",
        "event_title": "I'm Live on Parti"
      },
      {
        "user_id": 353044,
        "user_name": "BalthierGR",
        "viewers_count": 160,
        "category_name": "Gaming",
        "event_title": "Games and music"
      },
      {
        "user_id": 608513,
        "user_name": "Sourfarmer",
        "viewers_count": 18,
        "category_name": "Music",
        "event_title": "Heat is real Sesh"
      }
      // Up to 100 channels
    ]
    ```

3. **Get Live Livestream Channel Info (Limit 30)**:
   Fetches info on up to 30 live livestream channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/live?limit=30&offset=0`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 567503, "user_name": "DBR", "viewers_count": 200}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/live?limit=30&offset=0' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 567503,
        "user_name": "DBR",
        "viewers_count": 200,
        "category_name": "Other",
        "event_title": "I'm Live on Parti"
      },
      {
        "user_id": 353044,
        "user_name": "BalthierGR",
        "viewers_count": 160,
        "category_name": "Gaming",
        "event_title": "Games and music"
      },
      {
        "user_id": 612882,
        "user_name": "TrueBarrz",
        "viewers_count": 18,
        "category_name": "Music",
        "event_title": "TrueBarrz Music Mix"
      }
      // Up to 30 channels
    ]
    ```

4. **Get Livestream Calendar Events**:
   Fetches scheduled livestream events.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/livestream_calendar/events?offset=0&limit=100`
   - **Response**: JSON with event data (e.g., `[{"event_id": 80292, "event_title": "CSRTRS-18 MAY 25raw", "event_start_ts": 1747603500}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/livestream_calendar/events?offset=0&limit=100' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "event_id": 80292,
        "user_id": 601139,
        "category_id": 25,
        "event_title": "CSRTRS-18 MAY 25raw",
        "event_start_ts": 1747603500,
        "category_name": "AfterParti"
      },
      {
        "event_id": 63403,
        "user_id": 457056,
        "category_id": 21,
        "event_title": "PARTI BEACH",
        "event_start_ts": 1748621100,
        "category_name": "IRL"
      },
      {
        "event_id": 15207,
        "user_id": 398350,
        "category_id": 22,
        "event_title": "GET YOUR FREE PANELS",
        "event_start_ts": 1796020200,
        "category_name": "Creative"
      }
      // More events
    ]
    ```

5. **Get Featured Channels**:
   Fetches a list of featured channels.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/featured_channels`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 463000, "user_name": "SNEAKO"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/featured_channels' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 463000,
        "user_name": "SNEAKO",
        "members": 4340
      },
      {
        "user_id": 348242,
        "user_name": "Jack Doherty",
        "members": 3846
      },
      {
        "user_id": 601379,
        "user_name": "DigitalNas",
        "members": 10
      }
      // More featured channels
    ]
    ```

6. **Get Recent Livestream Channel Info (Default)**:
   Fetches recently ended livestreams within a time range, sorted by date. The `from_ts` and `to_ts` parameters specify the time range for filtering livestreams, using Unix timestamps (seconds since epoch). For example, `from_ts=1627948800` corresponds to August 3, 2021, and `to_ts=2229292800` corresponds to August 3, 2040. These parameters can often be omitted, as the API may default to a broad time range that includes all relevant livestreams.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 444522, "user_name": "ElementalMJ", "event_end_ts": 1747436206}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=false' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 444522,
        "user_name": "ElementalMJ",
        "event_id": 80739,
        "event_title": "I'm Live on Parti",
        "event_end_ts": 1747436206,
        "category_name": "Other",
        "total_viewers": 0
      },
      {
        "user_id": 355293,
        "user_name": "Capt_Robs_Adventures",
        "event_id": 80676,
        "event_title": "I'm Live on Parti",
        "event_end_ts": 1747434724,
        "category_name": "Other",
        "total_viewers": 132
      }
      // More recent livestreams
    ]
    ```

7. **Get Recent Livestream Channel Info (Category 10)**:
   Fetches recently ended livestreams for category 10 (Music). See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=10&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 608513, "user_name": "Sourfarmer", "category_name": "Music"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=10&offset=0&limit=15&top_views_sort=false' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 608513,
        "user_name": "Sourfarmer",
        "event_id": 80628,
        "event_title": "Just a chill guy sesh",
        "category_name": "Music",
        "total_viewers": 34
      },
      {
        "user_id": 593563,
        "user_name": "Oldies_Hits_Radio",
        "event_id": 80608,
        "event_title": "Classic Hits",
        "category_name": "Music",
        "total_viewers": 36
      },
      {
        "user_id": 612882,
        "user_name": "TrueBarrz",
        "event_id": 80417,
        "event_title": "Music Party",
        "category_name": "Music",
        "total_viewers": 30
      }
      // More music livestreams
    ]
    ```

8. **Get Recent Livestream Channel Info (Category 7)**:
   Fetches recently ended livestreams for category 7 (Gaming). See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=7&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 611713, "user_name": "Genxgaming0_1", "category_name": "Gaming"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=7&offset=0&limit=15&top_views_sort=false' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 611713,
        "user_name": "Genxgaming0_1",
        "event_id": 80642,
        "event_title": "doom the dark ages",
        "category_name": "Gaming",
        "total_viewers": 42
      },
      {
        "user_id": 43831,
        "user_name": "Chilly Dolphin",
        "event_id": 80495,
        "event_title": "Rust",
        "category_name": "Gaming",
        "total_viewers": 112
      },
      {
        "user_id": 353044,
        "user_name": "BalthierGR",
        "event_id": 80553,
        "event_title": "Games and Music",
        "category_name": "Gaming",
        "total_viewers": 90
      }
      // More gaming livestreams
    ]
    ```

9. **Get Recent Livestream Channel Info (Top Views Sort)**:
   Fetches recently ended livestreams, sorted by top views. See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=true`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 348242, "user_name": "Jack Doherty", "total_viewers": 93260}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&offset=0&limit=15&top_views_sort=true' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 348242,
        "user_name": "Jack Doherty",
        "event_id": 73640,
        "event_title": "I'm Live on Parti",
        "total_viewers": 93260,
        "event_end_ts": 1745468523
      },
      {
        "user_id": 572676,
        "user_name": "IrelandBoys",
        "event_id": 64022,
        "event_title": "I'm Live on Parti",
        "total_viewers": 69600,
        "event_end_ts": 1742254988
      },
      {
        "user_id": 463000,
        "user_name": "SNEAKO",
        "event_id": 78114,
        "event_title": "I'm Live on Parti",
        "total_viewers": 59565,
        "event_end_ts": 1746674059
      }
      // More high-view livestreams
    ]
    ```

10. **Get Recent Livestream Channel Info (No Category)**:
    Fetches recently ended livestreams without a specific category. See the `from_ts` and `to_ts` description in the "Get Recent Livestream Channel Info (Default)" section.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&offset=0&limit=15&top_views_sort=false`
    - **Response**: JSON with channel data (e.g., `[{"user_id": 444522, "user_name": "ElementalMJ"}]`)
    - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&offset=0&limit=15&top_views_sort=false' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

    - **Demo Response**:

    ```json
    [
      {
        "user_id": 444522,
        "user_name": "ElementalMJ",
        "event_id": 80739,
        "event_title": "I'm Live on Parti",
        "event_end_ts": 1747436206,
        "category_name": "Other",
        "total_viewers": 0
      },
      {
        "user_id": 355293,
        "user_name": "Capt_Robs_Adventures",
        "event_id": 80676,
        "event_title": "I'm Live on Parti",
        "event_end_ts": 1747434724,
        "category_name": "Other",
        "total_viewers": 132
      }
      // More uncategorized livestreams
    ]
    ```

11. **Get Asset Prices Info**:
    Fetches information about asset prices.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/assets_prices/info`
    - **Response**: JSON with asset price data (e.g., `[{"asset_id": 1, "price": 100.50}]`)
    - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/assets_prices/info' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

    - **Demo Response**:

    ```json
    [
      {
        "asset_type": "Crypto",
        "display_symbol": "BNB",
        "ticker": "binancecoin",
        "price": "645.66",
        "direction": "up",
        "price_diff": "0.00"
      },
      {
        "asset_type": "Crypto",
        "display_symbol": "BTC",
        "ticker": "bitcoin",
        "price": "103510",
        "direction": "up",
        "price_diff": "0.01"
      },
      {
        "asset_type": "Stock",
        "display_symbol": "TSLA",
        "ticker": "TSLA",
        "price": "340.34",
        "direction": "down",
        "price_diff": "0.63"
      }
      // More asset price data
    ]
    ```

12. **Get User Profile**:
    Fetches profile info for a specific user.

    - **Method**: `GET`
    - **Path**: `/parti_v2/profile/user_profile/{user_id}`
    - **Example Path**: `/parti_v2/profile/user_profile/123456`
    - **Response**: JSON with user data (e.g., `{"user_id": 123456, "user_name": "Inquisitive Mink", "bio": null}`)
    - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/user_profile/123456' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      --compressed
    ```

    - **Demo Response**:

    ```json
    {
      "user_id": 123456,
      "user_name": "Inquisitive Mink",
      "user_avatar_id": 9,
      "channels_joined": 0,
      "members": 1,
      "description": null,
      "social_media": "telegram",
      "social_username": "bmw_cmbk"
    }
    ```

## WebSocket API Connections (ws-backend.parti.com)

Use `wscat` or similar tools for WebSocket connections, not cURL.

1. **Subscribe to New Channel Live Notifications**:
   Get notifications when a new channel goes live.

   - **URL**: `wss://ws-backend.parti.com/`
   - **wscat Example**:

    ```bash
    wscat -c 'wss://ws-backend.parti.com/' \
      -H 'Origin: https://parti.com' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

   - **Message to Send**:

    ```json
    {"subscribe_options":{"NewChannelLiveNotify":{}}}
    ```

2. **Subscribe to Asset Price Refresh Notifications**:
   Get notifications for asset price updates.

   - **URL**: `wss://ws-backend.parti.com/`
   - **wscat Example**:

    ```bash
    wscat -c 'wss://ws-backend.parti.com/' \
      -H 'Origin: https://parti.com' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

   - **Message to Send**:

    ```json
    {"subscribe_options":{"AssetPriceRefreshNotify":{}}}
    ```

### Notes
- Install `wscat` with `npm install -g wscat` for WebSocket connections.
- Some endpoints may require authentication tokens not shown in these public-facing requests.
- Adjust timestamps or dynamic query parameters as needed for current use.
- The `Get User Profile` endpoint supports other user IDs (e.g., 234567, 345678).
- The `Get Livestream Calendar Events` endpoint had a misspelled URL in the terminal log (`li0`); the correct path is used here.