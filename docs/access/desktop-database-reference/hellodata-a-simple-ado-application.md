---
title: 'HelloData: A simple ADO application'
TOCTitle: 'HelloData: A simple ADO application'
ms:assetid: c271abeb-8865-81f9-db8e-47d3db87ad30
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249950(v=office.15)
ms:contentKeyID: 48547554
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# HelloData: A simple ADO application

**Applies to**: Access 2013, Office 2013

To lay the groundwork for an exploration of the ADO library, consider a simple ADO application called "HelloData." HelloData steps through each of the four major ADO operations (getting, examining, editing, and updating data). In order to focus on the fundamentals of ADO and prevent code clutter, minimal error handling is done in the example.

The application queries the Northwind sample database that is included with Microsoft SQL Server 2000.

**To run HelloData**

1.  Create a new Standard Executable Visual Basic Project that references the ADO 2.5 library.

2.  Create four command buttons at the top of the form, setting the **Name** and **Caption** properties to the values shown in the table below.

3.  Below the buttons, add a **Microsoft DataGrid Control** (Msdatgrd.ocx). The Msdatgrd.ocx file comes with Visual Basic and is located in your \\windows\\system32 or \\winnt\\system32 directory. To add the DataGrid control to your Visual Basic toolbox pane, select **Components...** from the **Project** menu. Then check the box next to "Microsoft DataGrid Control 6.0 (SP3) (OLEDB)" and click **OK**. To add the control to the project, drag the DataGrid control from the Toolbox to the Visual Basic form.

4.  Create a **TextBox** on the form below the grid and set its properties as shown in the table. The form should look similar to the following figure when you are finished.

5.  Finally, copy the code listed in [HelloData Code](hellodata-code.md) and paste it into the code editor window of the form. Press **F5** to run the code.

> [!NOTE]
> In the following example, and throughout the guide, the user id "MyId" with a password of "123aBc" is used to authenticate against the server. You should substitute these values with valid logon credentials for your server. Also, substitute the "MyServer" value with the name of your server.

For a detailed description of the code, see [HelloData Details](hellodata-details.md).

<table>
<colgroup>
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Control Type</p></th>
<th><p>Property</p></th>
<th><p>Value</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Form</p></td>
<td><p>Name</p></td>
<td><p>Form1</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Height</p></td>
<td><p>6500</p></td>
</tr>
<tr class="odd">
<td><p><br />
</p></td>
<td><p>Width</p></td>
<td><p>6500</p></td>
</tr>
<tr class="even">
<td><p>MS DataGrid</p></td>
<td><p>Name</p></td>
<td><p>grdDisplay1</p></td>
</tr>
<tr class="odd">
<td><p>TextBox</p></td>
<td><p>Name</p></td>
<td><p>txtDisplay1</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Multiline</p></td>
<td><p>true</p></td>
</tr>
<tr class="odd">
<td><p>Command Button</p></td>
<td><p>Name</p></td>
<td><p>cmdGetData</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Caption</p></td>
<td><p>Get Data</p></td>
</tr>
<tr class="odd">
<td><p>Command Button</p></td>
<td><p>Name</p></td>
<td><p>cmdExamineData</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Caption</p></td>
<td><p>Examine Data</p></td>
</tr>
<tr class="odd">
<td><p>Command Button</p></td>
<td><p>Name</p></td>
<td><p>cmdEditData</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Caption</p></td>
<td><p>Edit Data</p></td>
</tr>
<tr class="odd">
<td><p>Command Button</p></td>
<td><p>Name</p></td>
<td><p>cmdUpdateData</p></td>
</tr>
<tr class="even">
<td><p><br />
</p></td>
<td><p>Caption</p></td>
<td><p>Update Data</p></td>
</tr>
</tbody>
</table>



