# How to set up SSO using Okta

## Okta Admin Portal Setup
Upon logging in to the **Okta Admin Portal** account, this is how it looks like.

<br />

![Getting Started](/Resources/Images/gettingstarted.png "Getting Started")

1. Go to **Directory** > **People** to add users to the **IdP**.

> :bulb: **Tip:** Make sure to add **Users** or **Groups** to the **Application** through **Assignments**.
   <br />

![Assignments](/Resources/Images/assignments.png "Assignments")

1. Go to **Applications** > **Applications** and select **Create App Integration**.
   <br />
![Integration](/Resources/Images/integration.png "Create App Integration")

1. Select **SAML 2.0** and hit **Next**.
	<br />
![SAML](/Resources/Images/saml2.0.png "SAML 2.0")

1. Choose an **App name**. In this case, I chose MadCap Central. 
   
2. Hit **Next**.

	For **Single Sign On URL**, set this to the **URL** of the **login page**.

		https://[vanity].madcapcentral.com/#/login

	> :bulb: **Tip:** Keep the '**Use this for Recepient URL and Destination URL**' option **checked**.


	For **Audience URI (SP Entity ID)**, set this to their **Central Site URL**.

		https://[vanity].madcapcentral.com/

	- Leave **Default RelayState** blank.

	- **Name ID format** is set to '**Unspecified**'.

	- **Application username** is set to '**Okta username**'.

	- **Update application username on** is set to '**Create and update**'.
	<br />
![Endpoints](/Resources/Images/endpoint.png "Endpoints")

6. Click '**Show Advanced Settings**'.

	We are going to add the **SAML Endpoint for Portal** and **Single Log Out (SLO)** in '**Other Requestable SSO URLs**' section. 

	The values for **SAML Endpoint for Portal** should look like this:

		https://[vanity].api.madcapcentral.com/api/users/SamlLoginSucceeded

	The values for **Single Log Out (SLO)** should look like this:

		https://[vanity].madcapcentral.com

	> :bulb: **Tip:** If they also want to add the **SAML Endpoint for Sites**, they would also add it here.
	
	The **SAML Endpoint for Sites** should look like this:

			https://[vanity].mcoutput.com/api/users/SamlLoginSucceeded	
	
	> :bulb: **Tip:** Make sure the **Index** values are different for **each** entry.
	<br />

	![Advanced Options](/Resources/Images/advancedoptions.png "Advanced Options")

7. We keep the rest of the values here to its **default values**. Then, hit **Next**.

   - Regarding the "**Are you a customer or partner?**" question, it does not matter what the user's answer is. After selecting an answer, hit **Finish**.

The **MadCap Central Application** in Okta is now ready. 
<br />
<br />

## MadCap Central Portal SSO setup

We will then need to connect this Application to their **MadCap Central License**.

1. Go to [MadCap Central Portal](portal.madcapcentral.com "MadCap Central").
2. On the top-right hand side, select the **License Icon**.
3. Select **License Settings**.
   <br />
   ![License Settings](/Resources/Images/cen_licensesettings.png "License Settings")
4. Select **Single Sign-on `[Beta]`**.
5. Select **Change Settings**.
   
6. Check **Enable SSO for Central login** option.
   <br />
   ![SSO Setup](/Resources/Images/sso_setup.png "SSO Setup")
7. We then set the values for **SAML 2.0 Login Endpoint (HTTP)**, **Identity Provider Issuer** and **Public Certificate** information.
   - The information that we need to input to the next fields can be found in **Okta Portal** > **Applications** > **Applications** > **Sign On** tab > **View SAML setup instructions**
  	<br />

	![SAML Instructions](/Resources/Images/samlinstructions.png "SAML Instructions")
	<br />
	<br />
	We should see this page here:
	<br />
	
	![SAML Information](/Resources/Images/samlinfo.png "SAML Information")

	We then use these information to fill out the fields in Central portal.

   > :bulb: **Tip:** **The SLO Logout Endpoint** is optional.
<br />

   - Set **SAML 2.0 Login Endpoint (HTTP)** to **Identity Provider Single Sign-On URL**
  
   - Set **Identity Provider Issuer** to **Identity Provider Issuer**
   - Set **Public Certificate** to **X.509 Certificate**
	<br />
	<br />
	![SAML Information](/Resources/Images/xrefsamlinfo.png "SAML Information")










