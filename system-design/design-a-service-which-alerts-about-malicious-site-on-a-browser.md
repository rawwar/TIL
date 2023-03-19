---
description: Notes
---

# Design a Service which alerts about Malicious site on a browser

## 1. Functional Requirements

* Whenever user tries to open a link via redirect or by entering URL in the browser, website has to be evaluated.
* If Malicious website is detected, should show a pop-up, else open the website
* A way to receive reports from users about malicious websites
* keep updated malicious website database

## 2. Non-Functional Requirements

* <mark style="color:red;">Highly Available</mark> - Website should be up most of the time.&#x20;
* <mark style="color:red;">Consistency</mark> - Eventual Consistent state of database
* <mark style="color:red;">Secure -</mark>  Our service should be secure that no one can just mark any website as malicious
* <mark style="color:red;">Scalability</mark> -  Should withstand peak loads
* <mark style="color:red;">Performance</mark>  - Should be able to classify websites as malicious with minimal latency