# Parti.com Login API and hCaptcha Setup

This guide covers the login API for `parti.com` and how to set up the hCaptcha widget on the frontend to grab the `h-captcha-response` token needed for login.

## 1. hCaptcha Frontend Setup

To log in users, `parti.com` needs an hCaptcha token from a frontend widget. Here's how to set it up to capture the token and pass it to the login API.

- **hCaptcha Site Key**: `12b255be-3600-4fea-82b8-cf5e587e8866`
- **Goal**: Display the hCaptcha widget, grab the token when the user completes it, and include it in the login request.

### Steps to Set It Up

1. **Add the hCaptcha Script**:
   Drop the hCaptcha script into your HTML, either in the `<head>` or before `</body>`:

    ```html
    <script src="https://js.hcaptcha.com/1/api.js?render=explicit&onload=onHCaptchaApiLoad" async defer></script>
    ```

   - `render=explicit`: Stops the widget from loading automatically so your JavaScript can control it.
   - `onload=onHCaptchaApiLoad`: Calls a function when the script is ready.

2. **Set Up a Placeholder Element**:
   Add a `div` in your login form where the hCaptcha widget will show up:

    ```html
    <div id="hcaptcha-container-for-parti"></div>
    ```

3. **Add JavaScript**:
   Use this JavaScript to load the widget and handle the token:

    ```javascript
    let partiHCaptchaWidgetID;
    let hCaptchaTokenForPartiLogin = null;

    function onHCaptchaApiLoad() {
        renderPartiHCaptcha();
    }

    function renderPartiHCaptcha() {
        if (typeof hcaptcha === 'undefined') {
            return;
        }

        const hcaptchaContainer = document.getElementById('hcaptcha-container-for-parti');
        if (!hcaptchaContainer) {
            return;
        }

        partiHCaptchaWidgetID = hcaptcha.render(hcaptchaContainer, {
            sitekey: '12b255be-3600-4fea-82b8-cf5e587e8866',
            callback: function(token) {
                hCaptchaTokenForPartiLogin = token;
            }
        });
    }
    ```

4. **Use the Token for Login**:
   When the user submits the login form, include the `hCaptchaTokenForPartiLogin` in the request to `/parti_v2/auth/user_login` as the `token` field. Like this:

    ```javascript
    const loginPayload = {
        email: "user@example.com",
        password: "securepassword",
        token: hCaptchaTokenForPartiLogin
    };
    // Send loginPayload to https://api-backend.parti.com/parti_v2/auth/user_login via POST
    ```

## 2. User Login API

- **Method**: `POST`
- **URL**: `https://api-backend.parti.com/parti_v2/auth/user_login`
- **What It Does**: Logs in a user with their email, password, and hCaptcha token. Returns an access token if successful.
- **Headers**:
  - `Content-Type: application/json`
  - `Accept: application/json, text/plain, */*`
  - `Origin: https://parti.com`
  - `Referer: https://parti.com/`
- **Request Body**:

    ```json
    {
        "email": "YOUR_EMAIL_HERE",
        "password": "YOUR_PASSWORD_HERE",
        "token": "HCAPTCHA_TOKEN_OBTAINED_FROM_WEBSITE"
    }
    ```

- **Success Response**:

    ```json
    {
        "success": true,
        "data": {
            "access_token": "SAMPLE_JWT_TOKEN",
            "user_id": 123456
        }
    }
    ```

- **cURL Example**:

    ```bash
    curl -X POST 'https://api-backend.parti.com/parti_v2/auth/user_login' \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json, text/plain, */*' \
    -H 'Origin: https://parti.com' \
    -H 'Referer: https://parti.com/' \
    -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
    -d '{
        "email": "YOUR_EMAIL@example.com",
        "password": "YOUR_SECURE_PASSWORD",
        "token": "VALID_HCAPTCHA_TOKEN"
    }'
    ```

- **Notes**:
  - Swap out `YOUR_EMAIL@example.com`, `YOUR_SECURE_PASSWORD`, and `VALID_HCAPTCHA_TOKEN` with real values.
  - The hCaptcha token has to be fresh from solving the CAPTCHA on `parti.com`.

## 3. Get User Profile (After Login)

- **Method**: `GET`
- **URL**: `https://api-backend.parti.com/parti_v2/profile/user_profile`
- **What It Does**: Fetches the user’s profile info using the access token from the login.
- **Headers**:
  - `Authorization: Bearer <ACCESS_TOKEN>`
  - `Accept: application/json, text/plain, */*`
  - `Origin: https://parti.com`
  - `Referer: https://parti.com/`
- **Success Response**:

    ```json
    {
        "success": true,
        "data": {
            "id": 123456,
            "username": "user123",
            "email": "user@example.com",
            "first_name": null,
            "last_name": null,
            "profile_image_url": "https://assets.parti.com/default/profile.png",
            "cover_image_url": null,
            "bio": null,
            "is_verified_creator": false,
            "role_id": 30,
            "role_name": "User",
            "subscription_days_left": 0,
            "is_subscribed_with_trial": false,
            "telegram_id": 0,
            "balance": "0.00000000",
            "last_seen_ts": 0,
            "chat_settings": {
                "is_chat_sound_enabled": true,
                "is_display_chat_images": true,
                "is_display_chat_videos": true,
                "is_display_chat_gifs": true,
                "is_display_chat_avatars": true,
                "is_chat_auto_scroll_enabled": true,
                "is_emoticons_panel_enabled": false
            },
            "account_type": "user",
            "default_channel_slug": null,
            "profile_slug": "user123"
        }
    }
    ```

- **cURL Example**:

    ```bash
    ACCESS_TOKEN="PASTE_YOUR_ACCESS_TOKEN_HERE"
    curl -X GET 'https://api-backend.parti.com/parti_v2/profile/user_profile' \
    -H "Authorization: Bearer $ACCESS_TOKEN" \
    -H 'Accept: application/json, text/plain, */*' \
    -H 'Origin: https://parti.com' \
    -H 'Referer: https://parti.com/' \
    -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'
    ```

- **Notes**:
  - Replace `PASTE_YOUR_ACCESS_TOKEN_HERE` with the `access_token` from the `/auth/user_login` response.