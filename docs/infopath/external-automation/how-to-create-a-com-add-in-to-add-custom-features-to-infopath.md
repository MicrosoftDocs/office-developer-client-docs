---
title: "Create a COM Add-in to Add Custom Features to InfoPath"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
keywords:
- infopath 2007, creating com add-ins,InfoPath 2007, adding custom features,COM add-ins [InfoPath 2007]
ms.localizationpriority: medium
ms.assetid: af0b0bc9-20ef-4503-8b3b-8f2a97b671a2
description: "Microsoft InfoPath supports COM Add-ins for extending the form editing user experience. Although support for COM Add-ins was first added in InfoPath, other Office applications such as Microsoft Office Word and Microsoft Office Excel have supported COM add-ins since Office 2000."
---

# Create a COM Add-in to Add Custom Features to InfoPath

Microsoft InfoPath supports COM Add-ins for extending the form editing user experience. Although support for COM Add-ins was first added in InfoPath, other Office applications such as Microsoft Office Word and Microsoft Office Excel have supported COM add-ins since Office 2000.
  
COM Add-in support in InfoPath is available for the form editing environment. The form design environment cannot be extended by using COM Add-ins.
  
## The IDTExtensibility2 Interface

The InfoPath editing environment provides support for the **IDTExtensibility2** interface, which must be implemented by developers of COM Add-ins. **IDTExtensibility2** is a dual-interface object that provides five methods which act as events within the editing environment. These methods allow the COM add-in to respond to environment startup and shutdown conditions, listed in the following table. 
  
|**Interface**|**Description**|
|:-----|:-----|
|**OnAddInsUpdate (ByVal custom() As Variant)** <br/> |Occurs when an add-in is loaded or unloaded in the environment.  <br/> |
|**OnBeginShutdown (ByVal custom() As Variant)** <br/> |Occurs when the environment is being shut down.  <br/> |
|**OnConnection(ByVal Application As Object, ByVal ConnectMode As ext_ConnectMode, ByVal AddInInst As Object, ByVal custom() As Variant)** <br/> |Occurs when an add-in is loaded in the environment.  <br/> |
|**OnDisconnection (ByVal RemoveMode As ext_DisconnectMode, ByVal custom() As Variant)** <br/> |Occurs when an add-in is unloaded from the environment.  <br/> |
|**OnStartupComplete (ByVal custom() As Variant)** <br/> |Occurs when the environment has completed starting.  <br/> |
   
## Registering COM Add-ins

All Office applications, including InfoPath, use the registry to list add-ins in the COM Add-Ins collection, to store the connect state, and to store the boot or demand load information. For InfoPath COM Add-ins, the name of each add-in appears under the following key:
  
