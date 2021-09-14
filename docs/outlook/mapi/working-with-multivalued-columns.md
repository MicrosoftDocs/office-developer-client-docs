---
title: "Working with Multivalued Columns"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 911a41c3-c10f-4473-8853-fafb56b721ba
description: "Last modified: July 23, 2011"
 
 
---

# Working with Multivalued Columns

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A multivalued column contains the data of a multivalued property, which is a property that has an array of values of the base type instead of a single value. Because none of the tables include multivalued properties in their default column sets, multivalued properties are included in a table only if the user of the table requests it. 
  
Multivalued columns can be displayed in tables:
  
- In a single row, with all of the property values appearing in the single column instance. This is the default.
    
    - Or -
    
- In a series of rows, with one row for each of the property values. Each unique value appears in the column in its own row with there being as many rows as there are values in the multivalued property. Each row has a unique value for the **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property, but the same values for the other columns. If a row contains more than one column with multiple values, for example, two columns with  _M_ and  _N_ values respectively, then  _M\*N_ instances of the row appear in the table. 
    
A table user requests the nondefault type of display by calling the [IMAPITable::SetColumns](imapitable-setcolumns.md) method with the MVI_FLAG flag set in the property type of the multivalued column. The MVI_FLAG flag is a constant defined as the result of combining the MV_FLAG and MV_INSTANCE flags with a logical **OR** operation. In addition to being used in **SetColumns**, MVI_FLAG can also be passed to [IMAPITable::SortTable](imapitable-sorttable.md) in the  _lpSortCriteria_ parameter and [IMAPITable::Restrict](imapitable-restrict.md) in the **ulPropTag** member of the  _lpRestriction_ parameter. When passed the MVI_FLAG, **SortTable** performs similarly to **SetColumns**, adding one row for each value in the multivalued column and sorting on the single values in the instances. One row is added for each value. 
  
 **Restrict**, however, does not expand the multivalued column into additional computed rows. A multivalued column with the MVI_FLAG set instructs the service provider to use that column in restricting the table. If there is a property value in the restriction, it must be a single value property tag identical to the one that would be returned by [IMAPITable::QueryRows](imapitable-queryrows.md) for the column. 
  
Table implementers are only required to support the default type of display and can return the MAPI_E_TOO_COMPLEX value when a caller requests the other alternative. The ability to support both types of display is most important for message store providers implementing folder contents tables. 
  
## See also



[MAPI Tables](mapi-tables.md)

