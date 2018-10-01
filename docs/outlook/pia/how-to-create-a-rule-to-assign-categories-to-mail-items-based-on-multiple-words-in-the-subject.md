---
title: 'Create a Rule to Assign Categories to Mail Items Based on Multiple Words in the Subject'
TOCTitle: 'Create a Rule to Assign Categories to Mail Items Based on Multiple Words in the Subject'
ms:assetid: 6e1fa40c-edf3-407c-9e90-99f634fa8e24
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424472(v=office.15)
ms:contentKeyID: 55119918
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Create a Rule to Assign Categories to Mail Items Based on Multiple Words in the Subject

This example shows how to set up a rule that assigns categories to mail items based on multiple words in the subject.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>The following code example is an excerpt from <em>Programming Applications for Microsoft Office Outlook 2007</em>, from <a href="http://www.microsoft.com/learning/books/default.mspx">Microsoft Press</a> (ISBN 9780735622494, copyright Microsoft Press 2007, all rights reserved).</p>
<p><a href="http://www.amazon.com/gp/product/0735622493?ie=utf8%26tag=msmsdn-20%26linkcode=as2%26camp=1789%26creative=9325%26creativeasin=0735622493">Buy this book</a></p>
<p><a href="https://msdn.microsoft.com/en-us/library/cc513844(v=office.15)">Sample chapters</a></p></td>
</tr>
</tbody>
</table>


In Outlook, items can be categorized for easier organization and display. The Outlook object model provides the [Category](https://msdn.microsoft.com/en-us/library/bb623480\(v=office.15\)) object and the [Categories](https://msdn.microsoft.com/en-us/library/bb623535\(v=office.15\)) collection to represent categories. For more information about the Category object and the Categories collection for an Outlook item, see [Enumerate and Add Categories](how-to-enumerate-and-add-categories.md).

A rule, represented by a [Rule](https://msdn.microsoft.com/en-us/library/bb647152\(v=office.15\)) object, can be assigned with multiple conditions. You can get or set an array that represents conditions to be evaluated or actions to be completed. For example, the [Text](https://msdn.microsoft.com/en-us/library/bb611271\(v=office.15\)) property of the [TextRuleCondition](https://msdn.microsoft.com/en-us/library/bb644796\(v=office.15\)) object returns or sets an array of string elements that represents the text to be evaluated by the rule condition. You must assign an array with one string or multiple strings for evaluation. To evaluate multiple text strings that are assigned in an array, use the logical OR operation. The properties that you can use to get or set an array are as follows: [Address](https://msdn.microsoft.com/en-us/library/bb647045\(v=office.15\)), [Categories](https://msdn.microsoft.com/en-us/library/bb611021\(v=office.15\)), [Categories](https://msdn.microsoft.com/en-us/library/bb612345\(v=office.15\)), [FormName](https://msdn.microsoft.com/en-us/library/bb647042\(v=office.15\)), and TextRuleCondition.Text. For more information about rules, see [Create a Rule to File Mail Items from a Manager and Flag Them for Follow-Up](how-to-create-a-rule-to-file-mail-items-from-a-manager-and-flag-them-for-follow-up.md).

In the following example, CreateTextAndCategoryRule uses the CategoryExists method to check the user’s mail items for any categories by the name “Office” or “Outlook” in the Categories collection. If no categories are found, they are added. The example then creates an array of strings that include “Office, “Outlook”, and “2007”. This array will represent the conditions to be evaluated. CreateTextAndCategoryRule then creates a rule that assigns categories by examining the subject for any of the conditions in the array by using the Text property of the TextRuleCondition object and the [BodyOrSubject](https://msdn.microsoft.com/en-us/library/bb612744\(v=office.15\)) property of the [RuleConditions](https://msdn.microsoft.com/en-us/library/bb610965\(v=office.15\)) collection. If the condition is satisfied, the categories of Office and Outlook are assigned to the item by using the [AssignToCategory](https://msdn.microsoft.com/en-us/library/bb623146\(v=office.15\)) method of the [RuleActions](https://msdn.microsoft.com/en-us/library/bb610113\(v=office.15\)) object.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void CreateTextAndCategoryRule()
{
    if (!CategoryExists("Office"))
    {
        Application.Session.Categories.Add(
            "Office", Type.Missing, Type.Missing);
    }
    if (!CategoryExists("Outlook"))
    {
        Application.Session.Categories.Add(
            "Outlook", Type.Missing, Type.Missing);
    }
    Outlook.Rules rules =
        Application.Session.DefaultStore.GetRules();
    Outlook.Rule textRule =
        rules.Create("Demo Text and Category Rule",
        Outlook.OlRuleType.olRuleReceive);
    Object[] textCondition = 
        { "Office", "Outlook", "2007" };
    Object[] categoryAction = 
        { "Office", "Outlook" };
    textRule.Conditions.BodyOrSubject.Text =
        textCondition;
    textRule.Conditions.BodyOrSubject.Enabled = true;
    textRule.Actions.AssignToCategory.Categories =
        categoryAction;
    textRule.Actions.AssignToCategory.Enabled = true;
    rules.Save(true);
}

// Determines if categoryName exists in Categories collection
private bool CategoryExists(string categoryName)
{
    try
    {
        Outlook.Category category =
            Application.Session.Categories[categoryName];
        if (category != null)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
    catch { return false; }
}
```

## See also



[Rules](rules.md)

