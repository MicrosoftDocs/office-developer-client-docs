---
title: "Association BusinessDriver_ModifiedByResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: a7426ada-7f11-44e3-ab78-9bef1c6ae904
description: "The BusinessDriver_ModifiedByResource association relates business drivers to a resource."
---

# Association: BusinessDriver_ModifiedByResource (ProjectData service)

The **BusinessDriver_ModifiedByResource** association relates business drivers to a resource. 
  
## Definition

```XML
<Association Name="BusinessDriver_ModifiedByResource">
  <End Type="ReportingData.Resource" Role="ModifiedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.BusinessDriver" Role="BusinessDriver" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**BusinessDriver_ModifiedByResource** <br/> |Identifies the two entity types that form the **BusinessDriver_ModifiedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **BusinessDriver_ModifiedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the BusinessDriver_ModifiedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriver** <br/> |[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md) <br/> |**\*** <br/> |The collection of business drivers in the reporting tables.  <br/> |
|**ModifiedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **BusinessDriver_ModifiedByResource** association.  <br/> |
   
## Remarks

The **ModifiedByResource** navigation property in the **BusinessDriver** entity uses the **BusinessDriver_ModifiedByResource** association to query for a resource that is associated with a collection of business drivers. 
  
## See also

#### Reference

[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

