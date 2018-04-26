---
title: "Association RiskTaskAssociation_Risk (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: aed4fe69-c221-4966-979a-79cace9de43b
description: "The RiskTaskAssociation_Risk association relates a risk task assocation to a risk."
---

# Association: RiskTaskAssociation_Risk (ProjectData service)

The **RiskTaskAssociation_Risk** association relates a risk task assocation to a risk. 
  
## Definition

```XML
<Association Name="RiskTaskAssociation_Risk">
  <End Type="ReportingData.RiskTaskAssociation" Role="RiskTaskAssociation" Multiplicity="*" />
  <End Type="ReportingData.Risk" Role="Risk" Multiplicity="0..1" />
</Association>

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**RiskTaskAssociation_Risk** <br/> |Identifies the two entity types that form the **RiskTaskAssociation_Risk** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **RiskTaskAssociation_Risk** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the RiskTaskAssociation_Risk association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**RiskTaskAssociation** <br/> |[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of risk task associations in the reporting tables.  <br/> |
|**Risk** <br/> |[EntityType element: Risk](entitytype-risk-projectdata-service.md) <br/> |**0..1** <br/> |The risk object that is referenced in the **RiskTaskAssociation_Risk** association.  <br/> |
   
## Remarks

The **Risk** navigation property in the **RiskTaskAssociation** entity uses the **RiskTaskAssociation_Risk** association to query for a project that is associated with a collection of risk task associations. 
  
## See also

#### Reference

[EntityType element: Risk](entitytype-risk-projectdata-service.md)
  
[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md)

