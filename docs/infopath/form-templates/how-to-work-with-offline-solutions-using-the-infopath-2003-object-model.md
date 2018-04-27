---
title: "How to Work with Offline Solutions Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- solutions [infopath 2007], offline,offline solutions [InfoPath 2007], InfoPath 2003-compatible form templates,InfoPath 2003-compatible form templates, offline solutions
 
localization_priority: Normal
ms.assetid: 634ccd8c-0b5f-4161-875c-0e546a517377
description: "The InfoPath 2003-compatible object model provides the MachineOnlineState property of the Application object which enables your form code to check whether the user's computer is connected to the network. Your form code can perform different actions depending on the state of the connection."
---

# How to: Work with Offline Solutions Using the InfoPath 2003 Object Model

The InfoPath 2003-compatible object model provides the [MachineOnlineState](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.MachineOnlineState.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) object which enables your form code to check whether the user's computer is connected to the network. Your form code can perform different actions depending on the state of the connection. 
  
## Using the MachineOnlineState Property

The following example shows how you can add logic to your form code that determines how to submit a form based on whether the user's computer is online or offline.
  
This example assumes that you have created a form for submitting a sales report that contains a field named "period" that specifies the month and year covered in the report. It also assumes that you have already defined a data connection and the logic for submitting the report when the user is online.
  
### Add a data connection that submits the form as an attachment to an e-mail message

1. Create or open an InfoPath managed-code form template.
    
2. In InfoPath design mode, on the **Data** tab, click **Data Connections**.
    
3. In the **Data Connections** dialog box, click **Add**.
    
4. In the **Data Connection Wizard**, click **Submit data**, and then click **Next**.
    
5. On the next page of the wizard, click **As an e-mail message**, and then click **Next**.
    
6. On the next page of the wizard, type your e-mail address in the **To** box. 
    
7. In the **Subject** box, do the following to combine the sales period with the text Sales Report: 
    
1. Click the **Formula** button next to the **Subject** box. 
    
2. In the **Insert Formula** dialog box, click **Insert Function**.
    
3. In the **Insert Function** dialog box, click **Text** in the **Categories** list, and then double-click **concat** in the **Functions** list. 
    
4. Replace the first instance of **double click to insert field** with the following (include the single quotes): 'Sales Report: ' 
    
5. Double-click the second instance of **double click to insert field**.
    
6. In the **Select a Field or Group** dialog box, select the period field. 
    
7. Delete the final instance of **double click to insert field**, and then click **OK**.
    
8. In the wizard, click **Next**.
    
9. On the next page of the wizard, type 'E-mail Submit' in the **Enter a name for this data connection** box, and then click **Finish**.
    
### Add logic for submitting the form depending on the connected state of a user's computer

1. In InfoPath design mode, on the **Data** tab, click **Submit Options**.
    
2. In the **Submit Options** dialog box, click **Allow users to submit this form**, and then select **Perform custom action using Code**.
    
3. Click the **Edit Code** button. 
    
4. Add the following two functions below the [OnSubmitRequest](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2_Event.OnSubmitRequest.aspx) event handler: 
    
  ```cs
  public void OnlineSubmit(DocReturnEvent e)
  {
     // Logic for submitting online goes here.
  }
  public void OfflineSubmitX(DocReturnEvent e)
  {
     // Access and submit to the e-mail adapter.
     DataAdaptersCollection myDataAdapters = 
        thisXDocument.DataAdapters;
     EmailAdapterObject submitAdapter = 
        (EmailAdapterObject) myDataAdapters["E-mail Submit"];
     submitAdapter.Submit();
     // Notify the user that the form was submitted offline.
     System.Text.StringBuilder message = 
     new System.Text.StringBuilder();
     message.Append("You submitted your Sales Report offline. ");
     message.Append("Your Sales Report is in your outbox ");
     message.Append("and will be submitted when you connect to ");
     message.Append("the network.");
      thisXDocument.UI.Alert(message.ToString());
     // The submission was successful.
     e.ReturnStatus = true;
  }
  ```

5. Add the following **if** statement to the **OnSubmitRequest** event handler function. 
    
  ```cs
  // Check the computer's connection state.
  if (thisApplication.MachineOnlineState==XdMachineOnlineState.xdOnline)
  {
      OnlineSubmit(e);
  }
  else
  {
      OfflineSubmit(e);
  }
  ```

### Test the code

1. In the InfoPath designer, click **Preview** on the **Home** tab. 
    
2. Fill out the form.
    
3. Start Microsoft Internet Explorer.
    
4. In Internet Explorer, click **Work offline** on the **File** menu. 
    
5. In InfoPath, click **Submit**. You should see a message that the form will be submitted as an e-mail message.
    
6. Click **Send**. You should see a message stating that the form has been submitted offline.
    

