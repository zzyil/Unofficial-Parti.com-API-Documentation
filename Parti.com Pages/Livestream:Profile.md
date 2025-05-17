# Parti.com Backend API Routes Livestream/Profile Pages
This guide lists key backend API routes for parti.com, focusing on user profile and livestream interactions, with demo cURL and WebSocket commands.

## HTTP API Routes (api-backend.parti.com)

### Get User by Social Media (Twitter)
Fetches Parti user information based on their Twitter username.

- **Method**: GET
- **Path**: `/parti_v2/profile/get_user_by_social_media/twitter/{social_media_username}`
- **Response**: JSON with user data
- **cURL Example** (Example with username KickBalthierGR):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/get_user_by_social_media/twitter/KickBalthierGR' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
353044
```

### Get User by Social Media (Discord)
Fetches Parti user information based on their Discord username.

- **Method**: GET
- **Path**: `/parti_v2/profile/get_user_by_social_media/discord/{social_media_username}`
- **Response**: JSON with user data
- **cURL Example** (Example with username drb666%230):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/get_user_by_social_media/discord/drb666%230' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
567503
```

### Get User Profile
Fetches profile information for a specific user.

- **Method**: GET
- **Path**: `/parti_v2/profile/user_profile/{user_id}`
- **Response**: JSON with user data
- **cURL Example** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/user_profile/353044' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
{
  "user_id": 353044,
  "user_name": "BalthierGR",
  "user_avatar_id": 1,
  "channels_joined": 869,
  "members": 749,
  "description": "🎉PARTI PARTNER 🎉 PARTI BOUNCER 🎉\r\nHello we are twin brothers from greece we love gaming music chatting...",
  "social_media": "twitter",
  "social_username": "KickBalthierGR"
}
```

### List Global Moderators
Fetches a list of global moderators. This appears to be an admin-related endpoint.

- **Method**: GET
- **Path**: `/parti_v2/profile/admin/global_mod/list`
- **Response**: JSON with moderator data
- **cURL Example**:

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/admin/global_mod/list' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
[
  {
    "user_id": 355293,
    "user_name": "Capt_Robs_Adventures",
    "social_media": "parti",
    "social_username": "Capt_Robs_Adventures"
  },
  {
    "user_id": 43460,
    "user_name": "Johndoe",
    "social_media": "parti",
    "social_username": "Johndoe"
  },
  {
    "user_id": 33,
    "user_name": "TheCreator",
    "social_media": "discord",
    "social_username": "TheCreator"
  }
]
```

### Get Livestream Channel Info for a User
Fetches livestream channel information for a specific user.

- **Method**: GET
- **Path**: `/parti_v2/profile/get_livestream_channel_info/{user_id}`
- **Response**: JSON with channel data
- **cURL Example (Offline User)** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/353044' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response (Offline User)**:

```json
{
  "status": "Public",
  "channel_info": {
    "channel": {
      "livestream_id": 7862,
      "user_id": 353044,
      "is_live": false
    },
    "visibility_type": "Public"
  },
  "is_streaming_live_now": false
}
```

- **cURL Example (Online User)** (Example with user_id 567503):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/get_livestream_channel_info/567503' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response (Online User)**:

```json
{
  "status": "Public",
  "channel_info": {
    "channel": {
      "livestream_id": 76436,
      "user_id": 567503,
      "is_live": true,
      "current_event_id": 80695
    },
    "stream": {
      "health": "HEALTHY",
      "state": "LIVE",
      "viewer_count": 470
    },
    "visibility_type": "Public",
    "livestream_event_info": {
      "event_name": "I'm Live on Parti"
    }
  },
  "is_streaming_live_now": true
}
```

### Get User Profile Feed
Fetches the profile feed for a specific user, limited to a certain number of items.

- **Method**: GET
- **Path**: `/parti_v2/profile/user_profile_feed/{user_id}?limit=5`
- **Response**: JSON with feed data
- **cURL Example** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/user_profile_feed/353044?limit=5' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
[
  {
    "feed_id": 92140,
    "user_id": 353044,
    "post_content": "Games and music",
    "event_id": 80669,
    "created_at": 1747444493
  },
  {
    "feed_id": 92008,
    "user_id": 353044,
    "post_content": "Games and Music",
    "event_id": 80553,
    "created_at": 1747401808
  },
  {
    "feed_id": 91899,
    "user_id": 353044,
    "post_content": "Games and Music",
    "event_id": 80415,
    "created_at": 1747358160
  }
]
```

### Get Livestream Moderators
Fetches the moderators for a specific user's livestream.

- **Method**: GET
- **Path**: `/parti_v2/profile/livestream/moderators/{user_id}`
- **Response**: JSON with moderator data
- **cURL Example** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/livestream/moderators/353044' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
[
  {
    "user_id": 351819,
    "user_name": "officialsupercal",
    "social_media": "parti",
    "social_username": "officialsupercal"
  },
  {
    "user_id": 353111,
    "user_name": "ApolloGR",
    "social_media": "parti",
    "social_username": "ApolloGR"
  },
  {
    "user_id": 354445,
    "user_name": "JennyM",
    "social_media": "parti",
    "social_username": "JennyM"
  }
]
```

