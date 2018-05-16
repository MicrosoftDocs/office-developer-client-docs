---
title: "How to Create an Outlook profile using MFCMAPI"
ms.date: 5/18/2016
ms.audience: Developer
localization_priority: Normal
ms.assetid: 85581bc7-2d81-46af-8836-adef39c933fc
description: "MFCMAPI provides access to MAPI stores to facilitate investigation of Exchange and Outlook issues and to provide developers with support for MAPI development."
 
 
---

# How to: Create an Outlook profile using MFCMAPI

MFCMAPI provides access to MAPI stores to facilitate investigation of Exchange and Outlook issues and to provide developers with support for MAPI development.
  
 **Last modified:** May 18, 2016 
  
 * **Applies to:** Office 365 | Outlook | Outlook 2016 * 
  
For non-developers, it is recommended that you use the Outlook user interface to create profiles for Exchange 2013.
  
## Configure an Outlook profile using MFCMAPI

1. Open [MFCMAPI](https://mfcmapi.codeplex.com/), and on the **Profile** menu, click **Show Profiles**. 
    
2. On the **Actions** menu, click **Create Profile**. 
    
3. Create a new name for the profile, and then click **OK**. 
    
4. Right-click the new profile, and then on the **Services** menu, click **Add Service**. 
    
5. Uncheck the"Display Service UI" box, and then click **OK**. 
    
6. Double-click the newly created profile, and then click the **MSEMS** service. 
    
7. Locate the Exchange Profile section.
    
    This can be difficult in Outlook's MAPI, since in 2010 and above there is no longer the global profile section. To find the Profile section, find the property PR_EMSMDB_SECTION_UID (0x3D150102). The value will be the GUID of the profile section persisted in binary form, which will be used in the subsequent steps. You will need this value in step 9.
    
8. Double-click the **MSEMS** service. 
    
9. Find the **Exchange** profile section by using the UID from step 7, and then single-click to select the row. 
    
10. On the Property menu, click **Additional Properties**. 
    
11. Click **Add** and add the following properties: 
    
    ** *For Outlook 2016* **: PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W (0x6641001F) and PR_DISPLAY_NAME_W. 
    
    ** *For Outlook for Office 365* **: PR_PROFILE_UNRESOLVED_NAME, PR_PROFILE_UNRESOLVED_SERVER, PR_ROH_PROXY_SERVER, PR_ROH_FLAGS, PR_ROH_PROXY_AUTH_SCHEME, PR_PROFILE_AUTH_PACKAGE, and PR_ROH_PROXY_PRINCIPAL_NAME 
    
     * **For Exchange 2013*** : PR_PROFILE_UNRESOLVED_NAME, PR_PROFILE_UNRESOLVED_SERVER, PR_ROH_PROXY_SERVER, PR_ROH_FLAGS, PR_ROH_PROXY_AUTH_SCHEME, and PR_PROFILE_AUTH_PACKAGE. 
    
12. Click **OK**, and then configure each property according to the table below, depending on the version you are connecting to. 
    
13. On the **Session** menu, click **Logon and Display Store**, and then select the profile (if it is not already selected). 
    
 ** *For Outlook 2016* **
  
||||
|:-----|:-----|:-----|
|**Property** <br/> |**Tag** <br/> |**Description** <br/> |
| PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W  <br/> |0x6641001F  <br/> |SMTP Address of the user  <br/> |
|PR_DISPLAY_NAME_W  <br/> |0x3001001F  <br/> |The display name of the user  <br/> |
|PR_STORE_PROVIDERS  <br/> |0x3D000102  <br/> |Configure the value of this property, located in the **EMSMDB** section, and update the corresponding UID for the matching property  <br/> |
   
 ** *For Outlook for Office 365* **
  
||||
|:-----|:-----|:-----|
|**Property** <br/> |**Value** <br/> |**Description** <br/> |
|PR_PROFILE_UNRESOLVED_NAME<sup>1</sup> <br/> |mailbox alias  <br/> |The alias for the target mailbox; for example, Administrator  <br/> |
|PR_PROFILE_UNRESOLVED_SERVER<sup>1</sup> <br/> |personalized server id  <br/> |The value retrieved from **Autodiscover**. in the format <guid>@tenant.onmicrosoft.com; for example, F5FA2827-5978-43cd-8FA8-E07BC3BB5591@contoso.onmicrosoft.com  <br/>  *Autodiscover Node*  : Response/Account/Protocol/Server (EXCH)  <br/> |
|PR_ROH_PROXY_SERVER  <br/> |outlook.office365.com  <br/> | *Autodiscover Node*  : Response/Account/Protocol/Server (EXPR) <sup>2</sup> <br/> |
|PR_ROH_FLAGS  <br/> |ROHFLAGS_USE_ROH (0x1)  <br/> ROH_FLAGS_USE_SSL (0x2)  <br/>  ROHFLAGS_MUTUAL_AUTH (0x4)  <br/>  ROHFLAGS_HTTP_FIRST_ON_FAST (0x8)  <br/>  ROHFLAGS_HTTP_FIRST_ON_SLOW (0x20)  <br/> |Contains the settings in a profile used by Outlook to connect to Microsoft Exchange Server by using a remote procedure call (RPC) over Hypertext Transfer Protocol (HTTP). *Autodiscover Node*  : Response/Account/Protocol/SSL (EXPR) <sup>2</sup> <br/> |
| PR_ROH_PROXY_AUTH_SCHEME  <br/> | RPC_C_HTTP_AUTHN_SCHEME_BASIC (0x1)  <br/> |Represents the authentication protocol to be used for this profile *Autodiscover Node*  : Response/Account/Protocol/AuthPackage (EXPR) <sup>2</sup> <br/> |
|PR_PROFILE_AUTH_PACKAGE  <br/> |RPC_C_AUTHN_NONE (0x0)  <br/> |Describes the authentication scheme to use for the RPC *Autodiscover Node*  : Response/Account/Protocol/AuthPackage (EXCH) ) <sup>3</sup> <br/> |
|PR_ROH_PROXY_PRINCIPAL_NAME  <br/> |CertPrincipalName element  <br/> |Used to support mutual authentication; for example, msstd:outlook.com *Autodiscover Node*  : Response/Account/Protocol/CertPrincipalName (EXPR) ) <sup>2</sup> <br/> |
   
 ** *For Exchange 2013* **
  
