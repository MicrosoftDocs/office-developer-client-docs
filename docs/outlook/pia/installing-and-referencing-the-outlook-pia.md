---
title: Installing and Referencing the Outlook PIA
TOCTitle: Installing and Referencing the Outlook PIA
ms:assetid: b1afd047-dcbb-480f-ba74-993d7d7114cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb646840(v=office.15)
ms:contentKeyID: 55119774
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Installing and Referencing the Outlook PIA

You must have the Outlook Primary Interop Assembly (PIA) installed in the Global Assembly Cache (GAC) before you can incorporate information from the PIA in an Outlook managed add-in. By default, the PIA is installed automatically when you install Office on the development computer. However, if you need to install the PIA separately, see [Configuring a Computer to Develop Office Solutions](https://msdn.microsoft.com/en-us/library/bb398242\(v=office.15\)) and [How to: Configure a Computer to Develop Office Solutions](https://msdn.microsoft.com/en-us/library/54ds2za4\(v=office.15\)) for more information.


> [!NOTE]
> <P>You must be an administrator on the development computer to install the Office PIAs.</P>



After installation, if you are using Visual Studio to create the managed project, you can add a reference to the **Microsoft Outlook 15.0 Object Library** component. Subsequently, in the object browser, under the **Microsoft.Office.Interop.Outlook** namespace, you can see managed interfaces in the PIA that have names corresponding to objects in the Outlook object model.

## See also

#### Other resources

[How to: Install Office Primary Interop Assemblies](https://msdn.microsoft.com/en-us/library/kh3965hw\(v=office.15\))

[Architecture of the Outlook PIA](architecture-of-the-outlook-pia.md)

