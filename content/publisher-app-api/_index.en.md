---
title: Publisher Applications
date: 2020-09-08
weight: 6
pre: "<b>2. </b>"
description : "Publisher's application informations. application id, application name, platform"
---

- Publisher's application informations
  
`URL` : https:\//partners.admost.com/v1/apps?key=[key]

`METHOD` : **GET**

#### Request Parameters

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| key  | string | Publisher Token |

#### Response

| Name         | Description                        |
| ------------ | ---------------------------------- |
| app_id       | Admost Application ID              |
| name         | Application Name                   |
| package_name | Application bundle id/package name |
| platform     | (ios, android etc.)                |

#### Response Status Codes

| Code | Description                    |
| ---- | ------------------------------ |
| 200  | OK. The request has succeeded. |
| 400  | BAD REQUEST                    |
| 401  | UNAUTHORIZED                   |
| 429  | TOO MANY REQUESTS              |
| 500  | INTERNAL SERVER ERROR          |