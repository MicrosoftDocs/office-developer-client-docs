---
title: Using late binding if depending on multiple versions of Outlook
TOCTitle: Using late binding if depending on multiple versions of Outlook
ms:assetid: 4e5412a0-d0f8-4819-ba0f-f36ba885f8f6
ms:contentKeyID: 55119791
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Using late binding if depending on multiple versions of Outlook

Managed Outlook add-ins that use the Outlook Primary Interop Assembly (PIA) are compiled with type information that the PIA provides. This **early binding** of type information for methods and properties allows the compiler to perform type and syntax checks to ensure that the correct number and type of parameters are passed to the method or property, and that the returned value is of the expected type. 

However, early binding has the disadvantage of introducing version incompatibility if a method or property that the add-in calls has a different declaration in an earlier version. For example, adding new methods and properties or modifying existing members of an object can alter the binary layout of the object and cause problems with a managed add-in that uses the more recent type information to automate an earlier version of Outlook. 

In such cases, **late binding** waits until run time to bind property and method calls to their objects. Late binding can help avoid complications from types that are different in different versions of Outlook, and is especially useful when writing add-ins that depend on multiple versions of Outlook.

Late binding involves an add-in calling the [IDispatch](http://go.microsoft.com/fwlink/?linkid=88965) interface implemented by Outlook. To use late binding in Visual C\#, use the [System.Type.InvokeMember](http://go.microsoft.com/fwlink/?linkid=88970) method. This method calls [IDispatch::GetIDsOfNames](http://go.microsoft.com/fwlink/?linkid=88966) and [IDispatch::Invoke](http://go.microsoft.com/fwlink/?linkid=88967) to bind to Outlook’s methods and properties. The IDispatch::GetIDsOfNames method allows Visual C\# to interrogate an object about what methods and properties it supports and the IDispatch::Invoke method then allows Visual C\# to call those methods and properties. 

For more information about using late binding in C\#, see [KB 302902: Binding for Office Automation Servers with Visual C\# .NET](http://go.microsoft.com/fwlink/?linkid=88971). For more information about using late binding in Visual Basic, see [KB 304661: How to Use Visual Basic .NET for Binding for Office Automation Servers](http://go.microsoft.com/fwlink/?linkid=88972).

Note that late binding requires obtaining a DispID for every method or property, so late binding generally does not perform as well as early binding. For more information about how early binding compares with late binding, see [KB 245115: Using Early Binding and Late Binding in Automation](http://go.microsoft.com/fwlink/?linkid=88973).

## See also

- [Introduction to interoperability between COM and .NET](introduction-to-interoperability-between-com-and-net.md)

