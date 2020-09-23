---
title: Adjust Raw Data Integration
date: 2020-09-08
weight: 7
pre: "<b>3. </b>"
description : "You can see UA user install and cost information on the dashboard with adjust integration"
---

To fully integrate with Adjust, we need the APP token and API tokens of the application

### APP token and API token Settings

 **1. Get API Token from Adjust Dashboard Menu**

 - Adjust Dashboard Menu -> My Account -> User Details

![API TOKEN](/amrapi/images/adjust-user-details.png?classes=shadow)

 **2. Add API Token Admost Dashboard**
 
 - Admost Dashboard -> Settings -> Adjust Key

![Admost Adjust Settings](/amrapi/images/admost-adjust-settings.png?classes=shadow&width=10pc)
![Admost Adjust Key Setting](/amrapi/images/adjust-key.png?classes=shadow&width=20pc)

 **3. Get App Token from Adjust Dashboard Menu -> Apps**

![Admost App Token](/amrapi/images/adjust-app-token.png?classes=shadow)

**4. Add App Token to Admost Dashboard -> My Apps -> Edit App -> Adjust App Token** 

![Admost App Token Setting](/amrapi/images/admost-app-token.png?classes=shadow)

### Configure Amazon S3 CSV Upload Settings in Adjust App Settings

**1. Create AWS Bucket**

- Admost Dashboard -> Settings -> Adjust Key

![Create AWS Bucket](/amrapi/images/adjust-key.png?classes=shadow&width=20pc)

**2. Add AWS S3 Bucket Information to Adjust Raw Data Export Settings**

![AWS Bucket Info](/amrapi/images/aws-bucket-info.png?classes=shadow&width=20pc)

- Adjust App Settings -> All Settings -> Raw Data Export -> CSV Upload -> Storage Provider -> Amazon S3 Bucket

![Adjust CSV Upload Settings](/amrapi/images/adjust-csv-upload.png?classes=shadow&width=20pc)

**Select Events for Export:** install and updated attribution

**CSV Definition:**

```text
{idfa||gps_adid},{idfv},{adid},{tracker},{tracker_name},{app_name},{activity_kind},{created_at},{installed_at},{installed_at_hour},{conversion_duration},{cost_type},{cost_amount},{cost_currency},{nonce},{reporting_cost},{match_type},{network_name},{campaign_name},{adgroup_name},{creative_name},{is_organic},{country},{city},{os_name},{mac_md5},{device_name},{device_type},{device_manufacturer},{ip_address},{fb_campaign_id},{fb_campaign_group_id},{fb_adgroup_id},{store}
```

![Adjust Select Event for Export](/amrapi/images/adjust-events-for-export.png?classes=shadow)

### Adjust Partner Terms&Conditions Settings

{{% notice warning %}}
If you have an UA from one of these adjust partners, you have to accept terms&conditions. It is important for us to see the content of the campaign.
{{% /notice %}}

##### 1. Facebook Terms&Conditions

 * make sure sign the facebook terms and conditions 

![Facebook Terms](/amrapi/images/facebook-terms.png?classes=shadow)

##### 2. Twitter Terms&Conditions

Ask your twitter account manager to enable the data access between your account and Adjust in Twitter’s AMM Program 

* Twitter’s AMM Program via [this form](https://business.twitter.com/en/form/mact-data-opt-in.html?ref=adjust).

Also ask your adjust account manager to check `Approved By Twitter` settings.

![Approved By Twitter](/amrapi/images/approved-by-twitter.png?classes=shadow)