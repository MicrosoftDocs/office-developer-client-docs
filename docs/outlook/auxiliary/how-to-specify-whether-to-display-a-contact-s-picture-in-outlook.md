---
title: "code similar to the code sample in this topic to achieve the same in your managed Outlook solution.'"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 0c518245-2c52-435d-98ad-ffad72a4527b
description: "This topic shows how to use the dispidShowSenderPhoto dispatch ID to invoke the corresponding method on a Microsoft Outlook Explorer or Inspector object, to specify whether to display a contact's picture in the explorer or inspector window, according to a Boolean argument. Specifying true as the argument turns on the display, and false turns off the display. Note that the solution does not require the Outlook object model, but nonetheless, you can use C# code similar to the code sample in this topic to achieve the same in your managed Outlook solution."
---

# How to: Specify Whether to Display a Contact's Picture in Outlook

This topic shows how to use the **dispidShowSenderPhoto** dispatch ID to invoke the corresponding method on a Microsoft Outlook [Explorer](http://msdn.microsoft.com/library/026591e5-049f-503a-4166-34e6dbc225fb%28Office.15%29.aspx) or [Inspector](http://msdn.microsoft.com/library/d7384756-669c-0549-1032-c3b864187994%28Office.15%29.aspx) object, to specify whether to display a contact's picture in the explorer or inspector window, according to a Boolean argument. Specifying **true** as the argument turns on the display, and **false** turns off the display. Note that the solution does not require the Outlook object model, but nonetheless, you can use C# code similar to the code sample in this topic to achieve the same in your managed Outlook solution. 
  
Given a pointer to an **Explorer** or **Inspector** object, you can use the [Object.GetType()](https://msdn.microsoft.com/library/System.Object.GetType.aspx) method to obtain a [System.Type](https://msdn.microsoft.com/library/System.Type.aspx) object. 
  
The function in this topic,  `SetSenderContactPhoto`, accepts two input parameters:
  
-  _Inspector_—An **InspectorPtr** object. 
    
-  _ShowSenderContactPhoto_—A Boolean value that specifies whether to display contacts' pictures.
    
 `SetSenderContactPhoto` constructs the string representation of the **dispidShowSenderPhoto** dispatch ID as  `dispidShowSenderPhotoMemberName`.  `SetSenderContactPhoto` then calls the [Type.InvokeMember](https://msdn.microsoft.com/library/System.Type.InvokeMember.aspx) method—specifying **dispidShowSenderPhoto** as the argument for the  _name_ parameter and the flag  `System.Reflection.BindingFlags.InvokeMethod` as the argument for  _invokeAttr_, and using  _ShowSenderContactPhoto_ to form the argument for the  _args_ parameter—to turn on or off the display in an inspector according to the value of  _ShowSenderContactPhoto_.
  
```cs
void SetSenderContactPhoto(object Inspector, bool ShowSenderContactPhoto)
{
    Type typeInspector = Inspector.GetType();
    string dispidShowSenderPhotoMemberName = String.Format("[DispID={0}]", 0xF0D0);
    object[] args = {ShowSenderContactPhoto};
    try
    {
        typeInspector.InvokeMember(dispidShowSenderPhotoMemberName, 
            System.Reflection.BindingFlags.InvokeMethod,
            null,
            Inspector,
            args);
    }
    catch(System.Runtime.InteropServices.COMException comEx)
    {
    }
}

```

This setting does not persist across Outlook sessions and does not carry from one inspector or explorer to another. The default setting is to turn on the display. This means that if a picture is present, it is displayed. However, if no picture is present, no placeholder picture is displayed.
  
This setting works in conjunction with the  `TurnOffPhotograph` policy key as well as the older  `ShowContactPicture` registry key. The  `TurnOffPhotograph` policy key was introduced in Microsoft Outlook 2010, and  `ShowContactPicture` registry key was introduced in Microsoft Office Outlook 2007. The following table shows how these registry keys and **dispidShowSenderPhoto** interact. This setting does not turn on the display if administrator policy (  `TurnOffPhotograph` policy key) or user preference (  `ShowContactPicture` registry key) turns off the display. For more information about the  `TurnOffPhotograph` policy key, see [How to manage the Outlook Social Connector by using Group Policy](http://support.microsoft.com/kb/2020103). For more information about the  `ShowContactPicture` registry key, see [Deploying additional registry values in the Office Customization Tool for Outlook 2007](http://technet.microsoft.com/en-us/library/cc837949%28office.12%29.aspx).
  
|**Argument for method represented by **dispidShowSenderPhoto****|**`TurnOffPhotograph` policy key**|**`ShowContactPicture` registry key**|**Is picture displayed if present?**|
|:-----|:-----|:-----|:-----|
|True  <br/> |0 or not set  <br/> |1 or not set  <br/> |Yes  <br/> |
|True  <br/> |0 or not set  <br/> |0  <br/> |No  <br/> |
|True  <br/> |1  <br/> |1 or not set  <br/> |No  <br/> |
|True  <br/> |1  <br/> |0  <br/> |No  <br/> |
|False  <br/> |0 or not set  <br/> |1 or not set  <br/> |No  <br/> |
|False  <br/> |0 or not set  <br/> |0  <br/> |No  <br/> |
|False  <br/> |1  <br/> |1 or not set  <br/> |No  <br/> |
|False  <br/> |1  <br/> |0  <br/> |No  <br/> |
   
## See also

#### Concepts

[How to: Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)](how-to-specify-whether-to-display-a-contact-s-picture-in-outlook-outlook-auxilia.md)

