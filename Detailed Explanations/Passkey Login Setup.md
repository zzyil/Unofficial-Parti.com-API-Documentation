# Parti.com Private Key Authentication

This guide explains how to authenticate with `parti.com` using a private key.

## Private Key Authentication Setup

This method sends a private key to the API for authentication using a `POST` request.

### Steps to Set It Up

1. **Send the Private Key Authentication Request**:
   Send the private key in a `POST` request to authenticate.

   - **Method**: `POST`
   - **URL**: `https://api-backend.parti.com/parti_v2/auth/user_login_private_key`
   - **Key Headers**:
     - `Content-Type: application/json`
     - `Accept: application/json, text/plain, */*`
     - `Origin: https://parti.com`
     - `Referer: https://parti.com/`
   - **Request Body**:

    ```json
    {
      "private_key": "YOUR_PRIVATE_KEY"
    }
    ```

   - **Response**:
     - Status: `200 OK`
     - Headers:
       - `Access-Control-Allow-Origin: *`
       - `Content-Type: application/json`
     - Body: Returns a JSON response with a session token and user data.
     - Demo Response:

      ```json
      {
        "user_id": 123456,
        "role_id": 30,
        "jwt": "SAMPLE_JWT_TOKEN"
      }
      ```

   **cURL Example**:

    ```bash
    curl -X POST \
      'https://api-backend.parti.com/parti_v2/auth/user_login_private_key' \
      -H 'Accept: application/json, text/plain, */*' \
      -H 'Content-Type: application/json' \
      -H 'Origin: https://parti.com' \
      -H 'Referer: https://parti.com/' \
      -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36' \
      -d '{"private_key":"YOUR_PRIVATE_KEY"}' \
      --compressed
    ```

### How It Works

1. The client sends a `POST` request with the private key in the JSON payload to `https://api-backend.parti.com/parti_v2/auth/user_login_private_key`.
2. The server verifies the key and returns a session token and user data if successful.
3. All communication uses HTTPS for security.

### Notes
- Replace `YOUR_PRIVATE_KEY` with the actual private key for testing.
- The `--compressed` flag in cURL handles gzip encoding if used.
- The endpoint `/parti_v2/auth/user_login_private_key` is specific to private key authentication.