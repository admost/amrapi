+++
title = "Get Credential"
description = "Tells how to get credential from google play"
+++

Step-by-step guide for creating your Play service credentials

In order for Admost's servers to communicate with Google on your behalf you need to provide a set of service credentials. The process for configuring these credentials is a bit complex, but the added level of control improves security by only providing Admost with the access we need.

### 1. Link to a Google Developer Project

Your Play Developer account needs to be linked to a Google Developer Project.

#### 1a. Open the Settings > Developer account menus and select API access

![Play API Access](/amrapi/images/google_developer_api_access.png?classes=shadow&width=20pc)

#### 1b. Select Link to connect your Play account to a Google Developer Project

![Get API Access](/amrapi/images/google_developer_get_api_access.png?classes=shadow&width=20pc)

#### 1c. Agree to the terms and conditions

![Agree Terms](/amrapi/images/google_developer_agree_terms.png?classes=shadow&width=20pc)

### 2. Create Service Account

Next we need to create a service account. This is done from the Google API Console

#### 2a. Select Create Service Account

![Play Create Service Account](/amrapi/images/google_play_service_accounts.png?classes=shadow&width=700px)

#### 2b. Follow the link to the Google API Console

![Play Navigate API Console](/amrapi/images/google_play_create_new_service_account.png?classes=shadow&width=700px)

#### 2c. Create Service account key credentials

![Play Account Key](/amrapi/images/google-play-account-key-credential.png?chasses=shadow&width=700px)

#### 2d. Name it and assign it Project Owner Role

When you hit create, a JSON file will be downloaded. These are the credentials that Admost will need to communicate with Google

![Play Account Create](/amrapi/images/google_play_account_details2.png?chasses=shadow&width=40pc&height=40pc)

Add two Roles:

* Pub/Sub Admin (to enable [Platform Server Notifications](https://admost.github.io/amrapi/subscription/google/realtime-notification/))
* Monitoring Viewer (to allow monitoring of the notification queue)

![Grant this service](/amrapi/images/google-play-grant-service-account-project.png?chasses=shadow&width=40pc&height=40pc)

You can skip the optional third step, "Grant users access to this service account" by clicking Done.

![Grant this user](/amrapi/images/google-play-grant-this-user-service-account.png?chasses=shadow&width=40pc&height=40pc)

#### 2e. Create Public Key

In the Google Cloud Console, click on Actions > Manage keys.

![Service Account Manage Keys.png](/amrapi/images/google-play-service-account-manage-keys.png?chasses=shadow)

Click ADD KEY > Create new key.

![Manage Credentials Create New Key](/amrapi/images/google-play-service-credentials-create-new-key.png?chasses=shadow)

Make sure JSON is selected and click Create to create and download the JSON key.

![Create Credential JSON](/amrapi/images/google-credential-json-create.png?chasses=shadow)

![Save Private Key](/amrapi/images/google-private-key-saved-to-your-pc.png?chasses=shadow&width=40pc)

The downloaded JSON key is what you will need to enter in Admost in step 4.
### 3. Grant Financial Access to Admost
#### 3a. Back in the Play Console, select Grant Access on the newly created Admost service account

![Play Grant Access](/amrapi/images/google_play_grant_access.png?chasses=shadow&width=700px)

#### 3b. Grant the following permissions

* View app information and download bulk reports (read-only)
* View financial data, orders, and cancellation survey responses
* Manage orders and subscriptions

![Play Finance Permission](/amrapi/images/google_play_access_permissions.png?chasses=shadow)

#### 3c.Click Invite User at the bottom and send the invite

![Play Send Invite](/amrapi/images/google_play_send_invite.png?chasses=shadow&width=700px)

You will be redirected to Users and Permissions where you should see your newly created service account as Active.

#### 3d. Apply permissions to your apps

In the Users and Permissions section, click on the service account and add your apps to the account. Click Apply on the sheet that appears.

![Play App Permission](/amrapi/images/google_play_app_permission.png?chasses=shadow)

![App Permission](/amrapi/images/google_play_permission_for_app.png?chasses=shadow&width=700px)


Hit save and you're done. 

### 4. Enter the credentials JSON in Admost

Add the credential JSON that were downloaded in to `Android Store Credentials` and we'll be ready to handle Google Play purchases!

![Add Google Store Credential](/amrapi/images/google-subscription-credential.png?chasses=shadow&width=20pc)

{{% notice warning %}}
It can take up to 36 hours for your Play Service Credentials to work properly with the Android Developer API.
{{% /notice %}}