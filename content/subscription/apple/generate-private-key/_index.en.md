+++
title = "Generate JWT Token For Apple Subscriptions"
description = "Create API keys you use to sign JSON Web Tokens and authorize API requests"
+++

### Generate a private key

To generate keys, you must have an Admin role or Account Holder role in App Store Connect. You may generate multiple API keys. To generate an API key to use with the App Store Server API and External Purchase Server API, log in to App Store Connect and complete the following steps:

1. Select Users and Access, and then select the Keys tab.
2. Select In-App Purchase under the Key Type.
3. Click Generate API Key or the Add (+) button.
4. Enter a name for the key. The name is for your reference only and isn’t part of the key itself.

Click Generate.

The new key’s name, key ID, a download link, and other information appears on the page.

### Download and store the private key

After generating your API key, App Store Connect gives you the opportunity to download the private half of the key. The private key is only available for download a single time.

1. Log in to App Store Connect.
2. Select Users and Access, and then select the Keys tab.
3. Select In-App Purchase under the Key Type.
4. Click Download API Key next to the new API key.

The download link appears only if you haven’t yet downloaded the private key. Apple doesn’t keep a copy of the private key. Store your private key in a secure place.

### Getting Key id

To get your key ID, copy it from App Store Connect by logging in to App Store Connect, then:

1. Select Users and Access, then select the Keys tab.
2. The key IDs appear in a column under the Active heading. Hover the cursor next to a key ID to display the Copy Key ID link.
3. Click Copy Key ID.

If you have more than one API key, copy the key ID of the private key that you use to sign the JWT.

### Getting Issuer

To get your issuer ID, log in to App Store Connect, then:

1. Select Users and Access, then select the Keys tab.
2. The issuer ID appears near the top of the page. To copy the issuer ID, click Copy next to the ID.

### Bundle Id

Your app’s bundle ID (Ex: “com.example.testbundleid”)

You need to send us the private key (p8 file format), issuer, key id and bundle id information that you have created.
