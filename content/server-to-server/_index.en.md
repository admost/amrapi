---
title: Server to Server Rewarded Structure
date: 2020-09-09
weight: 8
pre: "<b>5. </b>"
description : "Tells how to use admost server to server validation in rewarded or offerwall videos"
---

`Publisher URL:` Callback URL identified by the publisher.

`Method:` you must have the capacity to receive GET syntax requests to a valid endpoint

### Parameters 

| Name          | Description                                                                                                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| app_id        | Admost application id                                                                                                                                                                          |
| app_user_id   | Application User ID. ( The ID that is used to identify the users to be rewarded, `must be set at SDK side.`)                                                                                   |
| created_at    | Callback sending time, epoch type.                                                                                                                                                             |
| currency      | in-game currency type of the reward (gold, coins…)                                                                                                                                             |
| reward        | in-game reward amount                                                                                                                                                                          |
| custom_data   | It’s not required. Query string typed, will be sent url encoded. Custom information that is set when the users watched rewarded video. `Must be set with the corresponding method at SDK side` |
| event_id      | Unique ID generated for callback                                                                                                                                                               |
| network       | Ad network that showed the ad                                                                                                                                                                  |
| verifier      | Required for security check, it is a md5 hash of the following                                                                                                                                 |
| activity_kind | Ad network activity type. Rewarded or offerwall                                                                                                                                                |


### S2S callback verification

* Calculation of the md5 hash verifier

verifier = md5(app_id + app_user_id + currency + event_id + network + reward + created_at + customer_S2S_Verifier)

`customer_S2S_Verifier:` The secret token identified by Admost

### Callback Sample

```text
http://publisher.doman.com?app_id=c9e86d87-453e-0d9a-3d00-56adc9ec4dc3&app_user_id=00054aee-2021-38fd-db3f-053403ad937a&created_at=1552308270&currency=Coin&custom_data=rewarded%3Dlobby&event_id=855912E3-7637-4359-9461-81C41492AF08&network=applovin&reward=3&verifier=d3721f221c163890f90742b5c2d710e9&activity_kind=rewarded
```

### Expected Response Codes by Request

| Code | Description                                                                                   |
| ---- | --------------------------------------------------------------------------------------------- |
| 200  | OK                                                                                            |
| 400  | Bad Request. (Shouldn't retry.)                                                               |
| 500  | Internal Server Error ( Retry again. 10sec. / 1min.  / 10min. / 1h / 5h / 24h time intervals) |
| 503  | Service Unavailable ( Retry again. 10sec. / 1min. / 10min. / 1h / 5h / 24h time intervals)    |