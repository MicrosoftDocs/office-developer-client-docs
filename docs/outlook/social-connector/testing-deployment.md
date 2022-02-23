---
title: "Testing deployment"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 8b585200-33e7-4607-a603-0c7e52a6b09d
description: "This topic describes some scenarios that you should test for regarding installing and uninstalling an Outlook Social Connector (OSC) provider."
---

# Testing deployment

This topic describes some scenarios that you should test for regarding installing and uninstalling an Outlook Social Connector (OSC) provider.

<a name="olosc_TestingDeployment_PresenceOfOutlook"> </a>

## Presence of Outlook and the OSC on client computer

Factors the affect installing an OSC provider includes the bitness of the operating system, the presence and bitness of Outlook, and the OSC being enabled in Outlook.
  
An OSC provider can be written for either a 32-bit or 64-bit version of the OSC. Outlook 2010 and Outlook 2013 are available in both 32-bit and 64-bit versions, and Office Outlook 2003 and Office Outlook 2007 are available in only 32-bit versions. On a 64-bit Windows operating system, you can install either 32-bit or 64-bit Outlook. On a 32-bit operating system, you can install only 32-bit, but not 64-bit, Outlook. Depending on the bitness of the installed version of Outlook and the OSC provider itself, the user should use the appropriate installer to install an OSC provider of the appropriate bitness. For example, if 64-bit Outlook is installed, and the OSC provider is a native COM component, a 32-bit OSC provider will not work and the user must use the appropriate installer to install a 64-bit OSC provider.
  
The deployment code of your OSC provider can assume that the user has a supported version of Outlook on the computer. However, if the current version of OSC is not on the client computer, your deployment code can download and install an appropriate version of the OSC by using specially constructed g-link URLs on <https://g.live.com>. These g-links depend on the version and bitness of Outlook and the locale of the client computer. For more information about using g-links to install or update the OSC, see [Installation checklist](installation-checklist.md).
  
Before installing an OSC provider, the Outlook user should ensure that the OSC add-in is enabled in Outlook.
  
The recommended method of deploying an OSC provider is to use a Windows Installer (.msi) package. Test each of the following scenarios to verify deployment works appropriately for the provider.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Outlook is not present - Outlook 2003 or Outlook 2007 is not installed, and Outlook 2010 or Microsoft Outlook 2013 is not installed nor has it been delivered by Click-to-Run. |The deployment fails. |
|Outlook 2003 or Outlook 2007 is not installed, but Outlook 2010 or Microsoft Outlook 2013 has been delivered by Click-to-Run. |The 32-bit provider is deployed. |
|Outlook 2003 or Outlook 2007 is installed, but the OSC is not installed. |The installer installs the OSC and all patches. Once the OSC has been installed successfully, then the installer deploys the provider. |
|Outlook 2003 or Outlook 2007 is installed, and an earlier version of the OSC is installed. |The installer updates the OSC, via a g-link to patches, and then deploys the provider. |
|Outlook 2003 or 2007 is installed and the OSC is up-to-date. |The installer deploys the 32-bit provider. |
|Outlook 2010 or Microsoft Outlook 2013 is installed but the OSC is not installed. |The installer fails with an appropriate error message. |
|Outlook 2010 or Microsoft Outlook 2013 is installed and an older version of the OSC is installed. |The installer which is appropriate for the bitness of the installed Outlook 2010 or Microsoft Outlook 2013, updates the OSC via the g-link to patches, and then deploys the appropriate provider. |
|Outlook 2010 or Microsoft Outlook 2013 is installed and the OSC is up-to-date. |The installer that is appropriate for the bitness of the installed Outlook 2010 or Microsoft Outlook 2013 (32-bit or 64-bit) deploys the appropriate provider. |

<a name="olosc_TestingDeployment_PresenceOfOutlook"> </a>

## Installed location and registry keys

Verify the file location where your OSC provider has been deployed, and the locations in the Windows registry where registry keys for your provider are created.
  
### File location for OSC provider DLLs