||||
|:-----|:-----|:-----|
|**Property** <br/> |**Value** <br/> |**Description** <br/> |
|PR_PROFILE_UNRESOLVED_NAME<sup>1</sup> <br/> |mailbox alias  <br/> |The alias for the target mailbox; for example, Administrator  <br/> |
|PR_PROFILE_UNRESOLVED_SERVER<sup>1</sup> <br/> |personalized server id  <br/> |The value retrieved from **Autodiscover**. in the format <guid>@tenant.onmicrosoft.com; for example, F5FA2827-5978-43cd-8FA8-E07BC3BB5591@contoso.onmicrosoft.com  <br/>  *Autodiscover Node*  : Response/Account/Protocol/Server (EXCH)  <br/> |
|PR_ROH_PROXY_SERVER  <br/> | client access server domain name  <br/> | The fully qualified domain name (FQDN); for example, e2013cas.contoso.com  *Autodiscover Node*  : Response/Account/Protocol/Server (EXPR) <sup>2</sup> <br/> |
|PR_ROH_FLAGS  <br/> |ROHFLAGS_USE_ROH (0x1)  <br/>  ROHFLAGS_HTTP_FIRST_ON_FAST (0x8)  <br/> ROHFLAGS_HTTP_FIRST_ON_SLOW (0x20))  <br/> |Contains the settings in a profile used by Outlook to connect to Microsoft Exchange Server by using a remote procedure call (RPC) over Hypertext Transfer Protocol (HTTP) *Autodiscover Node*  : Response/Account/Protocol/SSL (EXPR) <sup>2</sup> <br/> |
| PR_ROH_PROXY_AUTH_SCHEME  <br/> | RPC_C_HTTP_AUTHN_SCHEME_NTLM (0x2)  <br/> |Represents the authentication protocol to be used for this profile *Autodiscover Node*  : Response/Account/Protocol/AuthPackage (EXPR) <sup>2</sup> <br/> |
|PR_PROFILE_AUTH_PACKAGE  <br/> |RPC_C_AUTHN_WINNT (0xA)  <br/> |Describes the authentication scheme to use for RPC *Autodiscover Node*  : Response/Account/Protocol/AuthPackage (EXCH) ) <sup>3</sup> <br/> |
   
 **Additional Notes**
  
- All property values mentioned above may vary for your particular organization. 
    
- <sup>1</sup> You must use the Unicode version, rather than the ANSI version. 
    
- You must use the Plain Old XML (POX) based Autodiscover. This is the only supported Autodiscover for configuring Outlook/Exchange profiles.
    
- You can use Outlook to make an Autodiscover request on your behalf by right-clicking the Outlook icon in the **System Tray**, while holding down CTRL and clicking **Test E-Mail Autoconfiguration**. 
    
- For PR_ROH_FLAGS, your environment may require the flag ROHFLAGS_SSL_ONLY (0x2) to tell MAPI to use only SSL. If your environment requires mutual authentication, you will need to set that flag as well [ROHFLAGS_MUTUAL_AUTH (0x4)]. Setting ROHFLAGS_MUTUAL_AUTH (0x4) will require that you also set the property PR_ROH_PROXY_PRINCIPAL_NAME. You should set this to be the principal name of the server.
    
- <sup>2</sup> For Outlook 2010, you will need to use the EXPR protocol. Outlook 2013 uses the EXHTTP protocol. 
    
    <sup>3</sup> This value may not be in the Autodiscover response. If not specified, the client should use Kerberos or NTLM. 
    
For Troubleshooting tips, see [How to configure an Outlook profile using MFCMAPI for Exchange 2013](https://blogs.msdn.microsoft.com/dvespa/2014/01/16/how-to-configure-an-outlook-profile-using-mfcmapi-for-exchange-2013)
  
## See also
<a name="bk_addresources"> </a>

- [Outlook MAPI Reference](https://msdn.microsoft.com/en-us/library/office/cc765775.aspx)
    
- [How to: Programmatically Create a Profile in Outlook](https://msdn.microsoft.com/en-us/library/office/mt707568.aspx)
    

