---
title: "Troubleshoot form templates that use the InfoPath object model at design time"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
keywords:
- infopath 2003-compatible form templates, troubleshooting at design time,troubleshooting form templates [InfoPath 2007], design time
localization_priority: Normal
ms.assetid: 4179b235-e21d-4c37-ae2b-ad01388296ec
description: "The following sections describe common troubleshooting scenarios you may encounter while designing and debugging managed code form templates that use the InfoPath 2003-compatible object model provided by the Microsoft.Office.Interop.InfoPath.SemiTrust namespace."
---

# Troubleshoot form templates that use the InfoPath object model at design time

The following sections describe common troubleshooting scenarios you may encounter while designing and debugging managed code form templates that use the InfoPath 2003-compatible object model provided by the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace. 
  
## Cannot Preview or Debug Form Templates That Use Calls to Object Model Security Level 3 Methods and Properties

If you attempt to debug or preview a managed-code project that contains code that invokes object model members that require full trust, InfoPath will display the error message "An unhandled security exception has occurred in the form's code" and the form will not open. To allow business logic in the form template to be debugged or previewed, you must set the security level to **Full Trust** and digitally sign the form template. For details on how to do this, see [Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md).
  
## Cannot Update XPath Expressions in Event Handlers If the MatchPath Parameter Value Was Deleted Manually

If you add an event handler to a field or group and later change the schema of the data source in the InfoPath **Fields** task pane in a way that affects that field or group (for example, by renaming or moving it), a message will be displayed asking if you want to update the XPath expressions in your form's code. The XPath expressions referred to in this message are the values specified in the [MatchPath](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.InfoPathEventHandlerAttribute.MatchPath.aspx) parameter of the [InfoPathEventHandlerAttribute](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.InfoPathEventHandlerAttribute.aspx) attribute, which are used to associate the event handler with a field or group in your form's data source. No other XPath expressions in your code will be updated. The algorithm for updating the XPath expressions depends on a value being present in the **MatchPath** parameter of the **InfoPathEventHandler** attributes that are applied in your form code. If you manually deleted these values before responding to the prompt to update XPath expressions, InfoPath will not be able to update the XPath expressions automatically. For more information, see [Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md).
  
## Cannot Call Members of the InfoPath 2003 Compatible Object Model on a Separate Thread

The InfoPath 2003-compatible object model does not support calls on a separate thread. For example, the following code, which calls a function named LaunchOMFunction that calls members of the InfoPath object model, will not run. 
  
```cs
Thread th = new Thread(new ThreadStart(LaunchOMFunction));
th.Start();
```

When necessary, there is a way to work around this limitation. For information, see [Threading Support in InfoPath Projects Using the InfoPath 2003 Object Model](threading-support-in-infopath-projects-using-the-infopath-2003-object-model.md).
  
## Omitting Optional Parameters Causes a Build Error in Visual Basic and Visual C#

If an InfoPath object model member contains an optional parameter, and you do not specify a value for that parameter, you must pass the **Type.Missing** field for that parameter instead. Failure to pass the **Type.Missing** field when an actual value is omitted will result in a build error. This is true for code written in both Visual Basic and Visual C#. For more information and examples see the "Passing Optional Parameters to InfoPath Object Model Members" section in the [InfoPath 2003 Compatible Object Models](infopath-2003-compatible-object-models.md) topic. 
  
## See also



[About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)
  
[Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md)
  
[Handle Errors Using the InfoPath 2003 Object Model](how-to-handle-errors-using-the-infopath-2003-object-model.md)
  
[Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md)
  
[Debug InfoPath Projects Using the InfoPath 2003 Object Model](how-to-debug-infopath-projects-using-the-infopath-2003-object-model.md)