`HKEY_CURRENT_USER\Software\Microsoft\Office\InfoPath\AddIns\`
  
For COM Add-ins installed for use by every user of the client computer, the registry key is located in the HKLM registry hive:
  
`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\InfoPath\AddIns\`
  
The registry key name corresponds to the **ProgIdAttribute** of the add-in, and contains the following values. 
  
|**Name**|**Type**|**Description**|
|:-----|:-----|:-----|
|**FriendlyName** <br/> |**String** <br/> |The name that is displayed in the **COM Add-ins** dialog box and listed in the **Add-ins** page of the **Trust Center**.  <br/> |
|**Description** <br/> |**String** <br/> |The string that is displayed when the add-in is selected in the **Trust Center**.  <br/> |
|**LoadBehavior** <br/> |**DWORD** <br/> |Specifies the way the COM Add-in is loaded. The value can be a combination of 0, 1, 2, 8, and 16. See the table below for more information.  <br/> |
   
The **DWORD** value for **LoadBehavior** should contain a value describing how the COM Add-in loads in the editing environment. The value can be from the table below, or a combination of values from the table. For example, a COM Add-in created in Visual Studio 2005 will have a **LoadBehavior** of "3" loaded at application startup and be connected. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Disconnected. The add-in shows as Inactive in the **COM Add-in** dialog box.  <br/> |
|1  <br/> |Connected. The add-in shows as Active in the **COM Add-in** dialog box.  <br/> |
|2  <br/> |Load at Startup. The add-in is loaded and connected when the host application starts.  <br/> |
|8  <br/> |Load on Demand. The add-in is loaded and connected when the host application requires it, for example when a user clicks a button that uses functionality in the add-in.  <br/> |
|16  <br/> |Connect first time. The add-in will be loaded and connected the first time the user runs the host application after registering the add-in.  <br/> |
   
## Creating a Managed COM Add-in with Visual Studio 2005 or Visual Studio 2008

To create a managed COM add-in using Microsoft Visual Studio 2005 or Visual Studio 2008, create a Shared Add-In project as follows: 
  
1. Start Visual Studio.
    
2. On the **File** menu, click **New Project**.
    
3. In the **Project Types** pane of the **New Project** dialog box, click the **Other Projects Types** folder, and then click **Extensibility**.
    
4. In the **Templates** pane, click **Shared Add-In**.
    
5. In the **Name** box, type a name for the project. 
    
6. In the **Location** box, type a folder path or click **Browse** and select a folder path, and then click **OK**. The **Shared Add-in Wizard** appears. 
    
7. Click **Next** in the **Shared Add-in Wizard**. The **Select a Programming Language** page appears. 
    
8. Click **Create an Add-in using Visual Basic**, then click **Next**. The **Select An Application Host** page appears. 
    
9. Uncheck the boxes next to each application except **Microsoft InfoPath**, and then click **Next**. The **Enter a Name and Description** page appears. 
    
10. In the **What is the name of your Add-In** box, type the name of your COM Add-in. 
    
11. In the **What is the description of your Add-In** box, type the description for your COM Add-in, and click **Next**. The **Choose Add-In Options** page appears. 
    
12. Check the **I would like my Add-in to load when the host application loads** and **My Add-in should be available to all users of the computer it was installed on, not just the person who installs it** boxes. 
    
13. Click **Next** to review the **Summary** page, then click **Finish**.
    
After the project is created by Visual Studio, you will see two projects in the Solution Explorer window. The first project is the project for the COM Add-in; the second project is a setup project for deploying the COM Add-in. The **Shared Add-in Wizard** only inserts a reference to the **Microsoft Office 14.0 Object Library**, so it is necessary to insert a reference to the InfoPath object library using the following steps:
  
1. Double-click **My Project** to display the add-in project properties. Click the **References** tab to display the references automatically added to the project. 
    
2. Click the **Add** button to display the **Add Reference** dialog box. 
    
3. On the **COM** tab, double-click **Microsoft.InfoPath 2.0 Type Library**, and click **OK**.
    
4. Adding a reference to the **Microsoft InfoPath 3.0 Type Library** also adds references to three assemblies that must be removed: **ADODB**, **MSHTML**, and **MSXML2**. In **Solution Explorer** under **References**, right-click each of these references, and then click **Remove**.
    
## Viewing the Registry Settings

To view the registry settings that will be created when the COM Add-in is installed, follow these steps:
  
1. Right-click the root node of the setup project in the **Solution Explorer**, click **View**, then **Editor**, then click **Registry**.
    
2. In the left-hand pane, click the plus to expand **HKEY_LOCAL_MACHINE**, **Software**, **Microsoft**, **InfoPath**, then **AddIns**.
    
3. Click the name corresponding to your shared add-in project's **ProgID**.
    
To change any of these properties, right-click the property, click **Properties Window**, and change the **Value** box in the **Properties Window**.
  
## Compiling and Distributing the Shared Add-In

To compile the managed COM Add-in for testing on the computer on which the Shared Add-In project was developed, right-click the root node of the Shared Add-In project in the Solution Explorer and click Build. If the project builds with no errors, you can start the InfoPath editing environment and begin using the managed COM Add-in. If you have an instance of InfoPath running, close it before building the project. It may also be necessary to open the COM Add-ins dialog box to verify that the COM Add-in is registered. To open the COM Add-ins dialog box, follow these steps:
  
1. Open the InfoPath editing environment. The easiest way to do this is to open an existing form template, which will create a new form based on that form template.
    
2. Click **Trust Center** on the **Tools** menu. 
    
3. Click the **Add-ins** category on the left. 
    
4. In the **Manage** section near the bottom of the **Trust Center** dialog box, select **COM Add-ins** from the list and click the **Go** button. 
    
5. In the **COM Add-ins** dialog box, you will see the name of your recently-built add-in and there should be a check box next to it. If there is no check box next to it, the COM Add-in failed to load due to an error, which will be listed in the **Load Behavior** section of the dialog box. 
    
To compile the managed COM add-in for use on a computer other than the computer on which the Shared Add-In project was developed, you must follow additional steps to secure your code. For information on securing Shared Add-In projects for use on other computers, see the following three articles:
  
- [Deployment of Managed COM Add-Ins in Office XP](https://go.microsoft.com/fwlink/?LinkID=73473)
  
- [Using the COM Add-in Shim Solution to Deploy Managed COM Add-ins in Office XP](https://go.microsoft.com/fwlink/?LinkID=73474)
  
- [Isolating Office Extensions with the COM Shim Wizard](https://go.microsoft.com/fwlink/?LinkID=73475)
  
> [!IMPORTANT]
> Not isolating the COM Add-in may cause memory leaks and application instability. 
  
> [!NOTE]
> If the .NET Framework or other required assemblies from the setup project are not already installed on target computers, the .msi file may not install properly. Also, you cannot distribute the .msi file and then attempt to install the .msi file. You must also distribute the other support files in the same folder as the original .msi file generated by Visual Studio. 
  
## Coding in the COM Add-in

Application events that occur in the InfoPath form editing environment can be captured by a COM Add-in. The following events of the [ApplicationEvents](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.ApplicationEvents.aspx) object can be used by the COM Add-in to respond to user actions: 
  
|**Event**|**Description**|
|:-----|:-----|
|[NewXDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument.aspx) Event  <br/> |Occurs when a new form is created.  <br/> |
|[Quit](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.Quit.aspx) Event  <br/> |Occurs when the user quits InfoPath.  <br/> |
|[WindowActivate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate.aspx) Event  <br/> |Occurs when any document window is activated.  <br/> |
|[WindowDeactivate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate.aspx) Event  <br/> |Occurs when any document window is deactivated.  <br/> |
|[WindowSize](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowSize.aspx) Event  <br/> |Occurs when any document window is resized or moved.  <br/> |
|[XDocumentBeforeClose](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose.aspx) Event  <br/> |Occurs immediately before any open document closes.  <br/> |
|[XDocumentBeforePrint](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforePrint.aspx) Event  <br/> |Occurs immediately before any open document is printed.  <br/> |
|[XDocumentBeforeSave](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeSave.aspx) Event  <br/> |Occurs immediately before any open document is saved.  <br/> |
|[XDocumentChange](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentChange.aspx) Event  <br/> |Occurs when a new form is created, when an existing form is opened, or when another form is made the active form.  <br/> |
|[XDocumentOpen](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen.aspx) Event  <br/> |Occurs when a document is opened.  <br/> |
   
To capture these events in the COM Add-in, you must declare the following class-level variables in your **Connect** class: 
  
```vb
InfoPathApplication = DirectCast( _
   application, Microsoft.Office.Interop.InfoPath._Application3)
