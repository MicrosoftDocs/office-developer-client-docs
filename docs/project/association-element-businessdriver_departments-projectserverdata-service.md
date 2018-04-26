---
title: "Association element BusinessDriver_Departments (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: cc062254-fdb5-4eb4-b0ea-2bd91ae60aa7
description: "The BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver association relates a business driver to departments that it contains and relates business driver departments to a business driver."
---

# Association element: BusinessDriver_Departments (ProjectServerData service)

The **BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver** association relates a business driver to departments that it contains and relates business driver departments to a business driver. 
  
## Definition

```XML
<Association Name="BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver">
  <End Type="ReportingData.BusinessDriverDepartment" Role="BusinessDriverDepartment_BusinessDriver" Multiplicity="*" />
  <End Type="ReportingData.BusinessDriver" Role="BusinessDriver_Departments" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver** <br/> |Identifies the entity types and the navigation properties that form the two-way association for business drivers and business driver departments. In the first half of the name, **BusinessDriver** is the entity type and **Departments** is the navigation property. In the second half of the name, **BusinessDriverDepartment** is the entity type and **BusinessDriver** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriver_Departments** <br/> |[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md) <br/> |**0..1** <br/> |There is one business driver entity that corresponds to a collection of business driver departments.  <br/> |
|**BusinessDriverDepartment_BusinessDriver** <br/> |[EntityType element: BusinessDriverDepartment](entitytype-businessdriverdepartment-projectdata-service.md) <br/> |**\*** <br/> |There can be many business driver department entities that correspond with a business driver.  <br/> |
   
## Remarks

One end of the association is the **BusinessDriver** entity, and the other end is the **BusinessDriverDepartment** entity. The **BusinessDriver** entity type contains the **Departments** navigation property, where the **FromRole** defines **BusinessDriver_Departments** as the start of the association to get the collection of departments in a business driver. Similarly, the **BusinessDriverDepartment** entity type contains the **BusinessDriver** navigation property, where the **FromRole** defines **BusinessDriverDepartment_BusinessDriver** as the start of the association to get the business driver that is associated with a collection of business driver departments. 
  
## See also

#### Reference

[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md)
  
[EntityType element: BusinessDriverDepartment](entitytype-businessdriverdepartment-projectdata-service.md)

