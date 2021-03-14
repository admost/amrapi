---
title: Appsflyer Raw Data Export
date: 2021-03-12
weight: 10
pre: "<b>7. </b>"
description : "You can see UA's user install information on the dashboard with appsflyer integration"
---

{{% notice info %}}
You can find Appsflyer SDK integration document on their [help page](https://support.appsflyer.com/hc/en-us/categories/201114756-SDK-integration-).
{{% /notice %}}

### Create a New Hostname with an A Record

In this step, we need your domain address with `callback` subdomain. You’ll add a new `callback` hostname to your domain and point it to a `195.244.38.50` IP address by your domain registrar.

![Domain DNS A Record](/amrapi/images/dns_a_record.png?classes=shadow)

### AppsFlyer Push API Settings

1. Go to [AppsFlyer’s dashboard](https://hq.appsflyer.com/login), and select Apps -> Integration -> API access -> Push API. Push API is available only for AppsFlyer premium plan, so please contact AppsFlyer if you don't see it.
2. Click **Add Endpoint**.
3. Push API version **2.0**
4. Select an HTTP method: **POST**
5. Enter the **Endpoint URL**.
   * `https://callback.yourdomainaddress.com/v1/appsflyer/install`
6. Select **Install** **Non-organic** event type.
7. Select **all** message fields.
8. We don't need in-app events.
9. Click **Save**

{{% notice warning %}}
If you are using Facebook, you have to accept terms&conditions. Go [here](https://www.facebook.com/ads/manage/advanced_mobile_measurement/app_based_tos/) and accept the term.
{{% /notice %}}

![Appsflyer Push API SS](/amrapi/images/appsflyer_push_api_ss.png?classes=shadow)
