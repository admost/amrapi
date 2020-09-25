+++
title = "Get Credential"
description = "Tells how to get credential from google play"
+++

Step-by-step guide for creating your Play service credentials

In order for Admost's servers to communicate with Google on your behalf you need to provide a set of service credentials. The process for configuring these credentials is a bit complex, but the added level of control improves security by only providing Admost with the access we need.

### Link to a Google Developer Project

Your Play Developer account needs to be linked to a Google Developer Project.

+ Go to your [Play Console settings](https://play.google.com/apps/publish#ApiAccessPlace)

![Play Console](/amrapi/images/google-play-console-1.png?classes=shadow)

+ Select API access

![Play API Access](/amrapi/images/google-play-api-access.png?classes=shadow&width=20pc)

+ Select Link to connect your Play account to a Google Developer Project

![Play Link App](/amrapi/images/google-play-link.png?classes=shadow)

### Create Service Account

Next we need to create a service account. This is done from the Google API Console

+ Select Create Service Account

![Play Create Service Account](/amrapi/images/google-play-create-service-account.png?classes=shadow)

+ Follow the link to the Google API Console

![Play Navigate API Console](/amrapi/images/google-play-create-service-account-2.png?classes=shadow)

+ Create Service account key credentials

![Play Account Key](/amrapi/images/google-play-account-key.png?chasses=shadow)

+ Name it and assign it Project Owner Role

When you hit create, a JSON file will be downloaded. These are the credentials that Admost will need to communicate with Google

![Play Account Create](/amrapi/images/google-play-account2.png?chasses=shadow)

+ Set the Role to Project > Owner

![Play Set Project Owner](/amrapi/images/google-play-project-owner.png?chasses=shadow)

+ Download your JSON credential

![Play Download JSON](/amrapi/images/google-play-download-json.png?chasses=shadow)

### Grant Financial Access to Admost

+ Back in the Play Console, select Grant Access on the newly created Admost service account

![Play Grant Access](/amrapi/images/google-play-grant-access.png?chasses=shadow)

+ Set the Role to Finance and Add Manage Orders Permissions

![Play Finance Permission](/amrapi/images/google-play-finance-permission.png?chasses=shadow)

Hit save and you're done. 

Add the credential JSON that were downloaded in step 2 to `Android Store Credentials` and we'll be ready to handle Google Play purchases!

![Add Google Store Credential](/amrapi/images/google-subscription-credential.png?chasses=shadow)