InfoPathApplicationEvents = DirectCast( _
   InfoPathApplication.Events, _
   Microsoft.Office.Interop.InfoPath.ApplicationEvents)
```

```cs
InfoPathApplication =
   (Microsoft.Office.Interop.InfoPath._Application3)application;
InfoPathApplicationEvents =
   (Microsoft.Office.Interop.InfoPath.ApplicationEvents)
   InfoPathApplication.Events;
```

The first line casts the generic application **Object** received by the add-in to the [_Application3](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._Application3.aspx) object. The second line casts the [Events](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._Application3.Events.aspx) property of the **_Application3** object (represented by the **InfoPathApplication** variable) to the [ApplicationEvents](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.ApplicationEvents.aspx) object. 
  
To create event handlers, select **InfoPathApplicationEvents** from the **Class Name** drop-down box at the top of the Visual Studio window, and then select the event you want to handle in the **Method Name** drop-down box at the top of the Visual Studio window. For example, if you need to control when a form is saved, you handle the **XDocumentBeforeSave** event. Selecting **XDocumentBeforeSave** from the **Method Name** drop-down automatically inserts the following procedure: 
  
```vb
Private Sub InfoPathApplicationEvents_XDocumentBeforeSave( _
   ByVal pDocument As Microsoft.Office.Interop.InfoPath._XDocument, _
   ByRef pfCancel As Boolean) _
   Handles InfoPathApplicationEvents.XDocumentBeforeSave
End Sub
```

```cs
private void InfoPathApplicationEvents_XDocumentBeforeSave(
   Microsoft.Office.Interop.InfoPath._XDocument pDocument, ref bool pfCancel)
{
}

```

Any of the events of the **ApplicationEvents** object can be handled by the COM Add-in using the same method. 
  
## See also

- [Creating a Microsoft Office 2000 COM Add-in](https://go.microsoft.com/fwlink/?LinkID=73468) 
- [Creating Office Managed COM Add-Ins with Visual Studio .NET](https://go.microsoft.com/fwlink/?LinkID=73470)
- [Working with the IDTExtensibility2 Event Procedures](https://go.microsoft.com/fwlink/?LinkID=73471)
- [Build an Office COM Add-in With Visual Basic .NET](https://go.microsoft.com/fwlink/?LinkID=73469)
- [Build an Office COM add-in by using Visual C# .NET](https://support.microsoft.com/help/302901/how-to-build-an-office-com-add-in-by-using-visual-c-net)
- [Creating InfoPath 2007 Add-Ins by Using Visual Studio 2005 Tools for the Office System SE](https://msdn.microsoft.com/library/bb968857%28office.12%29.aspx)