Test for the scenarios as listed in the following table. Note that the table lists the default installation paths for OSC provider DLLs. Users can customize where they install these DLLs.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Microsoft Outlook 2013 is installed on the client computer. |Provider DLLs are deployed into the Office15 folder. If the operating system is 64-bit and Microsoft Outlook 2013 is 32-bit, the 32-bit DLLs are deployed under C:\Program Files (x86)\Microsoft Office\Office15. If the operating system is 64-bit and Microsoft Outlook 2013 is 64-bit, the 64-bit DLLs are deployed under C:\Program Files\Microsoft Office\Office15. If the operating system is 32-bit, DLLs are deployed under C:\Program Files\Microsoft Office\Office15. |
|Outlook 2010 is installed on the client computer. |Provider DLLs are deployed into the Office14 folder. If the operating system is 64-bit and Outlook 2010 is 32-bit, the 32-bit DLLs are deployed under C:\Program Files (x86)\Microsoft Office\Office14. If the operating system is 64-bit and Outlook 2010 is 64-bit, the 64-bit DLLs are deployed under C:\Program Files\Microsoft Office\Office14. If the operating system is 32-bit, DLLs are deployed under C:\Program Files\Microsoft Office\Office14. |
|Outlook 2007 is installed on the client computer. |Provider DLLs are deployed under C:\Program Files\Microsoft Office\Office14. Installing the OSC creates the Office14 folder, and the OSC should be installed before any provider DLLs. See the previous section [Presence of Outlook and the OSC on Client Computer](#olosc_TestingDeployment_PresenceOfOutlook). |
|Outlook 2003 is installed on the client computer. |Provider DLLs are deployed under C:\Program Files\Microsoft Office\Office14. Installing the OSC creates the Office14 folder, and the OSC should be installed before any provider DLLs. See the previous section [Presence of Outlook and the OSC on Client Computer](#olosc_TestingDeployment_PresenceOfOutlook). |
|Microsoft Outlook 2013 is not installed but delivered by Click-to-Run on the client computer. |Provider DLLs are deployed into the Office15 folder. If the operating system is 64-bit, 32-bit DLLs are deployed under C:\Program Files (x86)\Microsoft Office\Office15 or C:\Program Files\Microsoft Office\Office15. If the operating system is 32-bit, DLLs are deployed under C:\Program Files\Microsoft Office\Office15. If the Office15 folder does not exist, the installation creates the folder. |
|Outlook 2010 is not installed but delivered by Click-to-Run on the client computer. |Provider DLLs are deployed into the Office14 folder. If the operating system is 64-bit, 32-bit DLLs are deployed under C:\Program Files (x86)\Microsoft Office\Office14 or C:\Program Files\Microsoft Office\Office14. If the operating system is 32-bit, DLLs are deployed under C:\Program Files\Microsoft Office\Office14. If the Office14 folder does not exist, the installation creates the folder. |

### Windows registry locations

Verify the following:
  
- The OSC provider installer creates a ProgID value for the OSC provider in the Windows registry, in either `HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders` or `HKEY_LOCAL_MACHINE\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`.

- The exception is if the client computer has 32-bit Outlook running on a 64-bit Windows operating system. In this case, the ProgID is created in either `HKEY_CURRENT_USER\Software\Wow6432Node\Microsoft\Office\Outlook\SocialConnector\SocialProviders` or `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Office\Outlook\SocialConnector\SocialProviders`.

- The registry keys should be the same and in the same location if, instead, the DLLs are registered by regsvr32.exe.

<a name="olosc_TestingDeployment_PresenceOfOutlook"> </a>

## Removing the installation

The following are some tests to verify that the uninstall process works properly for your OSC provider.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|User chooses to uninstall the provider. |The provider uninstalls the DLLs and clears the registry. |
|User chooses to cancel the uninstall process of the provider. |The provider cancels the uninstall process and brings the user back to the state before the uninstall process started. |

## See also

- [Registering a Provider](registering-a-provider.md)  
- [Installation Checklist](installation-checklist.md)
- [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)
