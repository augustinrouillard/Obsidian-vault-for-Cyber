---
share: true
---

## Description
A flaw in the application's authentication workflow allows an attacker to completely bypass the Two-Factor Authentication (2FA) mechanism via Forced Browsing.

When a user enables 2FA, the application initializes a fully authenticated global session (generating a valid sessionid cookie) immediately after the username and password validation step, before the user provides a valid TOTP token. Because the application lacks strict server-side middleware access controls on other endpoints, a user (or an attacker with compromised credentials) can skip the 2FA verification page (/account/verification/) and directly access sensitive pages like the dashboard, banking services, and shop settings.

## Steps to Reproduce
1. Log into a pre-created user account where 2FA has been fully configured and activated.
2. Log out of the account to clear current session cookies.
3. Navigate to the login page and enter the valid username and password.
4. The server redirects you to the 2FA verification page (/account/2fa/setup/ or /account/verification/). Do not enter the 6-digit code.
5. In your browser's address bar, change the URL to the main dashboard: https://<ASSET_HOST>/account/ (or use a proxy like Burp Suite to request the endpoint with the freshly generated cookies).
6. Observe that the server grants full access to the dashboard with a 200 OK status code, completely bypassing the 2FA restriction.

## Impact
Authentication Bypass (CWE-287): The core principle of multi-factor authentication is broken. The application wrongly elevates privileges based on a single factor (knowledge) instead of enforcing both.

Loss of Confidentiality & Integrity: An attacker gaining access to the session can read sensitive user data (API keys, account history, personal information) and perform unauthorized actions (e.g., placing orders, tampering with user settings).

Proof of Concept
Unauthorized Request to Dashboard
By forcing the navigation to /account/ while stuck on the 2FA verification screen, the server improperly exposes the user dashboard:

```
HTTP
GET /account/ HTTP/2
Host: f134aa857e5d.3xploit.me
Cookie: csrftoken=sn55WMQ0ylcDVpr0WGQTomuBq6wzOodi; sessionid=m4gmkjrvclnp847mg4o8t6r8w0glbp41
Server Response
The server responds with a 200 OK status code and renders the full dashboard HTML instead of redirecting (302 Found) back to the 2FA verification page:
```
`
```
HTTP
HTTP/2 200 OK
Server: nginx
Content-Type: text/html; charset=utf-8
Vary: Cookie

<!DOCTYPE html>
<html lang="en">
<head>
    <title>V.R.C - Account</title>

<body class="vrc-body account-page">
    <h1 class="account-title">Welcome, TGV</h1>
```

-----

## POC

[[Before entering verification code.png|Before entering verification code.png]]
[[Http request.png|Http request.png]]
[[Http response.png|Http response.png]]
[[Granting access to community page.png|Granting access to community page.png]]