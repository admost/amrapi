---
title: Tag Impression Api
date: 2022-07-01
weight: 10
pre: "<b>8. </b>"
description : "You can get impression and estimated revenue data by tags."
---


`Endpoint:` http:\//amr-api.admost.com/api/publisher/v1/tagimpression

`METHOD` : **POST**

#### Request Parameters

| Name      | Type   | Description           |
| --------- | ------ | --------------------- |
| apiKey    | string | Publisher's token     |
| startdate | string | Start date (yyyy-MM-dd)     |
| enddate   | string | End date    (yyyy-MM-dd)   |
| groupBy   | string | Comma seperated values (day, app, zone, tag, country, placement)   |
| apps      | string | Filters app ids (comma seperated, can be found on Admost Dashboard -> My Apps)   |
| appType   | string | Filters app type (Allowed values ("android","ios"))   |
| countries | string | Filters countries (comma seperated, ISO 3166-1 alpha-2 )   |
| countryIn | string | Determines how the values of previous parameter is used, Allowed values ("in","notin"), "in" is default    |
| tags      | string | Filters tags (comma seperated, can be found on Admost Dashboard -> My Apps)   |

#### Request Example
```text
curl --location --request POST 'http://amr-api.admost.com/api/publisher/v1/tags' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apps" : "13236a79-3769-4de0-a8b2-bfedcb2ebc36",
    "apiKey":"hdxpKfQmttuYK557GH2hWf1Lg2ad6c6b",
    "startDate":"2022-06-20",
    "endDate":"2021-06-30",
    "groupBy":"tag,app"    
}'
```


#### Response Example
```json
[
    {
        "ecpm": 4.3112116404222012995456,
        "tag": "tag1",
        "sum_revenue": 30772.4198658098140810520543,
        "app_name": "appname1",
        "sum_tag_impression": 7137766.0,
        "application_id": "77c38280-b985-459c-8f82-c18c81089c2d"
    },
    {
        "ecpm": 6.675818990577592693769709,
        "tag": "tag2",
        "sum_revenue": 24385.878888654199290512475850,
        "app_name": "appname1",
        "sum_tag_impression": 3652867.0,
        "application_id": "77c38280-b985-459c-8f82-c18c81089c2d"
    },
    {
        "ecpm": 3.83853119177000496403693,
        "tag": "tag3",
        "sum_revenue": 6287.01124453314626044220545,
        "app_name": "appname2",
        "sum_tag_impression": 1637869.0,
        "application_id": "1dd05dd6-f8fc-45d7-a47e-1a15951a5e20"
    }
]
```