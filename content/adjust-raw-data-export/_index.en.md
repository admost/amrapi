---
title: Adjust Raw Data Integration
date: 2020-09-08
weight: 7
pre: "<b>3. </b>"
description : "You can see UA's user install information on the dashboard with adjust integration"
---

{{% notice info %}}
You can find Adjust SDK integration document on their [help page](https://help.adjust.com/en/sdk).
{{% /notice %}}

With this integration, we'll able to get paid campaign installs from Adjust.
We need the APP token of the application and API token

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

- You can get your AWS Bucket information from Admost Dashboard -> Settings -> Adjust Settings. If you can't see the informations, click `Create AWS Bucket` button.

![AWS Bucket Info](/amrapi/images/aws-bucket-info.png?classes=shadow&width=20pc)

- Adjust App Settings -> All Settings -> Raw Data Export -> CSV Upload -> Storage Provider -> Amazon S3 Bucket

![Adjust CSV Upload Settings](/amrapi/images/adjust-csv-upload.png?classes=shadow&width=20pc)

**3. Select Events for Export:** 
- select install and updated attribution events

![Adjust Select Event for Export](/amrapi/images/adjust-events-for-export.png?classes=shadow)

**4. Add CSV Definition:**
- It is enough to use the csv definitions below. Just copy and paste

```text
{idfa||gps_adid},{idfv},{adid},{tracker},{tracker_name},{app_name},{activity_kind},{created_at},{installed_at},{installed_at_hour},{conversion_duration},{cost_type},{cost_amount},{cost_currency},{nonce},{reporting_cost},{match_type},{network_name},{campaign_name},{adgroup_name},{creative_name},{is_organic},{country},{city},{os_name},{mac_md5},{device_name},{device_type},{device_manufacturer},{ip_address},{fb_campaign_id},{fb_campaign_group_id},{fb_adgroup_id},{store},{att_status},{fb_install_referrer},{fb_install_referrer_ad_id},{fb_install_referrer_adgroup_id},{fb_install_referrer_adgroup_name},{fb_install_referrer_campaign_id},{fb_install_referrer_campaign_name},{fb_install_referrer_campaign_group_id},{fb_install_referrer_campaign_group_name},{fb_install_referrer_account_id},{fb_install_referrer_ad_objective_name}
```

### Adjust Partner Terms&Conditions Settings

{{% notice warning %}}
If you have an UA from one of these adjust partners, you have to accept terms&conditions. It is important for us to see the content of the campaign.
{{% /notice %}}

##### 1. Facebook Terms&Conditions

{{% notice warning %}}
Facebook announced plans to deprecate the current iteration of the Advanced Mobile Measurement (AMM) program that Facebook has with Adjust and other MMPs. On October 29, 2021, access to AMM data will be removed from adjust reporting interfaces such that only aggregated data will be available.

Campaign metadata is appended to the Install Referrer in an encrypted format. To read the metadata, you need to use a Facebook-provided [decryption key](https://help.adjust.com/en/article/facebook-raw-data-reporting-for-android#set-up-the-install-referrer-solution) for your app.

For more details, please check [adjust help page document](https://help.adjust.com/en/article/facebook-raw-data-reporting-for-android#set-up-the-install-referrer-solution)
{{% /notice %}}

 * make sure sign the facebook terms and conditions 

![Facebook Terms](/amrapi/images/facebook-terms.png?classes=shadow)

##### 2. Twitter Terms&Conditions

Ask your twitter account manager to enable the data access between your account and Adjust in Twitter’s AMM Program 

* Twitter’s AMM Program via [this form](https://business.twitter.com/en/form/mact-data-opt-in.html?ref=adjust).

Also ask your adjust account manager to check `Approved By Twitter` settings.

![Approved By Twitter](/amrapi/images/approved-by-twitter.png?classes=shadow)