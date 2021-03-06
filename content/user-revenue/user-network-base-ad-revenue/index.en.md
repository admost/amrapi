---
title: 'Network Base Ad Revenue'
date: 2020-09-07
weight: 2
description : "You can get user ad revenue information with ad network"
---


- Download the report from the api response when ready.  
  
    - If you are getting **404 response** status when trying to download the file. The file is not prepared yet. Please wait a while and try again.

- The download file name is generated with appID, date and timestamp
    - :appID:\_:date:\_bynetwork\_:timestamp:.tar.gz
    - Extracted file format: csv

- Allows only a request per minute per application id

- By default, when a request is made twice for the same day, it returns the previously created csv file. If you want to get a new file from the same day, you must use `create_new_file` parameter.

- You can get the admost application id using by Admost [Publisher Applications API](https://admost.github.io/amrapi/publisher-app-api/)



`Authentication:` Bearer Token authentication.

`Method:` GET

`URL:` https:\//partners.admost.com/v2/userAdRevenue

#### Request Parameters:

| Name            | Type   | Description                                       |
| --------------- | ------ | ------------------------------------------------- |
| date            | string | YYYY-MM-DD                                        |
| app_id          | string | Application admost id                             |
| report_type     | int    | Optional. Default value 1 ( 1 -  User Ad Revenue) |
| create_new_file | int    | Optional. Default value false 0-> false, 1-> true |

#### Request Example URL:

https:\//partners.admost.com/v2/userAdRevenue?app_id={application_id}&date={date}

#### Response Example URL:

https:\//partners.admost.com/downloads/reports/userAdRevenue/c9e86d87-453e-0d9a-3d00-56adc9ec4dc3_bynetwork_1554291219.tar.gz

#### Response Status Codes:

| Code | Description                                                                                         |
| ---- | --------------------------------------------------------------------------------------------------- |
| 200  | OK. The request has succeeded. Returns with a link to download the report                           |
| 400  | BAD REQUEST. The request must belong to two days before etc.                                        |
| 401  | UNAUTHORIZED                                                                                        |
| 429  | TOO MANY REQUESTS. The user has sent too many requests in a given amount of time ("rate limiting"). |
| 500  | INTERNAL SERVER ERROR                                                                               |

#### Report Column Description

- The report is generated with columns titles.

| Name                       | Description                                |
| -------------------------- | ------------------------------------------ |
| UserID                     | Admost user id                             |
| LaunchedAt                 | User first session time ( UTC )            |
| Network                    | Ad network                                 |
| Country                    | User country                               |
| IDFA                       | User idfa id                               |
| AdjustUserID               | User adjust device id                      |
| AdRevenue                  | Network user revenue                       |
| InterstitialImpCount       | Number of interstitials seen by user       |
| RewardedImpCount           | Number of rewarded seen by user            |
| OfferwallImpCount          | Number of offerwall seen by user           |
| NativeInterstitialImpCount | Number of native interstitial seen by user |
| BannerImpCount             | Number of banner seen by user              |
| NativeImpCount             | Number of native banner seen by user       |