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
          "user_id":348242,
          "user_name":"Jack Doherty",
          "user_avatar_id":5,
          "avatar_link":"asset_url",
          "event_id":83848,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":12516,
          "social_media":"twitter",
          "social_username":"dohertyjackk",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/mvTHShbrmxS2",
          "playback_url":"asset_url.m3u8",
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":465731,
          "user_name":"worldoftshirts2001",
          "user_avatar_id":3,
          "avatar_link":"asset_url",
          "event_id":83893,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":5738,
          "social_media":"parti",
          "social_username":"worldoftshirts2001",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/he8vhFE098Ge",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":351819,
          "user_name":"officialsupercal",
          "user_avatar_id":7,
          "avatar_link":"asset_url",
          "event_id":83825,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":60,
          "social_media":"parti",
          "social_username":"officialsupercal",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/pQPooedoDjgV",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":593563,
          "user_name":"Oldies_Hits_Radio",
          "user_avatar_id":6,
          "avatar_link":null,
          "event_id":83870,
          "event_title":"Classic Hits",
          "event_file":"asset_url",
          "category_name":"Music",
          "viewers_count":51,
          "social_media":"parti",
          "social_username":"Oldies_Hits_Radio",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/9cNb4PD2VWYH",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      // Up to 100 Live Channels
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
          "user_id":348242,
          "user_name":"Jack Doherty",
          "user_avatar_id":5,
          "avatar_link":"asset_url",
          "event_id":83848,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":12516,
          "social_media":"twitter",
          "social_username":"dohertyjackk",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/mvTHShbrmxS2",
          "playback_url":"asset_url.m3u8",
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":465731,
          "user_name":"worldoftshirts2001",
          "user_avatar_id":3,
          "avatar_link":"asset_url",
          "event_id":83893,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":5738,
          "social_media":"parti",
          "social_username":"worldoftshirts2001",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/he8vhFE098Ge",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":351819,
          "user_name":"officialsupercal",
          "user_avatar_id":7,
          "avatar_link":"asset_url",
          "event_id":83825,
          "event_title":"I'm Live on Parti",
          "event_file":"asset_url",
          "category_name":"Other",
          "viewers_count":60,
          "social_media":"parti",
          "social_username":"officialsupercal",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/pQPooedoDjgV",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      {
          "user_id":593563,
          "user_name":"Oldies_Hits_Radio",
          "user_avatar_id":6,
          "avatar_link":null,
          "event_id":83870,
          "event_title":"Classic Hits",
          "event_file":"asset_url",
          "category_name":"Music",
          "viewers_count":51,
          "social_media":"parti",
          "social_username":"Oldies_Hits_Radio",
          "discord_discriminator":null,
          "channel_arn":"arn:aws:ivs:eu-west-1:455030909228:channel/9cNb4PD2VWYH",
          "playback_url":"asset_url.m3u8", //live-video.net (Amazon) URL with CORS header set to parti.com, needs to be proxied, media .ts files themselves are not CORS protected though
          "playback_auth_token":"asset_token"
      },
      // Up to 30 Live Channels
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
          "event_id":53474,
          "user_id":494426,
          "category_id":10,
          "event_title":"🎉",
          "event_description":"partintro ",
          "event_file":null,
          "event_start_ts":1748532120,
          "event_end_ts":1748575380,
          "livestream_visibility_type":"Public",
          "user_name":"TazMeraki",
          "avatar_link":null,
          "user_avatar_id":1,
          "livestream_recording":null,
          "total_viewers":null
      },
      {
          "event_id":63403,
          "user_id":457056,
          "category_id":21,
          "event_title":"PARTI BEACH",
          "event_description":"South Florida Events",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1748621100,
          "event_end_ts":1748660700,
          "livestream_visibility_type":"Public",
          "user_name":"pjmsky9",
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "user_avatar_id":2,
          "livestream_recording":null,
          "total_viewers":null
      },
      {
          "event_id":36260,
          "user_id":359640,
          "category_id":20,
          "event_title":"New site using Ai",
          "event_description":"p2ecalculator.site",
          "event_file":"https://https://assets.parti.com/asset.jpeg",
          "event_start_ts":1764436500,
          "event_end_ts":1764439200,
          "livestream_visibility_type":"Public",
          "user_name":"F7ASH",
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "user_avatar_id":11,
          "livestream_recording":null,
          "total_viewers":null
      },
      {
          "event_id":15207,
          "user_id":398350,
          "category_id":22,
          "event_title":"GET YOUR FREE PANELS",
          "event_description":"Download the FREE panels! Find the Link in profile",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1796020200,
          "event_end_ts":1796058060,
          "livestream_visibility_type":"Public",
          "user_name":"RJARIVI",
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "user_avatar_id":6,
          "livestream_recording":null,
          "total_viewers":null
      },
      // Up to 100 future scheduled streams
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
          "user_id":463000,
          "ordinal":0,
          "user_name":"SNEAKO",
          "user_avatar_id":2,
          "description":"Seek Truth Through Funny",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"telegram",
          "social_username":"realsneako",
          "discord_discriminator":null,
          "channels_joined":1,
          "members":25681
      },
      {
          "user_id":464860,
          "ordinal":1,
          "user_name":"MrBasedForever",
          "user_avatar_id":2,
          "description":"Welcome to MR. BASED’s Parti!",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"parti",
          "social_username":"MrBasedForever",
          "discord_discriminator":null,
          "channels_joined":7,
          "members":5528
      },
      {
          "user_id":462221,
          "ordinal":2,
          "user_name":"MoVlogs",
          "user_avatar_id":11,
          "description":"Let the Games Begin 💰",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"twitter",
          "social_username":"MovlogsCrypto",
          "discord_discriminator":null,
          "channels_joined":2,
          "members":2557
      },
      {
          "user_id":465731,
          "ordinal":3,
          "user_name":"worldoftshirts2001",
          "user_avatar_id":3,
          "description":"#huluchippendalesdance",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"parti",
          "social_username":"worldoftshirts2001",
          "discord_discriminator":null,
          "channels_joined":4,
          "members":18115
      },
      {
          "user_id":348242,
          "ordinal":4,
          "user_name":"Jack Doherty",
          "user_avatar_id":5,
          "description":"Follow me to watch all my new livestreams!",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"twitter",
          "social_username":"dohertyjackk",
          "discord_discriminator":null,
          "channels_joined":3,
          "members":34157
      },
      {
          "user_id":422974,
          "ordinal":6,
          "user_name":"JahBlessGames",
          "user_avatar_id":0,
          "description":"Spread love to d WORLD 💫",
          "avatar_link":"asset_url",
          "background_link":"asset_url",
          "social_media":"parti",
          "social_username":"JahBlessGames",
          "discord_discriminator":null,
          "channels_joined":110,
          "members":177
      },
      // lists all features creators
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
          "user_id":593563,
          "user_name":"Oldies_Hits_Radio",
          "user_avatar_id":6,
          "avatar_link":null,
          "livestream_visibility_type":"Public",
          "event_id":83870,
          "event_title":"Classic Hits",
          "avatar_link":"https://assets.parti.com/asset.png",
          "event_start_ts":1748467912,
          "event_end_ts":1748489531,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Music",
          "social_media":"parti",
          "social_username":"Oldies_Hits_Radio",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":85
      },
      {
          "user_id":464988,
          "user_name":"ClaireVoyant",
          "user_avatar_id":4,
          "avatar_link":"https://assets.parti.com/asset.png",
          "livestream_visibility_type":"Public",
          "event_id":83945,
          "event_title":"I'm Live on Parti",
          "avatar_link":"https://assets.parti.com/asset.png",
          "event_start_ts":1748485505,
          "event_end_ts":1748489256,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Other",
          "social_media":"parti",
          "social_username":"ClaireVoyant",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":16
      },
      {
          "user_id":615965,
          "user_name":"astralsworld",
          "user_avatar_id":4,
          "avatar_link":"https://assets.parti.com/asset.png",
          "livestream_visibility_type":"Public",
          "event_id":83930,
          "event_title":"Astrals World",
          "event_file":"https://assets.parti.com/asset.png",
          "event_start_ts":1748482973,
          "event_end_ts":1748488603,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Creative",
          "social_media":"discord",
          "social_username":"photobyastral_13781",
          "discord_discriminator":"0",
          "has_access_pass":false,
          "total_viewers":546
      },
      // Up to 15 recent livestreams
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
          "user_id":593563,
          "user_name":"Oldies_Hits_Radio",
          "user_avatar_id":6,
          "avatar_link":null,
          "livestream_visibility_type":"Public",
          "event_id":83870,
          "event_title":"Classic Hits",
          "event_file":"https://assets.parti.com/asset.png",
          "event_start_ts":1748467912,
          "event_end_ts":1748489531,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Music",
          "social_media":"parti",
          "social_username":"Oldies_Hits_Radio",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":85
      },
      {
          "user_id":347653,
          "user_name":"Jay Sylverhart",
          "user_avatar_id":8,
          "avatar_link":"https://assets.parti.com/asset.png",
          "livestream_visibility_type":"Public",
          "event_id":83873,
          "event_title":"Moogle Cafe - 80s Set",
          "event_file":"https://assets.parti.com/asset.png",
          "event_start_ts":1748476349,
          "event_end_ts":1748487695,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Music",
          "social_media":"discord",
          "social_username":"jaynair",
          "discord_discriminator":"0",
          "has_access_pass":false,
          "total_viewers":27
      },
      {
          "user_id":449352,
          "user_name":"ricviera",
          "user_avatar_id":0,
          "avatar_link":"https://assets.parti.com/asset.png",
          "livestream_visibility_type":"Public",
          "event_id":83926,
          "event_title":"Werk'n Wednesdays",
          "event_file":"https://assets.parti.com/asset.png",
          "event_start_ts":1748485101,
          "event_end_ts":1748485376,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Music",
          "social_media":"parti",
          "social_username":"ricviera",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":30
      },
      {
          "user_id":608513,
          "user_name":"Sourfarmer",
          "user_avatar_id":1,
          "avatar_link":"https://assets.parti.com/asset.png",
          "livestream_visibility_type":"Public",
          "event_id":83802,
          "event_title":"Random morning sesh",
          "event_file":"https://assets.parti.com/asset.png",
          "event_start_ts":1748440254,
          "event_end_ts":1748449063,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Music",
          "social_media":"twitter",
          "social_username":"sourfarmer",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":22
      },
      // Up to 15 recent livestreams
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
          "user_id":355536,
          "user_name":"Itz_J_Man",
          "user_avatar_id":5,
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "livestream_visibility_type":"Public",
          "event_id":83934,
          "event_title":"!!!Parti Time!!!",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1748483710,
          "event_end_ts":1748489787,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Gaming",
          "social_media":"parti",
          "social_username":"Itz_J_Man",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":105
      },
      {
          "user_id":617533,
          "user_name":"Dark Gorilla",
          "user_avatar_id":7,
          "avatar_link":null,
          "livestream_visibility_type":"Public",
          "event_id":83949,
          "event_title":"1st stream",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1748486661,
          "event_end_ts":1748487802,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Gaming",
          "social_media":"twitter",
          "social_username":"TalenJames13",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":38
      },
      {
          "user_id":353683,
          "user_name":"DrDamon",
          "user_avatar_id":2,
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "livestream_visibility_type":"Public",
          "event_id":83900,
          "event_title":"live on pari",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1748475446,
          "event_end_ts":1748485298,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Gaming",
          "social_media":"twitter",
          "social_username":"ItsDrDamon",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":56
      },
      // Up to 15 recent channels
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
          "user_id":348242,
          "user_name":"Jack Doherty",
          "user_avatar_id":5,
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "livestream_visibility_type":"Public",
          "event_id":73640,
          "event_title":"I'm Live on Parti",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1745433200,
          "event_end_ts":1745468523,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Other",
          "social_media":"twitter",
          "social_username":"dohertyjackk",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":93260
      },
      {
          "user_id":348242,
          "user_name":"Jack Doherty",
          "user_avatar_id":5,
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "livestream_visibility_type":"Public",
          "event_id":63781,
          "event_title":"I'm Live on Parti",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1742158084,
          "event_end_ts":1742180804,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"Other",
          "social_media":"twitter",
          "social_username":"dohertyjackk",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":76262
      },
      {
          "user_id":572676,
          "user_name":"IrelandBoys",
          "user_avatar_id":2,
          "avatar_link":"https://assets.parti.com/asset.jpeg",
          "livestream_visibility_type":"Public",
          "event_id":64022,
          "event_title":"I'm Live on Parti",
          "event_file":"https://assets.parti.com/asset.jpeg",
          "event_start_ts":1742241341,
          "event_end_ts":1742254988,
          "livestream_recording":"relative_vod_url.m3u8",
          "category_name":"IRL",
          "social_media":"parti",
          "social_username":"IrelandBoys",
          "discord_discriminator":null,
          "has_access_pass":false,
          "total_viewers":69600
      },
      // Up to 15 recently ended livestreams sorted by top views
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