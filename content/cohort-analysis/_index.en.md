---
title: Cohort Analysis API
date: 2021-04-08
weight: 10
pre: "<b>7. </b>"
description : "Cohort Analysis gives you the option to segregate this group of people according to different groupings and see multiple metrics."
---


**Endpoint:** `http://amr-api.admost.com/api/publisher/v1/cohort`

**METHOD** : POST

#### Request Parameters

| Name                    | Type    | Description                                                                                                     |
| ----------------------- | ------- | --------------------------------------------------------------------------------------------------------------- |
| apiKey                  | string  | Publisher's token                                                                                               |
| startdate               | string  | Start date (yyyy-MM-dd)                                                                                         |
| enddate                 | string  | End date    (yyyy-MM-dd)                                                                                        |
| groupBy                 | string  | Comma seperated values (day, week, month, app, country, source, campaign, adgroup, creative, source_type, test) |
| apps                    | string  | Filters app ids (comma seperated, can be found on Admost Dashboard -> My Apps)                                  |
| appType                 | string  | Filters app type (Allowed values ("android","ios"))                                                             |
| userType                | string  | Filters user type (Allowed values ("organic","paid"))                                                           |
| revenueType             | string  | Filters revenue type (Allowed values ("adRevenue","inAppPurchase"))                                             |
| countries               | string  | Filters countries (comma seperated, ISO 3166-1 alpha-2 )                                                        |
| countryIn               | string  | Determines how the values of previous parameter is used, Allowed values ("in","notin"), "in" is default         |
| sources                 | string  | Filters sources (comma seperated)                                                                               |
| sourceIn                | string  | Determines how the values of previous parameter is used, Allowed values ("in","notin"), "in" is default         |
| campaigns               | string  | Filters campaigns (comma seperated)                                                                             |
| adgroups                | string  | Filters adgroups (comma seperated)                                                                              |
| creatives               | string  | Filters creatives (comma seperated)                                                                             |
| tests                   | string  | Filters A/B tests (comma seperated)                                                                             |
| minCohortSize           | integer | Filters cohort size which are greater than the value specified                                                  |
| revenueCostRatioDay     | integer | Filters rows which has day N revenue/cost ratio greater or less than following parameter                        |
| revenueCostRatioPercent | integer | Filters rows which has day N revenue/cost ratio greater or less than specified %                                |
| revenueCostRatioType    | integer | Allowed values("min","max")                                                                                     |
| retentionFilterDay      | string  | Filters rows which has day N retention greater or less than following parameter                                 |
| retentionFilterPercent  | integer | Filters rows which has day N retention greater or less than specified %                                         |
| retentionFilterType     | string  | Allowed values("min","max")                                                                                     |
| currency                | string  | Currency, ISO 4217 alpha-3, Default value USD                                                                   |
| showExpected            | boolean | Allowed values (true,false)                                                                                     |
| showAllDays             | boolean | Allowed values (true,false)                                                                                     |

#### Request Example
```text
curl --location --request POST 'http://amr-api.admost.com/api/publisher/v1/cohort' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apps" : "13236a79-3769-4de0-a8b2-bfedcb2ebc36,32a70329-1971-4934-81fc-c926710fec46",
    "apiKey":"hdxpKfQmttuYK557GH2hWf1Lg2ad6c6b",
    "startDate":"2021-04-01",
    "endDate":"2021-04-07",
    "groupBy":"day,app",
    "minCohortSize" : 500,
    "showAllDays" : true,
    "countries" : "US,UK"
}'
```


#### Response Example
```json
{
    "rows": [
        {
            "date": "2021-04-01",
            "app": "13236a79-3769-4de0-a8b2-bfedcb2ebc36",
            "user_count": 10,
            "cost": 0.0,
            "ecpi": 0.0,
            "impression_ua": 0,
            "ecpm_ua": 0.0,
            "revenue": 0.4560423169992503,
            "profit": 0.4560423169992503,
            "roi": 0.0,
            "paying_users": 0,
            "days": [
                {
                    "install_count": 10,
                    "arpu": 0.0053,
                    "retention": 100.0,
                    "user_count": 10,
                    "revenue": 0.053355720999409183,
                    "roi": 0.0,
                    "converted": 0,
                    "rv_engagement": 10.0,
                    "int_engagement": 30.0,
                    "rv_imp_over_user": 0.2,
                    "int_imp_over_user": 2.5,
                    "day": 0
                },
                {
                    "install_count": 10,
                    "arpu": 0.0175,
                    "retention": 60.0,
                    "user_count": 6,
                    "revenue": 0.17509613351213407,
                    "roi": 0.0,
                    "converted": 0,
                    "rv_engagement": 16.666666666666668,
                    "int_engagement": 50.0,
                    "rv_imp_over_user": 0.66666666666666663,
                    "int_imp_over_user": 5.666666666666667,
                    "day": 1
                },
                {
                    "install_count": 10,
                    "arpu": 0.0247,
                    "retention": 50.0,
                    "user_count": 5,
                    "revenue": 0.24746051454861129,
                    "roi": 0.0,
                    "converted": 0,
                    "rv_engagement": 20.0,
                    "int_engagement": 60.0,
                    "rv_imp_over_user": 0.4,
                    "int_imp_over_user": 4.0,
                    "day": 2
                },
                {
                    "install_count": 10,
                    "arpu": 0.0273,
                    "retention": 40.0,
                    "user_count": 4,
                    "revenue": 0.272978108058449,
                    "roi": 0.0,
                    "converted": 0,
                    "rv_engagement": 0.0,
                    "int_engagement": 50.0,
                    "rv_imp_over_user": 0.0,
                    "int_imp_over_user": 3.25,
                    "day": 3
                }
				...
            ]
        },
        {
            "date": "2021-04-02",
            "app": "32a70329-1971-4934-81fc-c926710fec46",
            "user_count": 9,
            "cost": 0.0,
            "ecpi": 0.0,
            "impression_ua": 0,
            "ecpm_ua": 0.0,
            "revenue": 0.26141788889868828,
            "profit": 0.26141788889868828,
            "roi": 0.0,
            "paying_users": 0,
            "days": [
                {
				...
				}
            ]
        }
    ],
    "mean": {
        "install": 73,
        "cost": 0.0,
        "ecpi": 0.0,
        "impression_ua": 0,
        "ecpm_ua": 0.0,
        "revenue": 1.6675287341379905,
        "profit": 1.6675287341379905,
        "roi": 0.0,
        "paying_users": 0,
        "days": [
            {
                "install_count": 73,
                "arpu": 0.0058,
                "retention": 100.0,
                "user_count": 73,
                "revenue": 0.41995835787414187,
                "roi": 0.0,
                "converted": 0,
                "rv_engagement": 15.068493150684931,
                "int_engagement": 27.397260273972602,
                "rv_imp_over_user": 1.3561643835616439,
                "int_imp_over_user": 2.7123287671232879,
                "day": 0
            },
            {
                "install_count": 73,
                "arpu": 0.0132,
                "retention": 39.726027397260275,
                "user_count": 29,
                "revenue": 0.962708437683715,
                "roi": 0.0,
                "converted": 0,
                "rv_engagement": 41.379310344827587,
                "int_engagement": 51.724137931034484,
                "rv_imp_over_user": 1.1724137931034482,
                "int_imp_over_user": 7.9655172413793105,
                "day": 1
            }
			...
        ]
    }
}
```