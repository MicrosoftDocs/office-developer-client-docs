---
title: "Add an Event Handler"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- versionupgrade event [infopath 2007],handling events [InfoPath 2007],Changing event [InfoPath 2007],InfoPath 2007, adding event handlers,Changed event [InfoPath 2007],ContextChanged event [InfoPath 2007],Click event [InfoPath 2007],events [InfoPath 2007], adding event handlers,Sign event [InfoPath 2007],ViewSwitched event [InfoPath 2007],event handling [InfoPath 2007],Merge event [InfoPath 2007],Validating event [InfoPath 2007],Submit event [InfoPath 2007],Save event [InfoPath 2007],Loading event [InfoPath 2007]
 
ms.localizationpriority: medium
ms.assetid: d69393fb-fb5a-4edb-abc0-38f5d7e80bcc
description: "This topic describes the procedures for adding event handlers to an Microsoft InfoPath managed code form template using Visual Studio 2012. To add an event handler to a form template, you start with the form template open in the InfoPath Designer, and then select the appropriate user interface command for the event you want to write code for. After you select the command for an event in the InfoPath Designer, the focus automatically switches to the skeleton event handler for that event in the Visual Studio 2012 code editor."
---

# Add an Event Handler

This topic describes the procedures for adding event handlers to an Microsoft InfoPath managed code form template using Visual Studio 2012. To add an event handler to a form template, you start with the form template open in the InfoPath Designer, and then select the appropriate user interface command for the event you want to write code for. After you select the command for an event in the InfoPath Designer, the focus automatically switches to the skeleton event handler for that event in the Visual Studio 2012 code editor.
  
> [!IMPORTANT]
> You should always use the InfoPath Designer user interface to add an event handler. Adding an event handler with the user interface generates event binding code in the **InternalStartup** method of the FormCode.cs or FormCode.vb file in your form template project. You should not create the **InternalStartup** method or add any additional code within it yourself. 
  
### Add an event handler for the Click event of a Button control

1. Open the form template in the InfoPath Designer, and then add a **Button** control to the form. 
    
2. Click the button, and then on the **Properties** tab of the ribbon, click **Custom Code**.
    
    The focus switches to the skeleton event handler for the [Clicked](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ButtonEvent.Clicked.aspx) event in the Visual Studio 2012 code editor. 
    
### Add an event handler for the Changing, Validating, or Changed event of a field or group

1. Open the form template in the InfoPath Designer.
    
2. Right-click a data-entry control bound to the field or group, such as a **Text Box** control. 
    
3. Point to **Programming**, and then click the event you want to create an event handler for. The focus switches to the skeleton event handler for the [Changing](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Changing.aspx) , [Validating](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Validating.aspx) , or [Changed](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlEvent.Changed.aspx) event in the Visual Studio 2012 code editor. 
    
    > [!NOTE]
    > The command to create an event handler for the **Changing** event is not available if the compatibility setting for the form template is set to **Web Browser Form**. This is because the **Changing** event is not supported in the business logic of form templates published to document libraries on Microsoft SharePoint Server 2010 with InfoPath Forms Services. To create an event handler for the **Changing** event, you must change the compatibility setting to **InfoPath Editor** in the InfoPath designer. To do that, click the **File** tab, click **Form Options**, click **Compatibility**, and then set **Form type** to **InfoPath Editor Form**. 
  
### Add an event handler for the Loading, ViewSwitched, ContextChanged, and Sign events of a form

1. Open the form template in the InfoPath Designer.
    
2. On the **Developer** tab of the ribbon, click the form event that you want to write an event handler for. 
    
    The focus switches to the skeleton event handler for the [Loading](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Loading.aspx) , [ViewSwitched](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ViewSwitched.aspx) , [ContextChanged](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ContextChanged.aspx) , or [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event in the Visual Studio 2012 code editor. 
    
    > [!NOTE]
    > The commands to create an event handler for the [ContextChanged](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ContextChanged.aspx) or [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) events are not available if the compatibility setting for the form template is set to **Web Browser Form**. This is because those events are not supported in the business logic of form templates published to document libraries on Microsoft SharePoint Server 2010 with InfoPath Forms Services. To create an event handler for the [ContextChanged](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.ContextChanged.aspx) or [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event, you must change the compatibility setting to **InfoPath Editor Form** in the InfoPath Designer. To do that, click the **File** tab, click **Form Options**, click **Compatibility**, and then set **Form type** to **InfoPath Editor Form**. 
  
### Add an event handler for the Submit event of a form

1. Open the form template in the InfoPath Designer.
    
2. Click the **File** tab, click **Submit To** on the **Info** tab, and then click ** Submit Options **.
    
3. Click **Allow users to submit this form**, click **Perform custom action using Code**, and then click **Edit Code**.
    
    The focus switches to the skeleton event handler for the [Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Submit.aspx) event in the Visual Studio 2012 code editor. 
    
### Add an event handler for the Save event of a form

1. Open the form template in the InfoPath Designer.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. Click the **Save** category, select the **Save using custom code** check box, and then click **Edit**.
    
    The focus switches to the skeleton event handler for the [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Save.aspx) event in the Visual Studio 2012 code editor. 
    
    > [!NOTE]
    > The **Save using custom code** check box is not available if the compatibility setting for the form template is set to **InfoPath Forms Services**. This is because the [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Save.aspx) event is not supported in the business logic of form templates published to document libraries on Microsoft SharePoint Server 2010 with InfoPath Forms Services. To create an event handler for the [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Save.aspx) event, you must change the compatibility setting to **InfoPath Editor Form** in the InfoPath Designer. To do that, click the **File** tab, click **Form Options**, click **Compatibility**, and then set **Form type** to **InfoPath Editor Form**. 
  
### Add an event handler for the VersionUpgrade event of a form

1. Open the form template in the InfoPath Designer.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. Click the **Versioning** category, select **Use custom event** in the **Update existing forms** drop-down box, and then click **Edit**.
    
    The focus switches to the skeleton event handler for the [Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Save.aspx) event in the Visual Studio 2012 code editor. 
    
### Add an event handler for the Merge event of a form

1. Open the form template in the InfoPath Designer.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. Click the **Advanced** category, click the **Enable form merging** check box, click the **Merge using custom code** check box, and then click **Edit**.
    
    The focus switches to the skeleton event handler for the [Merge](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Merge.aspx) event in the Visual Studio 2012 code editor. 
    
    > [!NOTE]
    > The **Enable form merging** check box is not available if the compatibility setting for the form template is set to **InfoPath Forms Services**. This is because the [Merge](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Merge.aspx) event is not supported in the business logic of form templates published to document libraries on Microsoft SharePoint Server 2010 with InfoPath Forms Services. To create an event handler for the [Merge](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Merge.aspx) event, you must change the compatibility setting to **InfoPath Editor Form** in the InfoPath Designer. To do that, click the **File** tab, click **Form Options**, click **Compatibility**, and then set **Form type** to **InfoPath Editor Form**. 
  
## See also



[Walkthrough: Creating a Basic Form Template with Code](walkthrough-creating-a-basic-form-template-with-code.md)

