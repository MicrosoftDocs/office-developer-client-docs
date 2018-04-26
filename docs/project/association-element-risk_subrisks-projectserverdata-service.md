---
title: "Association element Risk_SubRisks (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: b76718fd-1f28-408d-a62d-57270595ff1e
description: "The Risk_SubRisks association relates risks to subrisks."
---

# Association element: Risk_SubRisks (ProjectServerData service)

The **Risk_SubRisks** association relates risks to subrisks. 
  
## Definition

```XML
<Association Name="Risk_SubRisks">
  <End Type="ReportingData.Risk" Role="SubRisks" Multiplicity="*" />
  <End Type="ReportingData.Risk" Role="Risk" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Risk_SubRisks** <br/> |Identifies the two entity types that form the **Risk_SubRisks** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Risk_SubRisks** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Risk_SubRisks association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Risk** <br/> |[EntityType element: Risk](entitytype-risk-projectdata-service.md) <br/> |**\*** <br/> |The collection of risks in the reporting tables.  <br/> |
|**SubRisks** <br/> |[EntityType element: Risk](entitytype-risk-projectdata-service.md) <br/> |**\*** <br/> |The collection of subrisks in the reporting tables.  <br/> |
   
## Remarks

The **SubRisks** navigation property in the **Risk** entity uses the **Risk_SubRisks** association to query subrisks that are associated with a collection of risks. 
  
## See also

#### Reference

[EntityType element: Risk](entitytype-risk-projectdata-service.md)

