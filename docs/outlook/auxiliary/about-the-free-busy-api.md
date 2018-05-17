---
title: "About the Free/Busy API"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 17c5e44e-ae56-8de7-3579-90171d996411
description: "The Free/Busy API allows mail providers to provide free/busy status information for specified user accounts within a specified time range. The free/busy status of a block of time on a user's calendar is one of the following: out-of-office, busy, tentative, or free."
---

# About the Free/Busy API

The Free/Busy API allows mail providers to provide free/busy status information for specified user accounts within a specified time range. The free/busy status of a block of time on a user's calendar is one of the following: out-of-office, busy, tentative, or free.
  
## Create a Free/Busy Provider

To provide free/busy information to mail users, a mail provider creates a free/busy provider and registers it with Outlook. The free/busy provider must implement the following interfaces. Note that a number of members in these interfaces are not supported and must return the specified return values. In particular, the Free/Busy API does not support write access to free/busy information and delegate access to accounts.
  
- [IFreeBusySupport](ifreebusysupport.md) —This interface supports specification of interfaces that access free/busy data for specified users. It uses [FBUser](fbuser.md) to identify a user. 
    
- [IFreeBusyData](ifreebusydata.md) —This interface gets and sets a time range for a given user and returns an interface for enumerating free/busy blocks of data within this time range. It uses relative time to get and set this time range. For more information, see [Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md).
    
- [IEnumFBBlock](ienumfbblock.md) —This interface supports accessing and enumerating free/busy blocks of data for a user within a time range. 
    
    > [!NOTE]
    > An enumeration contains free/busy blocks that indicate the free/busy status of periods of time on a user's calendar, within a time range (specified by [IFreeBusyData::EnumBlocks](ifreebusydata-enumblocks.md)). Items on a calendar, such as appointments and meeting requests, form blocks in the enumeration. Items that are adjacent to one another on the calendar and have the same free/busy status are combined to form one single block. A free period of time on a calendar also forms a block. Therefore, no two consecutive blocks in an enumeration would have the same free/busy status. These blocks do not overlap in time. When there are overlapping items on a calendar, Outlook merges these items to form non-overlapping free/busy blocks in the enumeration based on this order of precedence: out-of-office, busy, tentative. 
  
To register the free/busy provider with Outlook, the mail provider should do the following:
  
1. Register the free/busy provider with COM, providing a CLSID that allows access to the provider's implementation of **IFreeBusySupport**. 
    
2. Let Outlook know that the free/busy provider exists by setting the following key (where \<xx.x\> represents the version of Outlook) in the system registry: 
    
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\\<xx.x\>\Outlook\SchedulingInformation\FreeBusySupport
    
    For example, if the transport provider is SMTP, to register the provider with Microsoft Outlook 2010, set the following key to the data in the following table: 
    
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\14.0\Outlook\SchedulingInformation\FreeBusySupport
    
||||
|:-----|:-----|:-----|
|**Name** <br/> |**Type** <br/> |**Value** <br/> |
|SMTP  <br/> |REG_SZ  <br/> |{CLSID for respective implementation of IFreeBusySupport}  <br/> |
   
    In this scenario, Outlook will co-create the COM class and use it to retrieve free/busy information for any SMTP mail users.
    
To support an address book and transport provider that use an address entry type other than SMTP, change the  *Name*  accordingly. 
  
> [!NOTE]
> During installation, free/busy providers should check whether a registry setting for the the same address entry type already exists. If it does, the free/busy provider should overwrite the current provider for that address entry type, and restore to that provider when it uninstalls. However, if a user has installed more than one free/busy provider for the same address entry type, the user should uninstall these providers in the reverse order as installation (that is, always uninstall the latest provider). Otherwise, the registry may point to a provider that has already been uninstalled. 
  
## API Components

The Free/Busy API includes the following components:
  
## Definitions

- [Constants (Free/busy API)](constants-free-busy-api.md)
    
## Data Types

- [FBBlock_1](fbblock_1.md)
    
- [FBStatus](fbstatus.md)
    
- [FBUser](fbuser.md)
    
## Interfaces

- [IEnumFBBlock](ienumfbblock.md)
    
- [IFreeBusyData](ifreebusydata.md)
    
- [IFreeBusySupport](ifreebusysupport.md)
    

