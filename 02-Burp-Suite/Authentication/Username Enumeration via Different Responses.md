# Username Enumeration via Different Responses

## Lab Overview

**Platform:** PortSwigger Web Security Academy
**Category:** Authentication
**Vulnerability:** Username Enumeration
**Tools:** Burp Suite, Burp Intruder

## Objective

The objective of this lab was to identify a valid username by analyzing differences in the application's responses and then use the discovered username to continue the authentication attack.

## Methodology

I first enabled the **Burp Suite Proxy** and opened the lab through the browser. I submitted an incorrect login attempt and then inspected the request in **HTTP History**.

I located the login request, which used the `POST` method, and sent it to **Burp Intruder** for automated testing.

In Intruder, I selected the username parameter as the injection point and loaded the provided list of candidate usernames as the payload set. I then started the attack and compared the responses returned for each candidate.

The key observation was a **difference in response length** for one of the candidate usernames. This indicated that the application was responding differently when a valid username was submitted, allowing me to identify the valid account.

After identifying the valid username, I used it for the next stage of the lab and tested the password candidates. The correct credentials produced a distinguishable response, allowing me to successfully complete the lab.

## What I Learned

This lab demonstrated how an application can unintentionally disclose information through differences in its responses. Even when an application does not explicitly state whether a username exists, characteristics such as response length can reveal this information.

I also gained practical experience using **Burp Suite HTTP History and Intruder** to capture authentication requests, define attack positions, load payload lists, automate testing, and compare responses.

## Pentesting Takeaway

When assessing an authentication mechanism, I should not focus only on visible error messages. Response length, status codes, headers, redirects, and other response characteristics can potentially reveal information about how the application processes different inputs.

## Key Takeaways

* Authentication responses can unintentionally leak information.
* Username enumeration can be detected through response differences.
* Burp Intruder can automate testing of multiple candidate inputs.
* Response length can be a useful indicator when comparing authentication responses.
* Small information leaks can make subsequent credential attacks more effective.

## Tools Used

* Burp Suite Community Edition
* Burp Proxy
* Burp Intruder
* Web Browser
* PortSwigger Web Security Academy

