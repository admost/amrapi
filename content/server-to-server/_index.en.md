---
title: Server to Server Rewarded Structure
date: 2020-09-09
weight: 8
pre: "<b>5. </b>"
description : "Tells how to use admost server to server validation in rewarded videos"
---

With this integration, you can be sure whether the user is watching a rewarded video or not. In case of watching the rewarded video successfully, a callback is made to the publisher url.

You should active some s2s settings on admost dashboard.

* Add your endpoint and generate customer s2s verification token.
  * My Apps -> Edit App 

    ![s2sMyAppEnableS2s](/amrapi/images/s2sMyAppEnableS2s.png?classes=shadow&width=10pc)
    ![s2sRewardedEndpointAndVerifier](/amrapi/images/s2sRewardedEndpointAndVerifier.png?classes=shadow&width=20pc)

  * Activate s2s from Rewarded zone

    ![s2sRewardedZoneEdit](/amrapi/images/s2sRewardedZoneEdit.png?classes=shadow&width=20pc)
    ![S2sZoneEdit](/amrapi/images/S2sZoneEdit.png?classes=shadow&width=10pc)


**Publisher URL:** Callback URL identified by the publisher on admost dashboard.

**Publisher Method:** You must have the capacity to receive GET request for your endpoint

### Parameters 

| Name          | Description                                                                                                                                                                                                                                                                                                                            |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| app_id        | Admost application id                                                                                                                                                                                                                                                                                                                  |
| app_user_id   | Application User ID. ( The ID that is used to identify the users to be rewarded, `must be set at SDK side.`)                                                                                                                                                                                                                           |
| created_at    | Callback sending time, epoch type.                                                                                                                                                                                                                                                                                                     |
| currency      | in-game currency type of the reward (gold, coins…)                                                                                                                                                                                                                                                                                     |
| reward        | in-game reward amount                                                                                                                                                                                                                                                                                                                  |
| custom_data   | It’s not required. Query string typed, will be sent url encoded. Custom information that is set when the users watched rewarded video. `Must be set with the corresponding method at SDK side` [android sdk method](https://admost.github.io/amrandroid/#sscallbacks) / [ios sdk method](https://admost.github.io/amrios/#sscallbacks) |
| event_id      | Unique ID generated for callback                                                                                                                                                                                                                                                                                                       |
| network       | Ad network that showed the ad                                                                                                                                                                                                                                                                                                          |
| verifier      | Required for security check, it is a md5 hash of the following                                                                                                                                                                                                                                                                         |
| activity_kind | Ad network activity type. Rewarded                                                                                                                                                                                                                                                                                                     |


### S2S callback verification

* Calculation of the md5 hash verifier

verifier = md5(app_id + app_user_id + currency + event_id + network + reward + created_at + customer_S2S_Verifier)

**customer_S2S_Verifier:** The secret token. You can generate token on admost dashboard.

### Callback sample

```text
http://publisher.doman.com?app_id=c9e86d87-453e-0d9a-3d00-56adc9ec4dc3&app_user_id=00054aee-2021-38fd-db3f-053403ad937a&created_at=1552308270&currency=Coin&custom_data=rewarded%3Dlobby&event_id=855912E3-7637-4359-9461-81C41492AF08&network=applovin&reward=3&verifier=d3721f221c163890f90742b5c2d710e9&activity_kind=rewarded
```

### Expected response codes by request from publisher endpoint

| Code | Description                                                                                   |
| ---- | --------------------------------------------------------------------------------------------- |
| 200  | OK                                                                                            |
| 400  | Bad Request. (Shouldn't retry.)                                                               |
| 500  | Internal Server Error ( Retry again. 10sec. / 1min.  / 10min. / 1h / 5h / 24h time intervals) |
| 503  | Service Unavailable ( Retry again. 10sec. / 1min. / 10min. / 1h / 5h / 24h time intervals)    |