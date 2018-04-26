---
title: "After Insert Macro Event"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm3180
  
localization_priority: Normal
ms.assetid: 78013896-ee07-6979-96f7-fa0f3490419e
description: "The After Insert event occurs after a record is added."
---

# After Insert Macro Event

The **After Insert** event occurs after a record is added. 
  
> [!NOTE]
> The **After Insert** event is available only in Data Macros. 
  
## Remarks

Use the **After Insert** event to perform any actions that you want to occur when a record is added to a table. Common uses for the **After Insert** include enforcing business rules, workflows, updating an aggregate total, and sending notifications. 
  
You can use the **Updated(" *Field Name*  ") ** function to determine whether a field has changed. The following code example shows how to use an **If** statement to determine determine whether the PaidInFull field has been changed. 
  
```
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

The following table lists macro commands that can be used in the **After Insert** event. 
  
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
   
To create a Data macro that captures the **After Insert** event, use the following steps. 
  
1. Open the table for which you want to capture the **After Insert** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Insert**.
    
An empty data macro is displayed in the macro designer.
  
## Example

The following code example uses the **After Insert** event to perform some processing when a record is added to the Donations table. When a record is added, the amount of the donation is added to the DonationsReceived field in the Campaigns table and the TotalDonatedField in the Donors table. 
  
 * **Click here to view a copy of the macro that you can paste into Macro Designer.*** 
  
To view this example in the macro designer, use the following steps:
  
1. Open the table for which you want to capture the **After Insert** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Insert**.
    
3. Select the code in the following code example and then press CTRL+C to copy it to the Clipboard.
    
4. Activate the macro designer window and then press CTRL+V.
    
```
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


