---
title: "Work with Information Rights Management Settings"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
keywords:
- information rights management [infopath 2007],InfoPath 2007, Information Rights Management,IRM [InfoPath 2007]
 
localization_priority: Normal
ms.assetid: 4ad91898-b23e-4410-8839-a65259e53d37
description: "There are two types of Information Rights Management (IRM) settings available in Microsoft InfoPath: one for protecting access to InfoPath form templates, and one for controlling access to and actions on form data contained in completed forms."
---

# Work with Information Rights Management Settings

There are two types of Information Rights Management (IRM) settings available in Microsoft InfoPath: one for protecting access to InfoPath form templates, and one for controlling access to and actions on form data contained in completed forms.
  
> [!NOTE]
> Restricting permission is only available to form templates compatible with the InfoPath editor. Browser-compatible form templates do not support IRM. 
  
## Adding the Manage Credentials Command to the Quick Access Toolbar

The **Manage Credentials** command used to work with IRM settings when designing a form template is not available by default. Use the following steps to add it to the **Quick Access Toolbar**.
  
### Add the Manage Credentials Command to the Quick Access Toolbar

1.  Click the arrow on the right end of the **Quick Access Toolbar** to pull down the **Customize Quick Access Toolbar** menu, and then click **More Commands**.
    
2. In the **Choose commands from** list, select **All Commands**.
    
3. Scroll down the list to **Manage Credentials**, and then click **Add**.
    
4. Click **OK**.
    
For more information about using **Manage Credentials** command and the **Permission** dialog box in InfoPath, see the "Create a Form Template with Restricted Permission" topic in InfoPath help. 
  
## The IRM Object Model

Use the [Permission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.aspx) class to access the [UserPermissionCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.aspx) and IRM permission settings that can be applied to a form. To access the **Permission** object associated with a form template, use the [Permission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Permission.aspx) property of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class. The returned **Permission** object provides access to the collection of [UserPermission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermission.aspx) objects associated with the form template and each form instance created with that template. 
  
The **Permission** object and its properties and methods are available whether permissions are restricted on the active form template or not. Use the [Enabled](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.Enabled.aspx) property to determine whether a form has restricted permissions. 
  
Permissions on a form are enabled in one of the following ways by using properties and methods of the Permission class:
  
The **Enabled** property is set to **true**.
  
The [DocumentAuthor](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.DocumentAuthor.aspx) property is set. 
  
The [RequestPermissionUrl](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.RequestPermissionUrl.aspx) property is set. 
  
The [StoreLicenses](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.StoreLicenses.aspx) property is set to **true** or **false**.
  
The [ApplyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.ApplyPolicy.aspx) method is called. 
  
> [!NOTE]
> If the Windows Rights Management client is not installed on a user's computer, using the **Permission** class raises an exception. 
  
To work programmatically with IRM settings of individual users in forms, use the **UserPermissionCollection** and **UserPermission** classes. 
  
A **UserPermission** object associates a set of permissions for the current form with a single user and an optional expiration date. Use the [Add](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Add.aspx) method of the **UserPermissionCollection** class to add and grant a user a set of permissions on the current form. Use the [Remove](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Remove.aspx) method of the **UserPermissionCollection** class to remove a user and the user's permissions. While some permissions granted through the user interface apply to all users, such as printing and expiration date, you can use the **UserPermission** and **UserPermissionCollection** classes to assign them on a per-user basis with per-user expiration dates. The object model allows developers to enumerate permission settings in a form and to provide functionality that allows form users to add permissions to the form without having to use the **Form Permission** task pane or the **Permission** dialog box. 
  
> [!NOTE]
> Permissions cannot be applied when a form is in preview mode. For this reason, all of the properties of the **Permission** class are read-only when a form is being previewed. In preview mode, the **Enabled** property will always return **false**, and if code attempts to change this setting, a **System.Runtime.InteropServices.COMException** is raised and the error "The property/method is not available in preview mode" is returned. Similarly, the methods associated with the **UserPermission** and **UserPermissionCollection** classes will also return this error message when used in preview mode. 
  
### Overview of the Permission Class

The **UserPermissionCollection** class provides the following properties and one method. 
  
