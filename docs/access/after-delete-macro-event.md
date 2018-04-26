---
title: "After Delete Macro Event"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm15155
  
localization_priority: Normal
ms.assetid: ecf9e6d4-345f-9b78-eb36-bd526e5df09b
description: "The After Delete event occurs after a record is deleted."
---

# After Delete Macro Event

The **After Delete** event occurs after a record is deleted. 
  
> [!NOTE]
> The **After Delete** event is available only in Data Macros. 
  
## Remarks

Use the **After Delete** event to perform any actions that you want to occur when a record is deleted. Common uses for the **After Delete** include enforcing business rules, workflows, updating an aggregate total, and sending notifications. 
  
When the **After Delete** event occurs, the values contained in the deleted record are still available. You may want to use a deleted value to increment or decrement a total, create an audit trail, or compare to an existing value in a  *WhereCondition*  argument. 
  
You can use the **Updated(" *Field Name*  ") ** function to determine whether a field has changed. The following code example shows how to use an If staement to determine determine whether the PaidInFull field has been changed. 
  
```
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

You can use access a value in the deleted record by using the following syntax.
  
```
[Old].[Field Name ]
```

For example, to access the value of the QuantityInStock field in the deleted record, use the following syntax.
  
```
[Old].[QuantityInStock]
```

The values contained in the deleted record are deleted permanently when the **After Delete** event ends. 
  
The following macro commands can be used in the ** After Delete ** event. 
  
|**Command Type**|**Command**|
|:-----|:-----|
|Program Flow  <br/> |[Comment Macro Statement](comment-macro-statement.md) <br/> |
|Program Flow  <br/> |[Group Macro Statement](group-macro-statement.md) <br/> |
|Program Flow  <br/> |[If...Then...Else Macro Block](ifthenelse-macro-block.md) <br/> |
|Data Block  <br/> |[CreateRecord Macro Action](createrecord-data-block.md) <br/> |
|Data Block  <br/> |[EditRecord Macro Action](editrecord-data-block.md) <br/> |
|Data Block  <br/> |[ForEachRecord Macro Action](foreachrecord-data-block.md) <br/> |
|Data Block  <br/> |[LookupRecord Data Block](lookuprecord-data-block.md) <br/> |
|Data Action  <br/> |[CancelRecordChange Macro Action](cancelrecordchange-macro-action.md) <br/> |
|Data Action  <br/> |[ClearMacroError Macro Action](clearmacroerror-macro-action.md) <br/> |
|Data Action  <br/> |[DeleteRecord Macro Action](deleterecord-macro-action.md) <br/> |
|Data Action  <br/> |[ExitForEachRecord Macro Action](exitforeachrecord-macro-action.md) <br/> |
|Data Action  <br/> |[LogEvent Macro Action](logevent-macro-action.md) <br/> |
|Data Action  <br/> |[OnError Macro Action](onerror-macro-action.md) <br/> |
|Data Action  <br/> |[RaiseError Macro Action](raiseerror-macro-action.md) <br/> |
|Data Action  <br/> |[RunDataMacro Macro Action](rundatamacro-macro-action.md) <br/> |
|Data Action  <br/> |[SendEmail Macro Action](sendemail-macro-action.md) <br/> |
|Data Action  <br/> |[SetField Macro Action](setfield-macro-action.md) <br/> |
|Data Action  <br/> |[SetLocalVar Macro Action](setlocalvar-macro-action.md) <br/> |
|Data Action  <br/> |[StopAllMacros Macro Action](stopallmacros-macro-action.md) <br/> |
|Data Action  <br/> |[StopMacro Macro Action](stopmacro-macro-action.md) <br/> |
   
To create a Data Macro that captures the **After Delete** event, use the following steps. 
  
1. Open the table for which you want to capture the **After Delete** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Delete**.
    
An empty Data Macro is displayed in the macro designer.
  
## Example

The following code example uses the **After Delete** event to perform some processing when a record is deleted from the Donations table. When a record is deleted, the amount of the donation is subracted form the DonationsReceived field in the DonationsReceived table and the TotalDonatedField in the Donors table. 
  
 * **Click here to view a copy of the macro that you can paste into Macro Designer.*** 
  
To view this example in the macro designer, use the following steps.
  
1. Open the table for which you want to capture the **After Delete** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Delete**.
    
3. Select the code listed below and then press CTRL+C to copy it to the Clipboard.
    
4. Activate the macro designer window and then press CTRL+V.
    
```
<?xml version="1.0" encoding="UTF-16" standalone="no"?> 
<DataMacros xmlns="http://schemas.microsoft.com/office/accessservices/2009/04/application"> 
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


