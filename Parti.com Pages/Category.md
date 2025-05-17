# Parti.com Backend API Routes for "Categories" Pages

This guide lists the API routes used by the categories overview pages on `parti.com`.

## HTTP API Routes (api-backend.parti.com)

1. **Get Recent Livestream Channel Info (Categories NaN and 7)**:
   Fetches recently ended livestreams, filtered by categories (NaN, 7), sorted by date.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&categories=7&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 603610, "user_name": "ironway"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&categories=7&offset=0&limit=15&top_views_sort=false' \
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
        "user_id": 603610,
        "user_name": "ironway",
        "event_id": 80836,
        "event_title": "Knicks Advance 2 ECF",
        "category_name": "IRL",
        "total_viewers": 0
      },
      {
        "user_id": 446876,
        "user_name": "DaCabbageManCan",
        "event_id": 80827,
        "event_title": "I'm Live on Parti",
        "category_name": "Other",
        "total_viewers": 32
      },
      {
        "user_id": 441539,
        "user_name": "GrandpaGamer61",
        "event_id": 80721,
        "event_title": "I'm Live on Parti",
        "category_name": "Other",
        "total_viewers": 126
      }
    ]
    ```

2. **Get Recent Livestream Channel Info (Categories NaN, 7, 7)**:
   Fetches recently ended livestreams, filtered by categories (NaN, 7, 7), sorted by date.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&categories=7&categories=7&offset=0&limit=15&top_views_sort=false`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 603610, "user_name": "ironway"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&from_ts=1627948800&to_ts=2229292800&followed_only=false&categories=NaN&categories=7&categories=7&offset=0&limit=15&top_views_sort=false' \
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
        "user_id": 603610,
        "user_name": "ironway",
        "event_id": 80836,
        "event_title": "Knicks Advance 2 ECF",
        "category_name": "IRL",
        "total_viewers": 0
      },
      {
        "user_id": 446876,
        "user_name": "DaCabbageManCan",
        "event_id": 80827,
        "event_title": "I'm Live on Parti",
        "category_name": "Other",
        "total_viewers": 32
      },
      {
        "user_id": 441539,
        "user_name": "GrandpaGamer61",
        "event_id": 80721,
        "event_title": "I'm Live on Parti",
        "category_name": "Other",
        "total_viewers": 126
      }
    ]
    ```

3. **Get Live Livestream Channel Info (Category 7, Limit 12)**:
   Fetches live livestream channels, filtered by category 7 (Gaming), limit 12.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/get_livestream_channel_info/live?limit=12&offset=0&categories=7`
   - **Response**: JSON with channel data (e.g., `[{"user_id": 459442, "user_name": "CyberFoxNexus"}]`)
   - **cURL Example**:

    ```bash
    curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/live?limit=12&offset=0&categories=7' \
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
        "user_id": 459442,
        "user_name": "CyberFoxNexus",
        "event_id": 80794,
        "event_title": "Games & music",
        "category_name": "Gaming",
        "viewers_count": 38
      },
      {
        "user_id": 597832,
        "user_name": "Gonwitharose",
        "event_id": 80837,
        "event_title": "SOMEPLACE NEAR HELL",
        "category_name": "Gaming",
        "viewers_count": 36
      },
      {
        "user_id": 613177,
        "user_name": "nopulpnature",
        "event_id": 80663,
        "event_title": "Friday Stream!",
        "category_name": "Gaming",
        "viewers_count": 20
      }
    ]
    ```

4. **Get Livestream Event Categories**:
   Fetches livestream event categories.

   - **Method**: `GET`
   - **Path**: `/parti_v2/profile/livestream_calendar/events/categories`
   - **Response**: JSON with category data (e.g., `[{"category_id": 7, "name": "Gaming"}]`)
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
      {
        "category_id": 7,
        "name": "Gaming",
        "display_name": "Gaming"
      },
      {
        "category_id": 23,
        "name": "Crypto",
        "display_name": "CRYPTO"
      },
      {
        "category_id": 10,
        "name": "Music",
        "display_name": "Music"
      },
      {
        "category_id": 21,
        "name": "IRL",
        "display_name": "IRL"
      }
    ]
    ```

## WebSocket API Connections (ws-backend.parti.com)

Use `wscat` or similar tools for WebSocket connections, not cURL.

1. **Subscribe to New Channel Live Notifications**:
   Subscribes to notifications for new live channels.

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

### Notes
- Install `wscat` with `npm install -g wscat` for WebSocket connections.
- Timestamps (`from_ts=1627948800`, `to_ts=2229292800`) are hardcoded (Aug 3, 2021 to Aug 3, 2040); adjust for current data.
- `categories=NaN` may be ignored or have specific backend meaning.
- Repeated `categories` parameters may be treated as an array or take the last value.