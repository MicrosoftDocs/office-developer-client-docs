---
title: "Customization File SQL Section"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 002c544f-fe1b-6aeb-ba9a-97b1e1159516
description: "The sql section can contain a new SQL string that replaces the client command string. If there is no SQL string in the section, the section will be ignored."
---

# Customization File SQL Section

The **sql** section can contain a new SQL string that replaces the client command string. If there is no SQL string in the section, the section will be ignored. 
  
The new SQL string may be  *parameterized*  . That is, parameters in the **sql** section SQL string (designated by the '?' character) can be replaced by corresponding arguments in an  *identifier*  in the client command string (designated by a comma-delimited list in parentheses). The identifier and argument list behave like a function call. 
  
For example, assume the client command string is  `"CustomerByID(4)"`, the SQL section header is  `[SQL CustomerByID]`, and the new SQL section string is  `"SELECT * FROM Customers WHERE CustomerID = ?".` The Handler will generate , the SQL section header is  `[SQL CustomerByID]`, and the new SQL section string is  `"SELECT * FROM Customers WHERE CustomerID = ?".` The Handler will generate  `"SELECT * FROM Customers WHERE CustomerID = 4"` and use that string to query the data source. 
  
If the new SQL statement is the null string (""), then the section is ignored.
  
If the new SQL statement string is not valid, then the execution of the statement will fail. The client parameter is effectively ignored. You can do this intentionally to "turn off" all client SQL commands by specifying:
  
```
 
[SQL default] 
SQL = " " 

```

## Syntax

A replacement SQL string entry is of the form:
  
 **SQL= *sqlString* **
  
|**Part**|**Description**|
|:-----|:-----|
|**SQL** <br/> |A literal string that indicates this is an SQL section entry.  <br/> |
|***sqlString* ** <br/> |An SQL string that replaces the client string.  <br/> |
   

