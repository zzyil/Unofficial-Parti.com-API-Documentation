# Parti.com Backend API Routes for VOD Pages

This guide lists key backend API routes for `parti.com`, focusing on video-on-demand pages, livestream interactions, and user profiles, with demo cURL and WebSocket commands.

## Video Page (HTML Document)

1. **Video Page**: Retrieves the HTML page for a specific video.

   - **Method**: `GET`
   - **Path**: `/video/{video_id}`
   - **Response**: HTML content (binary output warning)
   - **cURL Example** (Example with video_id `80892`):

    ```bash
    curl -X GET 'https://parti.com/video/80892' \
      -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8' \
      -H 'Accept-Encoding: gzip, deflate, br, zstd' \
      -H 'Accept-Language: de-DE,de;q=0.9,en-US;q=0.8,en;q=0.7' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

   - **Demo Response**: HTML content (binary output warning)

## HTTP API Routes (api-backend.parti.com)

The base URL for these APIs is `https://api-backend.parti.com/parti_v2`

2. **Get Livestream Channel Info (Specific User/Channel)**: Retrieves information about a specific livestream channel or user's channel.

   - **Method**: `GET`
   - **Path**: `/profile/get_livestream_channel_info/{user_or_channel_id}`
   - **Response**: JSON with channel data
   - **cURL Example** (Example with user_or_channel_id `614111`):

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/614111' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Accept-Encoding: gzip, deflate, br, zstd' \
      -H 'Accept-Language: de-DE,de;q=0.9,en-US;q=0.8,en;q=0.7' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
    {
      "status": "Public",
      "channel_info": {
        "channel": {
          "livestream_id": 116272,
          "user_id": 614111,
          "playback_url": "https://f89c1a12071a.eu-west-1.playback.live-video.net/..."
        }
      }
    }
    ```

3. **Get Recent Livestream Channel Info (Specific Video ID)**: Retrieves information about a recent livestream by video ID.

   - **Method**: `GET`
   - **Path**: `/profile/get_livestream_channel_info/recent/{video_id}`
   - **Response**: JSON with livestream data
   - **cURL Example** (Example with video_id `80892`):

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent/80892' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
    {
      "user_id": 465731,
      "user_name": "worldoftshirts2001",
      "event_id": 80892,
      "event_title": "I'm Live on Parti",
      "total_viewers": 776
    }
    ```

4. **Get Live Livestream Channels**: Retrieves a list of currently live livestream channels.

   - **Method**: `GET`
   - **Path**: `/profile/get_livestream_channel_info/live?limit=100&offset=0`
   - **Response**: JSON with channel data
   - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/live?limit=100&offset=0' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
    [
      {
        "user_id": 465731,
        "user_name": "worldoftshirts2001",
        "event_id": 80896,
        "viewers_count": 2360
      },
      {
        "user_id": 567503,
        "user_name": "DBR",
        "event_id": 80695,
        "viewers_count": 560
      }
    ]
    ```

5. **Get Chat Settings**: Retrieves chat settings for the authenticated user.

   - **Method**: `GET`
   - **Path**: `/profile/chat_settings/{user_id}`
   - **Response**: JSON with chat settings
   - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/chat_settings/465731' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
	{
		"user_id":465731,
		"show_timestamp":false,
		"username_color":"#FAC94C",
		"user_badges":[],
		"settings_hint_shown":false,
		"require_follow_to_chat":false
}
    ```

6. **Get User Profile**: Retrieves public profile information for a given user.

   - **Method**: `GET`
   - **Path**: `/profile/user_profile/{user_id}`
   - **Response**: JSON with user data
   - **cURL Example** (Example with user_id `465731`):

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/user_profile/465731' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
    {
      "user_id": 465731,
      "user_name": "worldoftshirts2001",
      "description": "#huluchippendalesdance",
      "members": 4751
    }
    ```

7. **Get Livestream Calendar Event Categories**: Retrieves categories for livestream calendar events.

   - **Method**: `GET`
   - **Path**: `/profile/livestream_calendar/events/categories`
   - **Response**: JSON with category data
   - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/livestream_calendar/events/categories' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

   - **Demo Response**:

    ```json
    [
      {"category_id": 7, "name": "Gaming"},
      {"category_id": 23, "name": "Crypto"},
      {"category_id": 10, "name": "Music"}
    ]
    ```

8. **Get Available Creator Passes for a User**: Retrieves available creator passes for a specific user.

   - **Method**: `GET`
   - **Path**: `/profile/get_creator_passes_available/{user_id}`
   - **Response**: JSON with creator pass data
   - **cURL Example** (Example with user_id `614111`):

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/get_creator_passes_available/614111' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      -H 'Authorization: Bearer <YOUR_JWT_TOKEN>'
    ```

   - **Demo Response**:

    ```json
    []
    ```

9. **Get Unread User Profile Messages**: Retrieves a count or list of unread messages for the authenticated user.

   - **Method**: `GET`
   - **Path**: `/profile/user_profile_message/unread`
   - **Response**: JSON with message data
   - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/user_profile_message/unread' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      -H 'Authorization: Bearer <YOUR_JWT_TOKEN>'
    ```

   - **Demo Response**:

    ```json
{
		"unread_message_count":0
	}
    ```

10. **Get Followed User Profiles**: Retrieves a list of user profiles that the authenticated user is following.

    - **Method**: `GET`
    - **Path**: `/profile/user_profile_following`
    - **Response**: JSON with followed user data
    - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/user_profile_following' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      -H 'Authorization: Bearer <YOUR_JWT_TOKEN>'
    ```

    - **Demo Response**:

    ```json
    [614120,465731]
    ```

