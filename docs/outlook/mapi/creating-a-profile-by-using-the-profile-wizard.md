---
title: "Creating a Profile by Using the Profile Wizard"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 4b611818-f99f-43a2-9f6b-1aa5b9564d1d
description: "Last modified: July 23, 2011"
---

# Creating a Profile by Using the Profile Wizard

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The Profile Wizard is a MAPI feature that enables a user to create a profile in the easiest possible way. The Profile Wizard displays a series of dialog boxes which prompt the user to select message services and enter values for a few of the most essential configuration properties. For most of the other required properties, the Profile Wizard uses default values provided. To invoke the Profile Wizard, call **LaunchWizard**, a function based on the [LAUNCHWIZARDENTRY](launchwizardentry.md) prototype. 
  
The user can add only those message services and service providers to the new profile that support the Profile Wizard. Because each message service might require more properties to be set than the Profile Wizard can handle, be aware that if you use this approach, it is possible for one or more of the selected services or providers to be incompletely configured.
  

