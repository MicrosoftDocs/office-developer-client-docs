---
title: After Delete Macro Event
TOCTitle: After Delete Macro Event
ms:assetid: ecf9e6d4-345f-9b78-eb36-bd526e5df09b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836323(v=office.15)
ms:contentKeyID: 48548527
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm15155
f1_categories:
- Office.Version=v15
---

# After Delete Macro Event


**Applies to**: Access 2013 | Office 2013

The **After Delete** event occurs after a record is deleted.


> [!NOTE]
> The **After Delete** event is available only in Data Macros.



## Remarks

Use the **After Delete** event to perform any actions that you want to occur when a record is deleted. Common uses for the **After Delete** include enforcing business rules, workflows, updating an aggregate total, and sending notifications.

When the **After Delete** event occurs, the values contained in the deleted record are still available. You may want to use a deleted value to increment or decrement a total, create an audit trail, or compare to an existing value in a *WhereCondition* argument.

You can use the **Updated("*Field Name*")** function to determine whether a field has changed. The following code example shows how to use an If staement to determine determine whether the PaidInFull field has been changed.

```vb 
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

You can use access a value in the deleted record by using the following syntax.

`[Old].[Field Name]`

For example, to access the value of the QuantityInStock field in the deleted record, use the following syntax.

`[Old].[QuantityInStock]`

The values contained in the deleted record are deleted permanently when the **After Delete** event ends.

The following macro commands can be used in the **After Delete** event.

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
<td><p><a href="comment-macro-statement.md">Comment Macro Statement</a></p></td>
</tr>
<tr class="even">
<td><p>Program Flow</p></td>
<td><p><a href="group-macro-statement.md">Group Macro Statement</a></p></td>
</tr>
<tr class="odd">
<td><p>Program Flow</p></td>
<td><p><a href="if-then-else-macro-block.md">If...Then...Else Macro Block</a></p></td>
</tr>
<tr class="even">
<td><p>Data Block</p></td>
<td><p><a href="createrecord-data-block.md">CreateRecord Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Block</p></td>
<td><p><a href="editrecord-data-block.md">EditRecord Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Block</p></td>
<td><p><a href="foreachrecord-data-block.md">ForEachRecord Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Block</p></td>
<td><p><a href="lookuprecord-data-block.md">LookupRecord Data Block</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="cancelrecordchange-macro-action.md">CancelRecordChange Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="clearmacroerror-macro-action.md">ClearMacroError Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="deleterecord-macro-action.md">DeleteRecord Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="exitforeachrecord-macro-action.md">ExitForEachRecord Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="logevent-macro-action.md">LogEvent Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="onerror-macro-action.md">OnError Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="raiseerror-macro-action.md">RaiseError Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="rundatamacro-macro-action.md">RunDataMacro Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="sendemail-macro-action.md">SendEmail Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="setfield-macro-action.md">SetField Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="setlocalvar-macro-action.md">SetLocalVar Macro Action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="stopallmacros-macro-action.md">StopAllMacros Macro Action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="stopmacro-macro-action.md">StopMacro Macro Action</a></p></td>
</tr>
</tbody>
</table>


To create a Data Macro that captures the **After Delete** event, use the following steps.

1.  Open the table for which you want to capture the **After Delete** event.

2.  On the **Table** tab, in the **After Events** group, click **After Delete**.

An empty Data Macro is displayed in the macro designer.

## Example

The following code example uses the **After Delete** event to perform some processing when a record is deleted from the Donations table. When a record is deleted, the amount of the donation is subracted form the DonationsReceived field in the DonationsReceived table and the TotalDonatedField in the Donors table.

**Click here to view a copy of the macro that you can paste into Macro Designer.**

To view this example in the macro designer, use the following steps.

1.  Open the table for which you want to capture the **After Delete** event.

2.  On the **Table** tab, in the **After Events** group, click **After Delete**.

3.  Select the code listed below and then press CTRL+C to copy it to the Clipboard.

4.  Activate the macro designer window and then press CTRL+V.

<!-- end list -->

```xml
    <?xml version="1.0" encoding="UTF-16" standalone="no"?> 
    <DataMacros xmlns="https://schemas.microsoft.com/office/accessservices/2009/04/application"> 
      <DataMacro Event="AfterDelete"> 
        <Statements> 
          <Comment>Initialize a variable and assign the old</Comment> 
          <Action Name="SetLocalVar"> 
            <Argument Name="Name">varAmount</Argument> 
            <Argument Name="Value">[Old].[Amount]</Argument> 
          </Action> 
          <ConditionalBlock> 
            <If> 
              <Condition>Not (IsNull([Old].[CampaignID]))</Condition> 
              <Statements> 
                <ForEachRecord> 
                  <Data> 
                    <Reference>Campaigns</Reference> 
                    <WhereCondition>[ID]=[Old].[CampaignID]</WhereCondition> 
                  </Data> 
                  <Statements> 
                    <EditRecord> 
                      <Data /> 
                      <Statements> 
                        <Action Collapsed="true" Name="SetField"> 
                          <Argument Name="Field">[DonationsReceived]</Argument> 
                          <Argument Name="Value">[DonationsReceived]-[varAmount]</Argument> 
                        </Action> 
                      </Statements> 
                    </EditRecord> 
                  </Statements> 
                </ForEachRecord> 
              </Statements> 
            </If> 
          </ConditionalBlock> 
          <ConditionalBlock> 
            <If> 
              <Condition>Not (IsNull([Old].[DonorID]))</Condition> 
              <Statements> 
                <ForEachRecord> 
                  <Data> 
                    <Reference>Donors</Reference> 
                    <WhereCondition>[ID]=[Old].[DonorID]</WhereCondition> 
                  </Data> 
                  <Statements> 
                    <EditRecord> 
                      <Data /> 
                      <Statements> 
                        <Action Name="SetField"> 
                          <Argument Name="Field">[TotalDonated]</Argument> 
                          <Argument Name="Value">[TotalDonated]-[varAmount]</Argument> 
                        </Action> 
                      </Statements> 
                    </EditRecord> 
                  </Statements> 
                </ForEachRecord> 
              </Statements> 
            </If> 
          </ConditionalBlock> 
        </Statements> 
      </DataMacro> 
    </DataMacros>
```

<br/>

```vb
    SetLocalVar 
                    Name    varAmount 
              Expression   =[Old].[Amount] 
     
    If   Not(IsNull([Old].[CampaignID]]))   Then 
     
         For Each Record In     Campaigns 
            Where Condition     =[ID]=[Old].[CampaignID] 
                      Alias 
            EditRecord 
                      Alias 
                  SetField   ([DonationsReceived], [DonationsReceived] - [varAmount]) 
            End EditRecord 
     
    End If 
     
    If   Not(IsNull([Old].[DonorID]]))   Then 
     
         For Each Record In    Donors 
            Where Condition     =[ID]=[Old].[DonorID] 
                      Alias 
            EditRecord 
                      Alias 
     
              SetField 
                             Name   [TotalDonated] 
                            Value   =[TotalDonated]-[varAmount] 
            End EditRecord 
    End If
```
