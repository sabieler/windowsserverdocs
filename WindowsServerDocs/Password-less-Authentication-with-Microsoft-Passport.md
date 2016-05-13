---
title: Password-less Authentication with Microsoft Passport
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-identity
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af3f406f-8d26-4535-a7c7-9af186573ef9
robots: noindex,nofollow
---
# Password-less Authentication with Microsoft Passport
**This is preliminary content and subject to change.**

The current methods of authentication with passwords alone are not sufficient to keep users safe. Users reuse and forget passwords. Passwords are breachable, phishable, prone to cracks, and guessable. They also get difficult to remember and prone to attacks like “pass the hash”.

## What is Microsoft Passport
Microsoft Passport is a new private\/public key or certificate\-based authentication approach for organizations and consumers that goes beyond passwords. This form of authentication relies on these key pair credentials that can replace passwords and be resistant to breaches, thefts and phishing  Microsoft Passport lets users authenticate to a Microsoft account, an Active Directory account, a Microsoft Azure Active Directory \(AD\) account, or non\-Microsoft service that supports Fast ID Online \(FIDO\) authentication. After an initial two\-step verification during Microsoft Passport enrollment, a Microsoft Passport is set up on the user's device and the user sets a gesture, which can be Windows Hello or a PIN. The user provides the gesture to verify identity; Windows then uses Microsoft Passport to authenticate users and help them to access protected resources and services.

The private key is made available solely through a “user gesture” like a PIN, biometrics, remote device like a smart card that the user used to log on to the device and this information is linked to a certificate or an asymmetrical key pair. This private\-key is hardware attested if device has a Trusted Platform Module \(TPM\) chip. The private key never leaves the device.

The public key is registered with Azure Active Directory and Windows Server Active Directory \(for On\-Premises\). The Identity Providers \(IDPs\) validate the user by mapping the public key of the user to the private key and provides log on information through One Time Password \(OTP\), Phonefactor or a different notification mechanism.

## Why should enterprises adopt Microsoft Passport
By enabling Microsoft Passport, enterprises can make their resources even more secure by:

-   Setting up Microsoft Passport with a hardware\-preferred option, which means that keys will be generated on TPM 1.2 or TPM 2.0 when available and by software when TPM is not available.

-   Defining the complexity and length of the PIN, and whether Hello usage is enabled in your organization

-   Configuring Microsoft Passport to support smart card\-like scenarios using certificate\-based trust.

## How it works

1.  Keys are generated on the hardware. A lot of machines have a built\-in Trusted Platform Module \(TPM\) chip that secures the hardware by integrating cryptographic keys into devices. The TPM 1.2 or TPM 2.0 is used to generate keys or certificates that will be keyed out of the keys generated.

2.  These hardware\-bound keys are attested by the TPM and enterprises can

3.  Single unlock gesture will unlock the device and this gesture will be allowed to get access to multiple resources if the device is domain\-joined or Azure AD Joined.

**Microsoft Passport lifecycle**

![](media/AD_WindowsPassport.bmp)

The above diagram illustrates the private\-public key pair and the validation by the identity provider. Each of these steps are explained in detail below:

1.  User proves his\/her identity through multiple built\-in proofing methods \(gestures, physical smart cards, Multifactor Authentication\) and sends this information to the Identity Provider \(IDP\) like Azure Active Directory or Active Directory.

2.  The device then creates the keys, attests the key, takes the public portion of this key, attach it with station statements, signs in and sends it to IDP to register this key.

3.  As soon as the public portion of the key is registered in the IDP, it challenges the device to sign with the private portion of the key. The IDP then validates and issues the authentication token that lets the user access protected resources.

4.  As soon as the public portion of the key is registered in the IDP, it challenges the device for the challenge to sign with the private portion of the key.

5.  IDP then validates and issues the authentication token that lets the user and device access protected resources. IDPs can write cross\-platform apps or use browser support via JS\/Webcrypto APIs\) to create and use Microsoft Passport credentials for their users.

**Types of keys**

Microsoft Passport consists of three sets of keys:

-   KNGC pair of asymmetric keys

    -   Always require a user gesture \(pin or bio\) for an authentication operation

    -   HW attested, SW as a last resort

-   KIDP key\(s\) \(symmetric or asymmetric\)

    -   Delegated by KNGC keys

    -   Do not require a user gesture

    -   long lived

    -   If symmetric, wrapped with a transport key \(transport key is attested\)

-   KRP, used to access RP resources

    -   Delegated by KIDP key

    -   Do not require user gesture

    -   Symmetric and short lived

## Deployment Requirements
**At the enterprise level**

-   Azure Subscription

    or

-   Azure Subscription \+ AAD Connect if it’s a hybrid environment

    or

-   Windows Server 10 Active Directory and AD FS Server 10 if on\-prem\-only \(

    > [!NOTE]
    > Certificate\-based Passport does not require Active Directory upgrade if your organization has a PKI infrastructure\)

**At the user level**

-   Computer must run [!INCLUDE[winthreshold_client_2](includes/winthreshold_client_2_md.md)]

