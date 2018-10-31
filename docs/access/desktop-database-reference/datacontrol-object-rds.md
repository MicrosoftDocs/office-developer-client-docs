---
title: DataControl Object (RDS)
TOCTitle: DataControl Object (RDS)
ms:assetid: ac430669-7628-696c-c036-b5d35405d788
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249801(v=office.15)
ms:contentKeyID: 48547001
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DataControl Object (RDS)

**Applies to**: Access 2013, Office 2013

Binds a data query [Recordset](recordset-object-ado.md) to one or more controls (for example, a text box, grid control, or combo box) to display the **Recordset** data on a webpage.

## Syntax

```vb
    <OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"
       <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=usr;PWD=pw;">
       <PARAM NAME="Server" VALUE="https://awebsrvr">
       <PARAM NAME="SQL" VALUE="QueryText">
    </OBJECT>
```

## Remarks

The class ID for the **RDS.DataControl** object is BD96C556-65A3-11D0-983A-00C04FC29E33.

> [!NOTE]
> If you get an error that an [RDS.DataSpace](dataspace-object-rds.md) or **RDS.DataControl** object doesn't load, make sure you are using the correct class ID. The class IDs for these objects have changed from version 1.0 and 1.1.

For a basic scenario, you need to set only the **SQL**, **Connect**, and **Server** properties of the **RDS.DataControl** object, which will automatically call the default business object, [RDSServer.DataFactory](datafactory-object-rdsserver.md).

All the properties in the **RDS.DataControl** are optional because custom business objects can replace their functionality.

> [!NOTE]
> If you query for multiple results, only the first [Recordset](recordset-object-ado.md) is returned. If multiple result sets are needed, assign each to its own **DataControl**. 
> 
> An example of a query for multiple results could be the following:
> `"Select * from Authors, Select * from Topics"`.

Adding "DFMode=20;" to your connection string when using the **RDS.DataControl** object can improve your server's performance when updating data. With this setting, the **RDSServer.DataFactory** object on the server uses a less resource-intensive mode. However, the following features are not available in this configuration:

  - Using parameterized queries.

  - Getting parameter or column information before calling the **Execute** method.

  - Setting **Transact Updates** to **True**.

  - Getting row status.

  - Calling the [Resync](resync-method-ado.md) method.

  - Refreshing (explicitly or automatically) via the [Update Resync](update-resync-property-dynamic-ado.md) property.

  - Setting **Command** or [Recordset](recordset-sourcerecordset-properties-rds.md) properties.

  - Using **adCmdTableDirect**.

The **RDS.DataControl** object runs in asynchronous mode by default. If you require synchronous execution for your application, set the [ExecuteOptions](executeoptions-property-rds.md) parameter equal to **adcExecSync** and the [FetchOptions](fetchoptions-property-rds.md) parameter equal to **adcFetchUpFront**, as shown in the following example.

```vb
    <OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" 
        ID="DataControl"
       <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=usr;PWD=pw;">
       <PARAM NAME="Server" VALUE="https://awebsrvr">
       <PARAM NAME="SQL" VALUE="QueryText">
       <PARAM NAME="ExecuteOptions" VALUE="1">
       <PARAM NAME="FetchOptions" VALUE="1">
    </OBJECT>
```

Use one **RDS.DataControl** object to link the results of a single query to one or more visual controls. For example, suppose you code a query requesting customer data such as Name, Residence, Place of Birth, Age, and Priority Customer Status. You can use a single **RDS.DataControl** object to display a customer's Name, Age, and Region in three separate text boxes; Priority Customer Status in a check box; and all the data in a grid control.

Use different **RDS.DataControl** objects to link the results of multiple queries to different visual controls. For example, suppose you use one query to obtain information about a customer, and a second query to obtain information about merchandise that the customer has purchased. You want to display the results of the first query in three text boxes and one check box, and the results of the second query in a grid control. If you use the default business object (**RDSServer.DataFactory**), you need to do the following:

  - Add two **RDS.DataControl** objects to your webpage.

  - Write two queries, one for each **SQL** property of the two **RDS.DataControl** objects. One **RDS.DataControl** object will contain an SQL query requesting customer information; the second will contain a query requesting a list of merchandise the customer has purchased.

  - In each of the bound controls' OBJECT tags, specify the DATAFLD value to set the values for the data you want to display in each visual control.

There is no count restriction on the number of **RDS.DataControl** objects that you can embed via OBJECT tags on a single webpage.

When you define the **RDS.DataControl** object on a webpage, use nonzero **Height** and **Width** values such as 1 (to avoid the inclusion of extra space).

Remote Data Service client components are already included as part of Internet Explorer 4.0; therefore, you don't need to include a CODEBASE parameter in your **RDS.DataControl** object tag.

With Internet Explorer 4.0 or later, you can bind to data by using HTML controls and ActiveX® controls only if they are marked as apartment model controls.

**Microsoft Visual Basic Users** The **RDS.DataControl** is used only in web-based applications. A Visual Basic client application has no need for it.

