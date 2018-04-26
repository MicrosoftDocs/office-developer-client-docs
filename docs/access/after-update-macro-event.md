---
title: "After Update Macro Event"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm85126
  
localization_priority: Normal
ms.assetid: 5213793b-8301-0f18-3a12-4e3764c879ac
description: "The After Update event occurs after a record is changed."
---

# After Update Macro Event

The **After Update** event occurs after a record is changed. 
  
> [!NOTE]
> The **After Update** event is available only in Data Macros. 
  
## Remarks

Use the **After Update** event to perform any actions that you want to occur when a record is changed. Common uses for the **After Insert** include enforcing business rules, updating an aggregate total, and sending notifications. 
  
You can use the **Updated(" *Field Name*  ") ** function to determine whether a field has changed. The following code example shows how to use an **If** statement to determine determine whether the PaidInFull field has been changed. 
  
```
 
If  Updated("PaidInFull")   Then 
 
    /* Perform actions based on changes to the field.   */ 
 
End If 
 
```

You can use access a the previous value in a field by using the following syntax.
  
```
[Old].[Field Name ]
```

For example, to access the previous value of the QuantityInStock field, use the following syntax.
  
```
[Old].[QuantityInStock]
```

The previous values are deleted permanently when the **After Update** event ends. 
  
The following table lists macro commands can be used in the **After Update** event. 
  
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
   
To create a Data macro that captures the **After Update** event, use the folloiwng steps: 
  
1. Open the table for which you want to capture the **After Update** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Update**.
    
An empty data macro is displayed in the macro designer.
  
## Example

The following code example uses the **After Update** event to run a named data macro that adds a record to the Comment table each time the status of an issue is updated. 
  
 * **Click here to view a copy of the macro that you can paste into Macro Designer.*** 
  
To view this example in the macro designer, use the following steps:
  
1. Open the table for which you want to capture the **After Update** event. 
    
2. On the **Table** tab, in the **After Events** group, click **After Update**.
    
3. Select the code in the following code example and then press CTRL+C to copy it to the Clipboard.
    
4. Activate the macro designer window and then press CTRL+V.
    
```
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
                <Parameter Name="prmComment" Value="&amp;quot;-- Status changed to &amp;quot; &amp;amp; [Status]" /> 
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
                <Parameter Name="prmComment" Value="&amp;quot;-- Issue resolved as &amp;quot; &amp;amp; [Resolution]" /> 
              </Parameters> 
            </Action> 
          </Statements> 
        </If> 
      </ConditionalBlock> 
    </Statements> 
  </DataMacro> 
</DataMacros>

```

```
 
If  Updated("Status")   Then 
     RunDataMacro 
        Macro Name   Comments.AddComment 
     Parameters 
       prmRelatedID   = [ID] 
         prmComment   ="--Status Changes to "&amp;[Status] 
          prmUserID   =[ChangedByUserID] 
End If 
 
If   Updated("Resolution")   Then 
     RunDataMacro 
        Macro Name   Comments.AddComment 
     Parameters 
       prmRelatedID   = [ID] 
          prmUserID   =[ChangedByUserID] 
         prmComment   ="--Issue Resolved as "&amp;[Status] 
End If 

```


