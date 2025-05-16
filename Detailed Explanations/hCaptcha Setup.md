# Parti.com hCaptcha Frontend Setup

This guide shows how to set up the hCaptcha widget on your frontend for `parti.com` to grab the `h-captcha-response` token needed for the login request.

- **hCaptcha Site Key**: `12b255be-3600-4fea-82b8-cf5e587e8866`
- **Goal**: Display the hCaptcha widget, capture the token when the user completes it, and pass it to the login API.

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
        console.log("hCaptcha API ready for parti.com");
        renderPartiHCaptcha();
    }

    function renderPartiHCaptcha() {
        if (typeof hcaptcha === 'undefined') {
            console.error("hCaptcha object not found. API might not be loaded.");
            return;
        }

        const hcaptchaContainer = document.getElementById('hcaptcha-container-for-parti');
        if (!hcaptchaContainer) {
            console.error("hCaptcha container element not found.");
            return;
        }

        partiHCaptchaWidgetID = hcaptcha.render(hcaptchaContainer, {
            sitekey: '12b255be-3600-4fea-82b8-cf5e587e8866',
            theme: 'light',
            size: 'normal',
            callback: function(token) {
                console.log("hCaptcha challenge solved. Token received:", token);
                hCaptchaTokenForPartiLogin = token;
            },
            'expired-callback': function() {
                console.log("hCaptcha token expired.");
                hCaptchaTokenForPartiLogin = null;
            },
            'error-callback': function(errorCode) {
                console.error("hCaptcha error:", errorCode);
                hCaptchaTokenForPartiLogin = null;
            }
        });
        console.log("hCaptcha widget rendered with ID:", partiHCaptchaWidgetID);
    }
    ```

4. **Use the Token**:
   When the user submits the login form, include the `hCaptchaTokenForPartiLogin` in the JSON payload sent to `https://api-backend.parti.com/parti_v2/auth/user_login` as the `token` field. Like this:

    ```javascript
    const loginPayload = {
        email: "user@example.com",
        password: "securepassword",
        token: hCaptchaTokenForPartiLogin
    };
    // Send loginPayload to https://api-backend.parti.com/parti_v2/auth/user_login via POST
    ```

### How It Works

1. The page loads, and the hCaptcha `api.js` script is fetched.
2. `onHCaptchaApiLoad` runs, triggering `renderPartiHCaptcha`.
3. `hcaptcha.render()` shows the widget using the site key and sets up a callback.
4. The user solves the CAPTCHA in the `hcaptcha-container-for-parti` div.
5. hCaptcha verifies it with `api.hcaptcha.com`.
6. If successful, the callback function gets the `h-captcha-response` token.
7. Your JavaScript stores the token in `hCaptchaTokenForPartiLogin`.
8. When the user submits the login form, the token is sent with the email and password to the backend (`/parti_v2/auth/user_login`).

The `parti.com` backend verifies the token with hCaptcha’s `/siteverify` endpoint using their secret key. Your frontend’s job is to show the widget with the right site key and grab the token when the user completes it.