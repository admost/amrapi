---
title: Adjust Raw Data Export Settings
date: 2020-09-08
weight: 7
pre: "<b>3. </b>"
description : "You can see UA's user install information on the dashboard with adjust raw data export settings"
---

{{% notice info %}}
You can find Adjust SDK integration document on their [help page](https://help.adjust.com/en/sdk).
{{% /notice %}}

With this raw data export settings, we'll able to get paid campaign installs from Adjust.
We need the APP token of the application and API token

{{% notice warning %}}
[**Facebook Campaigns**]({{ ref . "#facebook-campaigns" }})

On October 29th 2021, Facebook deprecated their Advanced Mobile Measurement (AMM) program. This means that Facebook Marketing Partners and advertisers may not receive device-level campaign data for any iOS users attributed to Facebook, and only partial data for Android users. This is enforced regardless of the user's ATT status.

For IOS apps:
* We can not get anymore ios FB campaigns

For ANDROID apps:
* You have to do some extra steps

1. Set up install referrer
https://help.adjust.com/en/article/get-started-android-sdk#set-up-install-referrer
2. Campaign metadata is appended to the Install Referrer in an encrypted format. To read the metadata, you need to use a Facebook-provided [decryption key](https://help.adjust.com/en/article/facebook-raw-data-reporting-for-android#set-up-the-install-referrer-solution) for your app.
3. Add `{fb_install_referrer}` csv definition if not exist on adjust dashboard -> app all settings -> raw data export -> csv upload -> CSV DEFINITION

For more details, please check [adjust help page document](https://help.adjust.com/en/article/facebook-raw-data-reporting-for-android#set-up-the-install-referrer-solution)
{{% /notice %}}

### APP token and API token Settings

 **1. Get API Token from Adjust Dashboard Menu**

 - Adjust Dashboard Menu -> My Account -> User Details
   - The Adjust APIs are available to all clients on a **Business Pro package or above**. For more details please 
      check [adjust help page document](https://help.adjust.com/en/article/api-authentication)

{{% expand "API Token for Admin Users" "false" %}}    
1. Open your Adjust dashboard.
1. Click on the menu icon in the top left to open the main menu.
1. Click on My Account.
1. In the Your Data tab that opens, find the User Details section. Click on the cog icon at the bottom of this segment to open the user details panel.
1. In the panel that opens, click on API Token. This opens the API token panel.
1. Copy your API token from the API Token panel.
{{% /expand %}}

{{% expand "API Token for Non-admin Users" "false" %}}
**For Non-admin users, you have to give to user cost data access permission.**
1. Open your Adjust dashboard.
1. Click on the menu icon in the top left to open the main menu.
1. Click on My Profile to open the user details panel.
1. In the panel that opens, click on API Token. This opens the API token panel.
1. Copy your API token from the API Token panel.
{{% /expand %}}

 **2. Add API Token to Adjust Settings in Admost Dashboard**
 
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
- select install, reattribution and updated attribution events

![Adjust Select Event for Export](/amrapi/images/adjust-events-for-export1.png?classes=shadow&width=20pc)

**4. Add CSV Definition:**
- It is enough to use the csv definitions below. Just copy and paste

```text
{idfa||gps_adid},{idfv},{adid},{tracker},{tracker_name},{app_name},{activity_kind},{created_at},{installed_at},{installed_at_hour},{conversion_duration},{cost_type},{cost_amount},{cost_currency},{nonce},{reporting_cost},{match_type},{network_name},{campaign_name},{adgroup_name},{creative_name},{is_organic},{country},{city},{os_name},{mac_md5},{device_name},{device_type},{device_manufacturer},{ip_address},{fb_campaign_id},{fb_campaign_group_id},{fb_adgroup_id},{store},{att_status},{fb_install_referrer}
```

### Adjust Partner Terms&Conditions Settings

{{% notice warning %}}
If you have an UA from one of these adjust partners, you have to accept terms&conditions. It is important for us to see the content of the campaign.
{{% /notice %}}

##### 2. Twitter Terms&Conditions

Ask your twitter account manager to enable the data access between your account and Adjust in Twitter’s AMM Program 

* Twitter’s AMM Program via [this form](https://business.twitter.com/en/form/mact-data-opt-in.html?ref=adjust).

Also ask your adjust account manager to check `Approved By Twitter` settings.

![Approved By Twitter](/amrapi/images/approved-by-twitter.png?classes=shadow)