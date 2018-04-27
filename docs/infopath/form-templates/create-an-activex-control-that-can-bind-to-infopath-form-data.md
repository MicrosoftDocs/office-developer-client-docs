---
title: "Create an ActiveX Control that can Bind to InfoPath Form Data"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: a0d62047-bf08-9f70-de00-7f81ef1331f1
description: "You can host ActiveX controls in InfoPath forms that are designed to be opened in the InfoPath editor. These controls can be preexisting (with some constraints) or can be written specifically for InfoPath."
---

# Create an ActiveX Control that can Bind to InfoPath Form Data

You can host ActiveX controls in InfoPath forms that are designed to be opened in the InfoPath editor. These controls can be preexisting (with some constraints) or can be written specifically for InfoPath.
  
## Write an ActiveX Control

As with other controls in InfoPath, ActiveX controls should support existing Component Object Model (COM) interfaces:
  
- **IDispatch**
    
- **IPersistPropertyBag**
    
- **IPersistStreamInit**
    
- **IPropertyPage**
    
- **IObjectSafety**
    
- **IPropertyNotifySink**
    
- **IViewObject**
    
- **IOleObject**
    
- **IOleInPlaceObject**
    
In order for InfoPath to update properties in the Document Object Model (DOM) at the time that they change in the control, the control should implement the following interfaces:
  
- **IConnectionPointContainer**
    
- **IEnumConnectionPoints**
    
- **IConnectionPoint**
    
- **IEnumConnections**
    
Also, there are two InfoPath-specific COM interfaces that provide tighter integration of controls:
  
- [IInfoPathControl](http://msdn.microsoft.com/en-us/library/bb264625.aspx)
    
- [IInfoPathControlSite](http://msdn.microsoft.com/en-us/library/bb264627.aspx)
    
## Add an ActiveX Control to the InfoPath Design Environment

The **Add or Remove Custom Controls** command on the **Controls** task pane enables you to use the **Add Custom Control Wizard** to add a custom control. By using the wizard, you can select an ActiveX control that has already been registered or find additional custom controls on Office Marketplace. After you select a control, you can specify the following items. 
  
- Specify a CAB to install the ActiveX control with your form template.
    
- Specify a binding property to bind to the XML.
    
- Specify a property that is used to enable or disable the control in response to rules or digital signatures, which can be useful, for example, when the XML is not present or when conditional formatting is used.
    
- Specify data type binding.
    
> [!NOTE]
> If you are developing an ActiveX control and have added it to the **Controls** task pane in InfoPath, you will be unable to rebuild the ActiveX control until InfoPath is closed. 
  
## Deploy an ActiveX Control

To distribute an ActiveX control, you can write an installer that installs the control on the target computer and copies the InfoPath Control Template (ICT) file and the CAB file to the user's folder, \Users\\<username\>\AppData\Local\Microsoft\InfoPath\Controls. Note that if two or more developers are collaborating on developing forms that use ActiveX controls, each developer should have the controls that were added to the InfoPath design environment, or they will be unable to modify the properties of the controls from InfoPath.
  
## See also

#### Other resources

[Lab 6: Adding ActiveX Controls in InfoPath 2003](7655ed94-ae96-4d7e-b529-a0dfd2e70a94)
  
[Creating an InfoPath Custom Control using C# and .NET (InfoPath Team Blog)](http://blogs.msdn.com/infopath/archive/2005/04/15/creating-an-infopath-custom-control-using-c-and-net.aspx)

