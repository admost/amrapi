---
title: Impression and Revenue API
date: 2021-03-01
weight: 9
pre: "<b>6. </b>"
description : "You can get placement and country base impression and revenue data"
---

- Application's placement and country base impression and revenue data

**Endpoint:** `http://amr-api.admost.com/api/publisher/v1/reporting?apiKey=[apiKey]&startdate=[YYYY-MM-DD]&enddate=[YYYY-MM-DD]&app=[appid]`

`METHOD` : **GET**

#### Request Parameters

| Name      | Type   | Description           |
| --------- | ------ | --------------------- |
| apiKey    | string | Publisher's token     |
| startdate | string | Report start date     |
| enddate   | string | Report end date       |
| appid     | string | Admost application ID |

#### Response

| Name        | Description                   |
| ----------- | ----------------------------- |
| AdNetwork   | Ad Network Name               |
| AppName     | Application Name              |
| AppType     | Application type android/ios  |
| Placement   | Placement Name                |
| CountryCode | Country short code            |
| Country     | Country Name                  |
| Impression  | Impression count              |
| Revenue     | Revenue amount ($)            |
| Date        | Which day the data belongs to |