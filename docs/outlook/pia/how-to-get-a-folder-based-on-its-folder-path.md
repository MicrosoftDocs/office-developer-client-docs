---
title: 'Get a Folder Based on Its Folder Path'
TOCTitle: 'Get a Folder Based on Its Folder Path'
ms:assetid: 613f2209-667c-48f0-82cf-86e3c9a24cb4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184612(v=office.15)
ms:contentKeyID: 55119858
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Get a Folder Based on Its Folder Path

This example takes a folder path and obtains the associated folder.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In the following code example, the GetKeyContacts method uses the [GetRootFolder()](https://msdn.microsoft.com/en-us/library/bb645807\(v=office.15\)) property to obtain the folder path of the Contacts\\Key Contacts folder. The GetFolder method is then called by using the [FolderPath](https://msdn.microsoft.com/en-us/library/bb647409\(v=office.15\)) property as the argument. If GetFolder returns a folder, a message will appear saying the Key Contacts are found. The GetFolder method takes in a path to a folder and returns the correct [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) object. This is done by first splitting the FolderPath property into a string array and then using the array to find the correct **Folder** object starting from the top of the FolderPath property. If the specified folder is not found, GetFolder returns a null reference.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void GetKeyContacts()
{
    string folderPath =
        Application.Session.
        DefaultStore.GetRootFolder().FolderPath
        + @"\Contacts\Key Contacts";
    Outlook.Folder folder = GetFolder(folderPath);
    if (folder != null)
    {
        //Work with folder here
        Debug.WriteLine("Found Key Contacts");
    }
}

// Returns Folder object based on folder path
private Outlook.Folder GetFolder(string folderPath)
{
    Outlook.Folder folder;
    string backslash = @"\";
    try
    {
        if (folderPath.StartsWith(@"\\"))
        {
            folderPath = folderPath.Remove(0, 2);
        }
        String[] folders =
            folderPath.Split(backslash.ToCharArray());
        folder =
            Application.Session.Folders[folders[0]]
            as Outlook.Folder;
        if (folder != null)
        {
            for (int i = 1; i <= folders.GetUpperBound(0); i++)
            {
                Outlook.Folders subFolders = folder.Folders;
                folder = subFolders[folders[i]]
                    as Outlook.Folder;
                if (folder == null)
                {
                    return null;
                }
            }
        }
        return folder;
    }
    catch { return null; }
}        
```

## See also



[Folders](folders.md)

