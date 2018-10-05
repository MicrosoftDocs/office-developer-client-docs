---
title: After Insert Macro Event
TOCTitle: After Insert Macro Event
ms:assetid: 78013896-ee07-6979-96f7-fa0f3490419e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196099(v=office.15)
ms:contentKeyID: 48545742
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm3180
f1_categories:
- Office.Version=v15
---

# After Insert Macro Event


**Applies to**: Access 2013 | Office 2013

The **After Insert** event occurs after a record is added.


> [!NOTE]
> The **After Insert** event is available only in Data Macros.



## Remarks

Use the **After Insert** event to perform any actions that you want to occur when a record is added to a table. Common uses for the **After Insert** include enforcing business rules, workflows, updating an aggregate total, and sending notifications.

You can use the **Updated("*Field Name*")** function to determine whether a field has changed. The following code example shows how to use an **If** statement to determine determine whether the PaidInFull field has been changed.

```vb 
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

The following table lists macro commands that can be used in the**After Insert** event.

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


To create a Data macro that captures the **After Insert** event, use the following steps.

1.  Open the table for which you want to capture the **After Insert** event.

2.  On the **Table** tab, in the **After Events** group, click **After Insert**.

An empty data macro is displayed in the macro designer.

## Example

The following code example uses the **After Insert** event to perform some processing when a record is added to the Donations table. When a record is added, the amount of the donation is added to the DonationsReceived field in the Campaigns table and the TotalDonatedField in the Donors table.

**Click here to view a copy of the macro that you can paste into Macro Designer.**

To view this example in the macro designer, use the following steps:

1.  Open the table for which you want to capture the **After Insert** event.

2.  On the **Table** tab, in the **After Events** group, click **After Insert**.

3.  Select the code in the following code example and then press CTRL+C to copy it to the Clipboard.

4.  Activate the macro designer window and then press CTRL+V.

<!-- end list -->

```xml
    <DataMacros> 
      <DataMacro Event="AfterInsert"> 
        <Statements> 
          <Comment>This data macro increments the DonationsReceived field in Campaigns and theAmountCollected field in Pledges </Comment> 
          <Action Name="SetLocalVar"> 
            <Argument Name="Name">varAmount</Argument> 
            <Argument Name="Value">[Amount]</Argument> 
          </Action> 
          <ConditionalBlock> 
            <If> 
              <Condition>Not (IsNull([CampaignID]))</Condition> 
              <Statements> 
                <ForEachRecord> 
                  <Data> 
                    <Reference>Campaigns</Reference> 
                    <WhereCondition>[ID]=[Donations].[CampaignID]</WhereCondition> 
                  </Data> 
                  <Statements> 
                    <EditRecord> 
                      <Data /> 
                      <Statements> 
                        <Action Name="SetField"> 
                          <Argument Name="Field">[DonationsReceived]</Argument> 
                          <Argument Name="Value">[DonationsReceived]+[varAmount]</Argument> 
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
              <Condition>Not (IsNull([DonorID]))</Condition> 
              <Statements> 
                <ForEachRecord> 
                  <Data> 
                    <Reference>Donors</Reference> 
                    <WhereCondition>[ID]=[Donations].[DonorID]</WhereCondition> 
                  </Data> 
                  <Statements> 
                    <EditRecord> 
                      <Data /> 
                      <Statements> 
                        <Action Name="SetField"> 
                          <Argument Name="Field">[TotalDonated]</Argument> 
                          <Argument Name="Value">[TotalDonated]+[varAmount]</Argument> 
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
                  Name   varAmount 
            Expression   =[Amount] 
     
    If   Not (IsNull([CampaignID]))   Then 
     
         For Each Record In   Campaigns 
            Where Condition   =[ID]=[Donations].[CampaignID] 
                      Alias 
     
                 EditRecord 
                              Alias 
                     SetField 
                                 Name   [DonationsReceived] 
                                Value   =[DonationsReceived]+[varAmount] 
                End EditRecord 
    End If 
     
    If   Not (IsNull([DonorID]))   Then 
     
         For Each Record In  Donors 
            WhereCondition   =[ID]=[Donations].[DonorID] 
                     Alias 
     
                 EditRecord 
                              Alias 
                     SetField 
                                 Name   [TotalDonated] 
                                Value   =[TotalDonated]+[varAmount] 
                 End EditRecord 
    End If
```