11. **Get Recent Livestreams by User ID**: Retrieves recent livestreams, filterable by user ID and with pagination.

    - **Method**: `GET`
    - **Path**: `/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&by_user_id=465731&offset=0&limit=10`
    - **Response**: JSON with livestream data
    - **cURL Example**:

    ```bash
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/recent?sort_by_date_desc=true&by_user_id=465731&offset=0&limit=10' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    ```

    - **Demo Response**:

    ```json
    [
      {
        "user_id": 465731,
        "event_id": 80892,
        "event_title": "I'm Live on Parti",
        "total_viewers": 776
      },
      {
        "user_id": 465731,
        "event_id": 80894,
        "event_title": "I'm Live on Parti",
        "total_viewers": 0
      }
    ]
    ```

## Video Streaming API (watch.parti.com)

12. **Get Master HLS Playlist**: Retrieves the master HLS playlist listing available video qualities.

    - **Method**: `GET`
    - **Path**: `/ivs/v1/{account_id}/{channel_id}/{year}/{month}/{day}/{hour}/{minute}/{stream_id}/media/hls/master.m3u8`
    - **Response**: M3U8 playlist
    - **cURL Example**:

    ```bash
    curl -X GET 'https://watch.parti.com/ivs/v1/455030909228/he8vhFE098Ge/2025/5/17/7/19/9saEZCu7T6dG/media/hls/master.m3u8' \
      -H 'Accept: application/x-mpegURL, application/vnd.apple.mpegurl, application/json, text/plain' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

    - **Demo Response**:

    ```m3u8
    #EXTM3U
    #EXT-X-STREAM-INF:BANDWIDTH=3691379,RESOLUTION=1920x1080
    1080p/playlist.m3u8
    #EXT-X-STREAM-INF:BANDWIDTH=630000,RESOLUTION=640x360
    360p30/playlist.m3u8
    ```

13. **Get Quality-Specific HLS Playlist**: Retrieves the HLS playlist for a specific video quality, listing video segments.

    - **Method**: `GET`
    - **Path**: `/ivs/v1/{account_id}/{channel_id}/{year}/{month}/{day}/{hour}/{minute}/{stream_id}/media/hls/{quality}/playlist.m3u8`
    - **Response**: M3U8 playlist
    - **cURL Example** (Example with quality `360p30`):

    ```bash
    curl -X GET 'https://watch.parti.com/ivs/v1/455030909228/he8vhFE098Ge/2025/5/17/7/19/9saEZCu7T6dG/media/hls/360p30/playlist.m3u8' \
      -H 'Accept: application/x-mpegURL, application/vnd.apple.mpegurl, application/json, text/plain' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

    - **Demo Response**:

    ```m3u8
    #EXTM3U
    #EXT-X-VERSION:3
    #EXT-X-TARGETDURATION:10
    #EXTINF:10.000,
    0.ts
    #EXTINF:10.000,
    1.ts
    ```

14. **Get Video Segment**: Retrieves an actual video segment.

    - **Method**: `GET`
    - **Path**: `/ivs/v1/{account_id}/{channel_id}/{year}/{month}/{day}/{hour}/{minute}/{stream_id}/media/hls/{quality}/{segment_name}.ts`
    - **Response**: Binary video data (MPEG-TS, binary output warning)
    - **cURL Example** (Example with segment_name `1`):

    ```bash
    curl -X GET 'https://watch.parti.com/ivs/v1/455030909228/he8vhFE098Ge/2025/5/17/7/19/9saEZCu7T6dG/media/hls/1080p/1.ts' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

    - **Demo Response**: Binary video data (MPEG-TS, binary output warning)

## WebSocket API (ws-backend.parti.com)

16. **WebSocket Connection**: Used for real-time communication (chat, notifications).

    - **URL**: `wss://ws-backend.parti.com/`
    - **wscat Example**:

    ```bash
    wscat -c "wss://ws-backend.parti.com/" \
      -H "Origin: https://parti.com" \
      -H "User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36"
    ```

    - **Messages to Send**:

      - **Authenticate & Subscribe to Inbox**:

        ```json
        {
          "jwt": "<YOUR_JWT_TOKEN>",
          "subscribe_options": {
            "Inbox": {}
          }
        }
        ```

      - **Subscribe to Livestream Live Notifications**:

        ```json
        {
          "jwt": "<YOUR_JWT_TOKEN>",
          "subscribe_options": {
            "LivestreamLive": {}
          }
        }
        ```

    - **Demo Response**: Server pushes JSON messages for subscribed topics

### Notes
- Install `wscat` with `npm install -g wscat` for WebSocket connections.
- Many endpoints require authentication via an `Authorization: Bearer <YOUR_JWT_TOKEN>` header for HTTP requests or a valid JWT in WebSocket messages.
- Video streaming URLs (e.g., `watch.parti.com/ivs/`) are part of AWS IVS and use short-lived tokens or signed parameters, not suitable for direct API integration.
- Handle potential Cloudflare challenges when using these APIs programmatically.