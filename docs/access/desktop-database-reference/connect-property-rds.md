---
title: Connect property (RDS)
TOCTitle: Connect property (RDS)
ms:assetid: 11aa3284-18e9-6d2d-761b-c25090370b77
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248890(v=office.15)
ms:contentKeyID: 48543324
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Connect property (RDS)

**Applies to**: Access 2013, Office 2013

Indicates the database name from which the query and update operations are run.

You can set the **Connect** property at design time in the [RDS.DataControl](datacontrol-object-rds.md) object's OBJECT tags, or at run time in scripting code (for instance, VBScript).

## Syntax

Design time: \<PARAM NAME="Connect" VALUE="ConnectionString"\>

Run time: DataControl.Connect = "ConnectionString"

## Parameters

|Parameter|Description|
|:--------|:----------|
|*ConnectionString* |A valid connection string. For more general information about connection strings, see the [ConnectionString](connectionstring-property-ado.md) property or your provider documentation.<br/><br/>**NOTE**: Specifying MS Remote as the provider for the **RDS.DataControl** would create a four-tier scenario. Scenarios greater than three tiers have not been tested and should not be needed.|
|*DataControl* |An object variable that represents an **RDS.DataControl** object.|

