---
title: 'Create a Rule to File Mail Items from a Manager and Flag Them for Follow-Up'
TOCTitle: 'Create a Rule to File Mail Items from a Manager and Flag Them for Follow-Up'
ms:assetid: c50578c2-15de-4d5f-87d9-d6162034f083
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424477(v=office.15)
ms:contentKeyID: 55119880
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Create a Rule to File Mail Items from a Manager and Flag Them for Follow-Up

This example shows how to set up a rule to file mail items from the user’s manager and flag them for follow up.

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


Outlook rules can operate either server-side or client-side, depending on the type of account and rule. There are many ways you can implement rules to enforce your own organizational schemes when you organize items in your mailbox. For example, you can create a subfolder hierarchy that organizes unread mail and read mail by subject area. Or, you can create a subfolder hierarchy that corresponds to the sender of the message. You can also categorize your mail and then use search folders to aggregate the mail by category.

The Rules object model, which includes a [Rule](https://msdn.microsoft.com/en-us/library/bb647152\(v=office.15\)) object that represents a rule in Outlook, allows you to create rules programmatically to enforce a certain organizational scheme, create a specific rule that is unique to your solution, or ensure that certain rules are deployed to a group of users. By using the Rules object model, you can programmatically add, edit, and delete rules. By using the [Rules](https://msdn.microsoft.com/en-us/library/bb622788\(v=office.15\)) collection and the Rule object, you can also access, add, and delete rules defined for a session. A Rule object has a [RuleType](https://msdn.microsoft.com/en-us/library/bb645613\(v=office.15\)) property that indicates whether the rule is a send or receive rule. When a rule is created, the RuleType property is specified, and cannot be changed without deleting and re-creating the rule with a different RuleType property. The [RuleAction](https://msdn.microsoft.com/en-us/library/bb644297\(v=office.15\)) and [RuleCondition](https://msdn.microsoft.com/en-us/library/bb612469\(v=office.15\)) objects, their collection objects, and derived action and condition objects are also used to further support editing rule actions and rule conditions.

The Rules object model does not support all rules that you can create by using the Rules and Alert Wizard in the Outlook user interface, but it supports the most commonly used rule actions and conditions. Any rules created by using the Rules and Alerts Wizard that are applied to messages, which include mail items, meeting requests, task requests, documents, delivery receipts, read receipts, voting responses, and out-of-office notices, can also be created programmatically.

A rule can execute on the Exchange server or on the Outlook client, provided that the current user’s mailbox is hosted on an Exchange server. The [IsLocalRule](https://msdn.microsoft.com/en-us/library/bb647386\(v=office.15\)) property of the Rule object returns true to indicate that the rule executes on a client, and Outlook must be running for the rule to execute. If the rule executes on the server, Outlook does not have to be running for the rule conditions to be evaluated and the rule actions to be completed.


> [!NOTE]
> <P>There is no separate collection that represents rule exception conditions. Use the <A href="https://msdn.microsoft.com/en-us/library/bb609880(v=office.15)">Exceptions</A> property of the Rule object to get a <A href="https://msdn.microsoft.com/en-us/library/bb610965(v=office.15)">RuleConditions</A> collection that represents rule exception conditions.</P>



To create rules through the Outlook object model, follow these steps:

1.  Get the Rules collection from the [DefaultStore](https://msdn.microsoft.com/en-us/library/bb623164\(v=office.15\)) property of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object by calling the [GetRules()](https://msdn.microsoft.com/en-us/library/bb609979\(v=office.15\)) method on the default [Store](https://msdn.microsoft.com/en-us/library/bb609139\(v=office.15\)) object. Use a try…catch block to account for the user being offline or disconnected from the Exchange server. This prevents Outlook from raising an error.

2.  Call the [Create(String, OlRuleType)](https://msdn.microsoft.com/en-us/library/bb643857\(v=office.15\)) method on the Rules object to create an instance variable or a Rule object, specifying a Name and a [OlRuleType](https://msdn.microsoft.com/en-us/library/bb645776\(v=office.15\)) parameter.

3.  Use the [RuleActions](https://msdn.microsoft.com/en-us/library/bb610113\(v=office.15\)) and [RuleConditions](https://msdn.microsoft.com/en-us/library/bb610965\(v=office.15\)) collections to enable actions, conditions, and exceptions on the Rule object. Note that any condition enabled in the RuleConditions collection, returned by the [Exceptions](https://msdn.microsoft.com/en-us/library/bb609880\(v=office.15\)) property, is treated as a rule exception condition, and additional built-in custom actions or conditions cannot be added to the collection.

4.  Set the [Enabled](https://msdn.microsoft.com/en-us/library/bb609147\(v=office.15\)) property to true for any given rule action, condition, or exception to be operational. Some actions or conditions, such as the [Folder](https://msdn.microsoft.com/en-us/library/bb646755\(v=office.15\)) property, require that you set additional properties on the action or condition to save the Rule object without an error.

5.  Finally, call the [Save(Object)](https://msdn.microsoft.com/en-us/library/bb610738\(v=office.15\)) method on the Rules collection to save the created or modified rules. Enclose the Save method in a try…catch block to handle exceptions.

In the following code example, CreateManagerRule implements the steps previously described. CreateManagerRule first verifies whether the [CurrentUser](https://msdn.microsoft.com/en-us/library/bb622574\(v=office.15\)) property represents an [ExchangeUser](https://msdn.microsoft.com/en-us/library/bb609574\(v=office.15\)) object, indicating that the current user is an Exchange user. If the current user is an Exchange user, CreateManagerRule gets the current user’s manager by calling the [GetExchangeUserManager()](https://msdn.microsoft.com/en-us/library/bb646656\(v=office.15\)) method on the ExchangeUser object of the CurrentUser property of the NameSpace object. A receive rule is then created to move received messages to a subfolder of the Inbox for the following conditions:

  - The message is from the user’s manager.

  - The recipient is on the **To:** line of the message.

  - The message is not a meeting request or update.

Finally, the message is flagged for follow-up today. CreateManagerRule also illustrates appropriate error handling for conditions that could raise an exception such as the user being offline or disconnected in cached Exchange mode.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void CreateManagerRule()
{
    Outlook.ExchangeUser manager;
    Outlook.Folder managerFolder;
    Outlook.AddressEntry currentUser =
        Application.Session.CurrentUser.AddressEntry;
    if (currentUser.Type == "EX")
    {
        try
        {
            manager = currentUser.
                GetExchangeUser().GetExchangeUserManager();
        }
        catch
        {
            Debug.WriteLine("Could not obtain user's manager.");
            return;
        }
        Outlook.Rules rules;
        try
        {
            rules = Application.Session.DefaultStore.GetRules();
        }
        catch
        {
            Debug.WriteLine("Could not obtain rules collection.");
            return;
        }
        if (manager != null)
        {
            string displayName = manager.Name;
            Outlook.Folders folders =
                Application.Session.GetDefaultFolder(
                Outlook.OlDefaultFolders.olFolderInbox).Folders;
            try
            {
                managerFolder =
                    folders[displayName] as Outlook.Folder;
            }
            catch
            {
                managerFolder =
                    folders.Add(displayName, Type.Missing)
                    as Outlook.Folder;
            }
            Outlook.Rule rule = rules.Create(displayName,
                Outlook.OlRuleType.olRuleReceive);

            // Rule conditions
            // From condition
            rule.Conditions.From.Recipients.Add(
                manager.PrimarySmtpAddress);
            rule.Conditions.From.Recipients.ResolveAll();
            rule.Conditions.From.Enabled = true;

            // Sent only to me
            rule.Conditions.ToMe.Enabled = true;

            // Rule exceptions
            // Meeting invite or update
            rule.Exceptions.MeetingInviteOrUpdate.Enabled = true;

            // Rule actions
            // MarkAsTask action
            rule.Actions.MarkAsTask.MarkInterval =
                Outlook.OlMarkInterval.olMarkToday;
            rule.Actions.MarkAsTask.FlagTo = "Follow-up";
            rule.Actions.MarkAsTask.Enabled = true;

            // MoveToFolder action
            rule.Actions.MoveToFolder.Folder = managerFolder;
            rule.Actions.MoveToFolder.Enabled = true;
            try
            {
                rules.Save(true);
            }
            catch (Exception ex)
            {
                Debug.WriteLine(ex.Message);
            }
        }
    }
}
```

## See also



[Rules](rules.md)