|**Name**|**Description**|
|:-----|:-----|
|[ApplyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.ApplyPolicy.aspx) method  <br/> |Applies a policy to the form using a policy template file.  <br/> |
|[DocumentAuthor](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.DocumentAuthor.aspx) property  <br/> |Gets or sets the author of the current form as an e-mail address.  <br/> |
|[Enabled](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.Enabled.aspx) property  <br/> |Gets or sets whether the permission settings represented by the **Permission** object are enabled for the current form.  <br/> |
|[PermissionFromPolicy](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.PermissionFromPolicy.aspx) property  <br/> |Gets or sets whether a permission policy has been applied to the current form.  <br/> |
|[PolicyDescription](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.PolicyDescription.aspx) property  <br/> |Gets a description of the policy that was applied to the current form.  <br/> |
|[PolicyName](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.PolicyName.aspx) property  <br/> |Gets the name of the policy that was applied to the current form.  <br/> |
|[RequestPermissionUrl](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.RequestPermissionUrl.aspx) property  <br/> |Gets or sets the file, URL, or e-mail address to contact for users who need additional permissions on the current form.  <br/> |
|[StoreLicenses](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.StoreLicenses.aspx) property  <br/> |Gets or sets whether the user's license to view the current form should be cached to allow offline viewing when the user cannot connect to a rights management server.  <br/> |
|[UserPermissions](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.UserPermissions.aspx) property  <br/> |Gets a **UserPermissionCollection** object for the current form.  <br/> |
   
### Overview of the UserPermissionCollection Class

The **UserPermissionCollection** class provides the following properties and methods. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Add](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Add.aspx) method (+3 overloads)  <br/> |Adds a new user to the current form, optionally specifying permissions and an expiration date.  <br/> |
|[Remove](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Remove.aspx) method  <br/> |Removes the **UserPermission** object with the specified **UserId** from the collection.  <br/> |
|[RemoveAll](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.RemoveAll.aspx) method  <br/> |Removes all **UserPermission** objects from the collection.  <br/> |
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Count.aspx) property  <br/> |Gets the number of **UserPermission** objects in the collection.  <br/> |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermissionCollection.Item.aspx) property (+1 overload)  <br/> |Gets a **UserPermission** object.  <br/> |
   
### Overview of the UserPermission Class

The **UserPermission** class provides the following properties and one method. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Remove](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermission.Remove.aspx) method  <br/> |Removes the current **UserPermission** object from the form's permissions.  <br/> |
|[ExpirationDate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermission.ExpirationDate.aspx) property  <br/> |Gets or sets the optional expiration date for the permissions on the current form assigned to the user associated with an instance of the **UserPermission** class.  <br/> |
|[Permission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermission.Permission.aspx) property  <br/> |Gets or sets a value representing the permissions on the current form assigned to the user associated with an instance of the **UserPermission** class.  <br/> |
|[UserId](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.UserPermission.UserId.aspx) property  <br/> |Gets the e-mail address of the user whose permissions on the current form are determined by the specified **UserPermission** object.  <br/> |
   
### The PermissionType Enumeration

A user's permissions are set or read using [PermissionType](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.PermissionType.aspx) enumeration values. 
  
|**Name**|**Description**|
|:-----|:-----|
|**PermissionType.Change** <br/> |Allows users to view, edit, copy, and save, but not print a form. Equivalent to the **Read**, **Edit**, **Save**, and **Extract** permissions combined.  <br/> |
|**PermissionType.Edit** <br/> |Allows the user to edit the form.  <br/> |
|**PermissionType.Extract** <br/> |Allows a user with the **Read** permission to copy content in the form.  <br/> |
|**PermissionType.FullControl** <br/> |Allows the user to add, change, and remove permissions for other users of a form.  <br/> |
|**PermissionType.ObjectModel** <br/> |Allows a user to access the form document programmatically through its object model. Users without the **ObjectModel** permission cannot use the object model to determine their own permissions.  <br/> |
|**PermissionType.Print** <br/> |Allows the user to print the form.  <br/> |
|**PermissionType.Read** <br/> |Allows the user to read (view) the form. (The **Read** and **View** permissions are equivalent.)  <br/> |
|**PermissionType.Save** <br/> |Allows the user to save the form.  <br/> |
|**PermissionType.View** <br/> |Allows the user to view (read) the form. (The **Read** and **View** permissions are equivalent.)  <br/> |
   
### Example

In the following example, clicking the **Button** control gets the **UserPermissionsCollection** for the current form, adds and assigns a user to the Change access level, and sets an expiration date of two days from the current date. 
  
```cs
public void CTRL1_Clicked(object sender, ClickedEventArgs e)
{
   string strExpirationDate = DateTime.Today.AddDays(2).ToString();
   DateTime dtExpirationDate = DateTime.Parse(strExpirationDate);
   this.Permission.UserPermissions.Add("someone@example.com", 
      PermissionType.Change, dtExpirationDate);
}
```

```VB.net
Public Sub CTRL1_Clicked(ByVal sender As Object, _
   ByVal e As ClickedEventArgs)
   Dim strExpirationDate As String = _
      DateTime.Today.AddDays(2).ToString()
   dtExpirationDate As DateTime = DateTime.Parse(strExpirationDate)
   Me.Permission.UserPermissions.Add("someone@example.com", _
      PermissionType.Change, dtExpirationDate)
End Sub
```


