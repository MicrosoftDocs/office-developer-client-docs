---
title: "Association ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 05c4eaed-81e7-4ba2-a6ac-c6c51d7decde
description: "The ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet association relates resource timephased data to a resource and relates a resource to timephased information."
---

# Association: ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet (ProjectData service)

The **ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet** association relates resource timephased data to a resource and relates a resource to timephased information. 
  
## Definition

```XML
<Association Name="ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet">
  <End Type="ReportingData.Resource" Role="Resource_TimephasedInfoDataSet" Multiplicity="0..1" />
  <End Type="ReportingData.ResourceTimephasedData" Role="ResourceTimephasedData_Resource" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet** <br/> |Identifies the entity types and the navigation properties that form the two-way association for resource timephase data and a resource. In the first half of the name, **ResourceTimephasedData** is the entity type and **Resource** is the navigation property. In the second half of the name, **Resource** is the entity type and **TimephasedInfoDataSet** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceTimephasedData_Resource** <br/> |[EntityType element: ResourceTimephasedData](entitytype-resourcetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be many resource timephased data entities that correspond to a resource.  <br/> |
|**Resource_TimephasedInfoDataSet** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |There is one resource entity that corresponds to timephased information dataset entities.  <br/> |
   
## Remarks

One end of the association is the **ResourceTimephasedData** entity, and the other end is the **Resource** entity. The **ResourceTimephasedData** entity type contains the **Resource** navigation property, where the **FromRole** defines **ResourceTimephasedData_Resource** as the start of the association to get the resource that is associated with resource timephased data. Similarly, the **Resource** entity type contains the **TimephasedInfoDataSet** navigation property, where the **FromRole** defines **Resource_TimephasedInfoDataSet** as the start of the association to get timephased information data that is associated with a resource. 
  
## See also

#### Reference

[EntityType element: Resource](entitytype-resource-projectdata-service.md)
  
[EntityType element: ResourceTimephasedData](entitytype-resourcetimephaseddata-projectdata-service.md)

