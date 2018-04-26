---
title: "Association element Prioritization_ModifiedByResource (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b2c0d56a-d17c-4920-b040-7a7a6cab85bc
description: "The Prioritization_ModifiedByResource association relates portfolio analysis prioritizations to the resource that modified prioritizations."
---

# Association element: Prioritization_ModifiedByResource (ProjectServerData service)

The **Prioritization_ModifiedByResource** association relates portfolio analysis prioritizations to the resource that modified prioritizations. 
  
## Definition

```XML
<Association Name="Prioritization_ModifiedByResource">
  <End Type="ReportingData.Resource" Role="ModifiedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.Prioritization" Role="Prioritization" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Prioritization_ModifiedByResource** <br/> |Identifies the two entity types that form the **Prioritization_ModifiedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Prioritization_ModifiedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Prioritization_ModifiedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Prioritization** <br/> |[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |**\*** <br/> |The collection of prioritizations in the reporting tables.  <br/> |
|**ModifiedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **Prioritization_ModifiedByResource** association.  <br/> |
   
## Remarks

The **ModifiedByResource** navigation property in the **Prioritization** entity uses the **Prioritization_ModifiedByResource** association to query for a resource that performed modifications on prioritizations and is associated with a collection of portfolio analysis prioritizations. 
  
## See also

#### Reference

[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

