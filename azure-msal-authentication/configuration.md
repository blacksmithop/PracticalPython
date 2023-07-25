---
description: Getting started with app development in Azure with Active Directory
---

# 🔧 Configuration

## Public Flows

Public Flows must be enabled for acquiring Access Token as a token on behalf of the Client

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

## Access on behalf of user

To enable the app to access resources through an authenticated user some permissions need to be set.

1. Add API Permission

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

2. Select Graph API

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>



3. Select Delegated Permissions

\


<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



4. Add Read & Write permission for Sites and Files

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Click Add Permissions



5. Next we need to define Scopes to used under Delegated Permissions

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Please take note of the App ID shown here\


<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

6. Next we will define the Scopes we had previously set under Permissions

The two scopes required are:

`Files.ReadWrite.All` and `Sites.ReadWrite.All`

Example Scope:

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Select Add Application

7. &#x20;We make some changes to the Manifest

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

8. &#x20;Allow client flow under Authentication

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
