---
title: After Update macro event
TOCTitle: After Update macro event
ms:assetid: 5213793b-8301-0f18-3a12-4e3764c879ac
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193905(v=office.15)
ms:contentKeyID: 48544838
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm85126
f1_categories:
- Office.Version=v15
ms.localizationpriority: high
---

# After Update macro event

**Applies to**: Access 2013, Office 2013

The **After Update** event occurs after a record is changed.

> [!NOTE]
> The **After Update** event is available only in Data Macros.

## Remarks

Use the **After Update** event to perform any actions that you want to occur when a record is changed. Common uses for the **After Insert** include enforcing business rules, updating an aggregate total, and sending notifications.

You can use the **Updated("*Field Name*")** function to determine whether a field has changed. The following code example shows how to use an **If** statement to determine determine whether the PaidInFull field has been changed.

```vb 
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

You can use access a the previous value in a field by using the following syntax.

`[Old].[Field Name]`

For example, to access the previous value of the QuantityInStock field, use the following syntax.

`[Old].[QuantityInStock]`

The previous values are deleted permanently when the **After Update** event ends.

The following table lists macro commands can be used in the**After Update** event.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Command Type</p></th>
<th><p>Command</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Program Flow</p></td>
<td><p><a href="comment-macro-statement.md">Comment macro statement</a></p></td>
</tr>
<tr class="even">
<td><p>Program Flow</p></td>
<td><p><a href="group-macro-statement.md">Group macro statement</a></p></td>
</tr>
<tr class="odd">
<td><p>Program Flow</p></td>
<td><p><a href="if-then-else-macro-block.md">If...Then...Else macro block</a></p></td>
</tr>
<tr class="even">
<td><p>Data Block</p></td>
<td><p><a href="createrecord-data-block.md">CreateRecord macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Block</p></td>
<td><p><a href="editrecord-data-block.md">EditRecord macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Block</p></td>
<td><p><a href="foreachrecord-data-block.md">ForEachRecord macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Block</p></td>
<td><p><a href="lookuprecord-data-block.md">LookupRecord data block</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="cancelrecordchange-macro-action.md">CancelRecordChange macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="clearmacroerror-macro-action.md">ClearMacroError macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="deleterecord-macro-action.md">DeleteRecord macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="exitforeachrecord-macro-action.md">ExitForEachRecord macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="logevent-macro-action.md">LogEvent macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="onerror-macro-action.md">OnError macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="raiseerror-macro-action.md">RaiseError macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="rundatamacro-macro-action.md">RunDataMacro macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="sendemail-macro-action.md">SendEmail macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="setfield-macro-action.md">SetField macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="setlocalvar-macro-action.md">SetLocalVar macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="stopallmacros-macro-action.md">StopAllMacros macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="stopmacro-macro-action.md">StopMacro macro action</a></p></td>
</tr>
</tbody>
</table>


To create a Data macro that captures the **After Update** event, use the folloiwng steps:

1.  Open the table for which you want to capture the **After Update** event.

2.  On the **Table** tab, in the **After Events** group, click **After Update**.

An empty data macro is displayed in the macro designer.

## Example

The following code example uses the **After Update** event to run a named data macro that adds a record to the Comment table each time the status of an issue is updated.

**Click here to view a copy of the macro that you can paste into Macro Designer.**

To view this example in the macro designer, use the following steps:

1.  Open the table for which you want to capture the **After Update** event.

2.  On the **Table** tab, in the **After Events** group, click **After Update**.

3.  Select the code in the following code example and then press CTRL+C to copy it to the Clipboard.

4.  Activate the macro designer window and then press CTRL+V.

<!-- end list -->

```xml
    <DataMacros xmlns="http://schemas.microsoft.com/office/accessservices/2009/04/application"> 
      <DataMacro Event="AfterUpdate"> 
        <Statements> 
          <ConditionalBlock> 
            <If> 
              <Condition>Updated("Status")</Condition> 
              <Statements> 
                <Action Name="RunDataMacro"> 
                  <Argument Name="MacroName">Comments.AddComment</Argument> 
                  <Parameters> 
                    <Parameter Name="prmRelatedID" Value="[ID]" /> 
                    <Parameter Name="prmComment" Value="&quot;-- Status changed to &quot; &amp; [Status]" /> 
                    <Parameter Name="prmUserID" Value="[UserID]" /> 
                  </Parameters> 
                </Action> 
              </Statements> 
            </If> 
          </ConditionalBlock> 
          <ConditionalBlock> 
            <If> 
              <Condition>Updated("Resolution")</Condition> 
              <Statements> 
                <Action Name="RunDataMacro"> 
                  <Argument Name="MacroName">Comments.AddComment</Argument> 
                  <Parameters> 
                    <Parameter Name="prmRelatedID" Value="[ID]" /> 
                    <Parameter Name="prmUserID" Value="[UserID]" /> 
                    <Parameter Name="prmComment" Value="&quot;-- Issue resolved as &quot; &amp; [Resolution]" /> 
                  </Parameters> 
                </Action> 
              </Statements> 
            </If> 
          </ConditionalBlock> 
        </Statements> 
      </DataMacro> 
    </DataMacros>
``` 


```vb
If  Updated("Status")   Then 
     RunDataMacro 
        Macro Name   Comments.AddComment 
     Parameters 
       prmRelatedID   = [ID] 
         prmComment   ="--Status Changes to "&[Status] 
          prmUserID   =[ChangedByUserID] 
End If 
 
If   Updated("Resolution")   Then 
     RunDataMacro 
        Macro Name   Comments.AddComment 
     Parameters 
       prmRelatedID   = [ID] 
          prmUserID   =[ChangedByUserID] 
         prmComment   ="--Issue Resolved as "&[Status] 
End If 
```

