---
title: 'Display Selected Items in the Active Explorer'
TOCTitle: 'Display Selected Items in the Active Explorer'
ms:assetid: 31bb217b-8b45-4b50-942e-b6c2a7f13c83
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn292517(v=office.15)
ms:contentKeyID: 55119844
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Display Selected Items in the Active Explorer

This example shows how to use the OutlookItem helper class to conveniently display all the items selected in the active Explorer window.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

The [Selection](https://msdn.microsoft.com/en-us/library/bb612099\(v=office.15\)) object contains the set of Outlook items currently selected in the active Outlook explorer. Neither the active explorer, represented by [ActiveExplorer()](https://msdn.microsoft.com/en-us/library/bb647410\(v=office.15\)), nor the set of selected items indicates the type of the items that are selected. Normally, you would have to first identify the item type and then call the specific Display method for that type. Because the Display method is common to all Outlook items objects and the OutlookItem helper class includes this method, you can take advantage of the helper class, by declaring an instance of the OutlookItem object, myItem, and using myItem.Display to display each item in the selection. You can see the implementation of the OutlookItem helper class in [Create a Helper Class to Access Common Outlook Item Members](how-to-create-a-helper-class-to-access-common-outlook-item-members.md)

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void DisplaySelectedItems()
{
    Outlook.Selection selection =
        Application.ActiveExplorer().Selection;
    for (int i = 1; i <= selection.Count; i++)
    {
        OutlookItem myItem = new OutlookItem(selection[i]);
        myItem.Display();
    }
}
```

## See also

#### Tasks

[Create a Helper Class to Access Common Outlook Item Members](how-to-create-a-helper-class-to-access-common-outlook-item-members.md)



[General Outlook Items](https://msdn.microsoft.com/en-us/library/hh780899\(v=office.15\))