### Get User Currency Info
Fetches currency-related information for a specific user.

- **Method**: GET
- **Path**: `/parti_v2/profile/user_currency_info/{user_id}`
- **Response**: JSON with currency data
- **cURL Example** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/user_currency_info/353044' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
[
  {
    "currency_address_id": 3429,
    "user_id": 353044,
    "blockchain_id": 4,
    "amount": "10000000",
    "pass_name": "AvP"
  }
]
```

### Get Pinned Message for User Profile
Fetches the pinned message for a specific user's profile.

- **Method**: GET
- **Path**: `/parti_v2/profile/pinned_message/{user_id}`
- **Response**: JSON with pinned message data
- **cURL Example (Offline User)** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/pinned_message/353044' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response (Offline User)**:

```json
[]
```

- **cURL Example (Online User)** (Example with user_id 567503):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/pinned_message/567503' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response (Online User)**:

```json
[["DBR",{
  "chat_id": 4441829,
  "user_id": 567503,
  "user_name": "DBR",
  "post_content": "$2 TTS h ttps://kickbot.com/tips/DBR6",
  "created_at": 1747304740
}]]
```

### Get User Profile Chat (Public)
Fetches public chat messages for a user's profile.

- **Method**: GET
- **Path**: `/parti_v2/profile/user_profile_chat/{user_id}/public`
- **Response**: JSON with chat messages
- **cURL Example** (Example with user_id 353044):

```bash
curl 'https://api-backend.parti.com/parti_v2/profile/user_profile_chat/353044/public' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Origin: https://parti.com' \
  -H 'Referer: https://parti.com/' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
  --compressed
```

- **Response**:

```json
[
  {
    "chat_id": 4470868,
    "user_id": 353044,
    "user_name": "BalthierGR",
    "post_content": "i will be on later ",
    "created_at": 1747444386
  },
  {
    "chat_id": 4470866,
    "user_id": 457269,
    "user_name": "BabbleChat",
    "post_content": "BalthierGR, You have leveled up the Streamers level to 2903!",
    "created_at": 1747444378
  },
  {
    "chat_id": 4470865,
    "user_id": 353044,
    "user_name": "BalthierGR",
    "post_content": "{\"channel_from_name\":\"BalthierGR\",\"channel_to_name\":\"Lionheart\"...}",
    "created_at": 1747444378
  }
]
```

## WebSocket API Connections (ws-backend.parti.com)
Use `wscat` or similar tools for WebSocket connections, not cURL.

### Subscribe to New Channel Live Notifications
Subscribes to notifications when a new channel goes live.

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

### Subscribe to Public Chat for a User
Subscribes to public chat messages for a specific user.

- **URL**: `wss://ws-backend.parti.com/`
- **wscat Example**:

```bash
wscat -c 'wss://ws-backend.parti.com/' \
  -H 'Origin: https://parti.com' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
```

- **Message to Send** (Example for user_id 353044):

```json
{"subscribe_options":{"ChatPublic":{"user_id":353044}}}
```

### Subscribe to Livestream Live Viewers Update
Subscribes to updates on the number of live viewers for a specific livestream.

- **URL**: `wss://ws-backend.parti.com/`
- **wscat Example**:

```bash
wscat -c 'wss://ws-backend.parti.com/' \
  -H 'Origin: https://parti.com' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
```

- **Message to Send** (Example for livestream_id 7862):

```json
{"jwt":null,"subscribe_options":{"LivestreamLiveViewersUpdate":{"livestream_id":7862}}}
```

## Notes
- Install `wscat` with `npm install -g wscat` for WebSocket connections.
- Some endpoints may require an `Authorization: Bearer YOUR_TOKEN_HERE` header for authentication.
- The Get User Profile Feed endpoint had an empty query parameter (&) in the HAR, likely a typo, and was corrected to include only `limit=5`.
- Video playback URLs (player.live-video.net, *.hls.live-video.net, watch.parti.com/ivs/) are part of AWS IVS and typically require tokens or signed URLs, not direct API integration.