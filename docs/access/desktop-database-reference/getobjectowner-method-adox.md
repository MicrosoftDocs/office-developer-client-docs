---
title: GetObjectOwner method (ADOX)
TOCTitle: GetObjectOwner method (ADOX)
ms:assetid: 716dd49a-8663-3f7a-32a3-0be353aea506
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249451(v=office.15)
ms:contentKeyID: 48545585
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# GetObjectOwner method (ADOX)

**Applies to**: Access 2013, Office 2013

Returns the owner of an object in a [Catalog](catalog-object-adox.md).

## Syntax

*Owner* = *Catalog*.GetObjectOwner(*ObjectName*, *ObjectType* \[,*ObjectTypeId*\])

## Return value

Returns a **String** value that specifies the [Name](name-property-adox.md) of the [User](user-object-adox.md) or [Group](group-object-adox.md) that owns the object.

## Parameters

|Parameter|Description|
|:--------|:----------|
|*ObjectName* |A **String** value that specifies the name of the object for which to return the owner.|
|*ObjectType* |A **Long** value which can be one of the [ObjectTypeEnum](objecttypeenum.md) constants, that specifies the type of the object for which to get the owner.|
|*ObjectTypeId* |Optional. A **Variant** value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if *ObjectType* is set to **adPermObjProviderSpecific**; otherwise, it is not used.|

## Remarks

An error will occur if the provider does not support returning object owners.

