---
title: 'How to: Enumerate and Add Categories'
TOCTitle: 'How to: Enumerate and Add Categories'
ms:assetid: 17a94a01-c463-4332-851e-7d280c66d8c2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424467(v=office.15)
ms:contentKeyID: 55119829
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Enumerate and Add Categories

This example shows how to enumerate categories and add a category to the main category list.

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


The Outlook object model supports categories that help organize items in a user’s Inbox. To maintain a higher level of organization, you can do the following:

  - Categorize Outlook items and display them by category.

  - Apply multiple color categories to a single Outlook item.

  - Group and sort Outlook items by color category.

  - Assign shortcut keys to each color category, enabling users to more easily categorize items.

  - Create, delete, and change color categories either programmatically, or by user action within the Outlook user interface.

To expose the functionality of categories, the Outlook object model provides a [Category](https://msdn.microsoft.com/en-us/library/bb623480\(v=office.15\)) object that represents a single user-defined color category in the main category list. The main category list contains color categories that are presented in the Outlook user interface. The list is represented by the [Categories](https://msdn.microsoft.com/en-us/library/bb623535\(v=office.15\)) collection of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object. To create a Category object, use the [Add(String, Object, Object)](https://msdn.microsoft.com/en-us/library/bb623093\(v=office.15\)) method of the Categories collection. When you create a Category object, a globally unique identifier (GUID) is created, and this identifier cannot be changed. It is represented by the [CategoryID](https://msdn.microsoft.com/en-us/library/bb647100\(v=office.15\)) property. You can, however, change the name, color, and shortcut key associated with a color category by setting the [Name](https://msdn.microsoft.com/en-us/library/bb645577\(v=office.15\)), [Color](https://msdn.microsoft.com/en-us/library/bb612316\(v=office.15\)), and [ShortcutKey](https://msdn.microsoft.com/en-us/library/bb644944\(v=office.15\)) properties, respectively, of the Category object. You can change the Color property by setting or getting its [OlCategoryColor](https://msdn.microsoft.com/en-us/library/bb608974\(v=office.15\)) constant. To reproduce the color in a custom control, use the following read-only properties of the Category object:

  - [CategoryBorderColor](https://msdn.microsoft.com/en-us/library/bb610083\(v=office.15\))

  - [CategoryGradientBottomColor](https://msdn.microsoft.com/en-us/library/bb647357\(v=office.15\))

  - [CategoryGradientTopColor](https://msdn.microsoft.com/en-us/library/bb623975\(v=office.15\))

These properties return an OLE\_COLOR value, which is dependent on the Color property of the Category object.

Outlook items are displayed based on the category name. Each item object has a Categories property that stores a comma-delimited string that represents category names. (For example, for the [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object, you would use the MailItem [Categories](https://msdn.microsoft.com/en-us/library/bb646442\(v=office.15\)) property). This enables you to add a category to the item, even if the category is not present in the main category list.


> [!NOTE]
> <P>If the Categories property of an item contains a category name that is not in the Categories collection of the NameSpace object, the category name associated with that Outlook item is displayed, but without an associated color. The Categories property on an Item object does not return a Categories collection.</P>



In the following code example, the first procedure, EnumerateCategories, gets the current user’s main list of categories, represented by the Categories collection. It then enumerates the Category objects in that collection, and writes the Name and CategoryID properties to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection. The second procedure, AddACategory, gets the current user’s main list of categories and uses the CategoryExists method to check whether a category named “ISV” exists in the collection. If no category with the name “ISV” exists, AddACategory adds a category named “ISV” to the main category list and assigns it a dark blue color by using the Add method of the Categories collection. It also assigns CTRL+F11 as the shortcut key for the category.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void EnumerateCategories()
{
    Outlook.Categories categories =
        Application.Session.Categories;
    foreach (Outlook.Category category in categories)
    {
        Debug.WriteLine(category.Name);
        Debug.WriteLine(category.CategoryID);
    }
}

private void AddACategory()
{
    Outlook.Categories categories =
        Application.Session.Categories;
    if (!CategoryExists("ISV"))
    {
        Outlook.Category category = categories.Add("ISV",
            Outlook.OlCategoryColor.olCategoryColorDarkBlue,
            Outlook.OlCategoryShortcutKey.olCategoryShortcutKeyCtrlF11);
    }
}

private bool CategoryExists(string categoryName)
{
    try
    {
        Outlook.Category category = 
            Application.Session.Categories[categoryName];
        if(category != null)
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



[Color Categories](color-categories.md)

