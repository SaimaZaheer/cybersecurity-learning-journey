# Password Reset Broken Logic

## Lab Overview

**Platform:** PortSwigger Web Security Academy
**Category:** Authentication
**Vulnerability:** Broken Password Reset Logic
**Tools:** Burp Suite, Proxy, Repeater

## Objective

The objective of this lab was to exploit a flaw in the application's password-reset functionality and gain access to another user's account.

## Methodology

I first logged into the account provided by the lab and used the **Forgot Password** functionality to initiate a password reset.

After requesting the reset, I accessed the password-reset link that was sent through the lab's email functionality. I then used **Burp Suite Proxy** to inspect the HTTP requests generated during the password-reset process.

### 1. Capturing the Password Reset Request

I located the password-reset request in **HTTP History** and sent it to **Burp Repeater** so that I could manually modify and resend the request.

The request contained a reset token that was being used as part of the password-reset process.

### 2. Testing the Reset Token

I modified the request in Repeater by removing the reset token from the request body and from the relevant parameter.

After sending the modified request, I observed that the application still processed the password-reset operation instead of rejecting the request because of the missing token.

This indicated that the application was not correctly enforcing the token requirement.

### 3. Modifying the Password Reset Request

I repeated the process using the target account's username.

I removed the reset token again and modified the password parameter to a password of my choice.

The modified request was accepted by the application, allowing the target account's password to be changed without a valid reset token.

### 4. Verifying the Result

I returned to the login functionality and attempted to authenticate using the target username and the password I had set through the manipulated password-reset request.

The login was successful, confirming that the password-reset mechanism could be bypassed.

## Vulnerability Analysis

The vulnerability existed because the application failed to properly validate the password-reset token before allowing the password to be changed.

A secure password-reset workflow should require a valid, unpredictable, and properly associated reset token before accepting a password change.

The vulnerable flow effectively allowed:

```text
Password Reset Request
        ↓
Reset Token Removed
        ↓
Application Still Accepts Request
        ↓
Password Changed
        ↓
Account Access
```

## Security Impact

Broken password-reset logic can lead to **account takeover**.

If an attacker can modify the password-reset request and the application does not properly verify the reset token, the attacker may be able to set a new password for another user's account and subsequently log in as that user.

The impact can therefore be severe depending on the privileges and data associated with the affected account.

## Pentesting Perspective

When testing password-reset functionality, I would verify that:

* Reset tokens are required.
* Tokens are unpredictable and sufficiently long.
* Tokens are properly associated with the intended account.
* Tokens expire after an appropriate period.
* Tokens cannot be reused after successful use.
* Removing or modifying the token causes the request to fail.
* A reset request cannot be manipulated to target another account.

I would also test whether user-controlled parameters such as usernames or email addresses can be modified without proper server-side validation.

## Key Takeaways

* Password-reset functionality is an important authentication attack surface.
* Security controls must be enforced server-side rather than assumed from the client-side workflow.
* Burp Repeater is useful for manually modifying and testing individual requests.
* Removing or modifying security-critical parameters can reveal broken validation logic.
* A flawed password-reset mechanism can result in complete account takeover.

## Tools Used

* Burp Suite Community Edition
* Burp Proxy
* Burp Repeater
* Web Browser
* PortSwigger Web Security Academy

## Conclusion

This lab demonstrated how a seemingly normal password-reset workflow can contain a critical authorization flaw when security tokens are not properly validated.

The most important lesson was to test whether security mechanisms are actually enforced by the server rather than assuming that because a token exists in the request, it is being securely validated.
