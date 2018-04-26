---
title: "Fabricating Hierarchical Recordsets"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0a6e41ba-015e-c07e-8876-1e744256b876

---

# Fabricating Hierarchical Recordsets

The following example shows how to fabricate a hierarchical Recordset without an underlying data source by using the data shaping grammar to define columns for parent, child, and grandchild **Recordsets**. 
  
To fabricate a hierarchical **Recordset**, you must specify the Microsoft Data Shaping Service for OLE DB (MSDataShape), and you may specify a Data Provider value of NONE in the connection string parameter of the [Connection](connection-object-ado.md) object's [Open](open-method-ado-connection.md) method. For more information, see [Required Providers for Data Shaping](required-providers-for-data-shaping.md).
  
```
Dim cn As New ADODB.Connection
Dim rsCustomers As New ADODB.Recordset
cn.Open "Provider=MSDataShape;Data Provider=NONE;"
 
strShape = _
"SHAPE APPEND NEW adInteger AS CustID," &amp; _
            " NEW adChar(25) AS FirstName," &amp; _
            " NEW adChar(25) AS LastName," &amp; _
            " NEW adChar(12) AS SSN," &amp; _
            " NEW adChar(50) AS Address," &amp; _
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," &amp; _
                        " NEW adInteger AS CustID," &amp; _
                        " NEW adChar(20) AS BodyColor, " &amp; _
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," &amp; _
                                    " NEW adChar(20) AS Make, " &amp; _
                                    " NEW adChar(20) AS Model," &amp; _
                                    " NEW adChar(4) AS Year) " &amp; _
                        " AS VINS RELATE VIN_NO TO VIN_NO))" &amp; _
            " AS Vehicles RELATE CustID TO CustID) "
 
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1

```

Once the **Recordset** has been fabricated, it can be populated, manipulated, or persisted to a file. 
  

