---
title: "How to Work with Offline Solutions"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- offline solutions [infopath 2007],solutions [InfoPath 2007], offline,InfoPath 2007, offline solutions
 
localization_priority: Normal
ms.assetid: 108f9bd0-c80f-4790-a572-da2f571a7d85
description: "The InfoPath object model provides the MachineOnlineState property of the Application class that enables your form code to check whether the user's computer is connected to the network. By checking the value of MachineOnlineState property, your form code can perform different actions depending on the state of the connection."
---

# How to: Work with Offline Solutions

The InfoPath object model provides the [MachineOnlineState](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.MachineOnlineState.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.aspx) class that enables your form code to check whether the user's computer is connected to the network. By checking the value of **MachineOnlineState** property, your form code can perform different actions depending on the state of the connection. 
  
## Using the MachineOnlineState Property

The following example shows how you can add logic to your form code that determines how to submit a form based on whether the user's computer is online or offline.
  
This example assumes that you have created a form for submitting a sales report that contains a field named period that specifies the month and year covered in the report. It also assumes that you have already defined a data connection and the logic for submitting the report when the user is online. 
  
### Add a data connection that submits the form as an attachment to an e-mail message

1. Create an InfoPath form template using the **Blank (InfoPath Editor)** template. 
    
2. In InfoPath design mode, click **Data Connections** on the **Data** tab. 
    
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
    
9. On the next page of the wizard, click the **Formula** button next to the **Attachment Name** box, and then repeat the steps above to create the formula concat("Sales Report - ", period), and then click **Next**.
    
10. On the last page of the wizard, type E-mail Submit in the **Enter a name for this data connection** box, and then click **Finish**.
    
### Add logic for submitting the form depending on the connected state of a user's computer

1. In InfoPath design mode, click **Submit Options** on the **Data** tab. 
    
2. In the **Submit Options** dialog box, click **Allow users to submit this form**, select **Perform custom action using Code**, click **Edit Code**.
    
3. Add the following two functions below the [Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Submit.aspx) event handler: 
    
  ```cs
  public void OnlineSubmit(SubmitEventArgs e)
  {
     // Logic for submitting online goes here.
  }
  public void OfflineSubmit(SubmitEventArgs e)
  {
     // Access and submit to the e-mail connection.
     DataConnectionCollection myDataConnections =
        this.DataConnections;
     EmailSubmitConnection submitConnection =
        (EmailSubmitConnection)myDataConnections["E-mail Submit"];
     submitConnection.Execute();
     // Notify the user that the form was submitted offline.
     System.Text.StringBuilder myMessage = 
        new System.Text.StringBuilder();
     myMessage.Append("You submitted your Sales Report offline. ");
     myMessage.Append("Your Sales Report is in your outbox ");
     myMessage.Append("and will be submitted when you connect to ");
     myMessage.Append("the network.");
      MessageBox.Show(myMessage.ToString());
     // The submission was successful.
     e.CancelableArgs.Cancel = false;
  }
  ```

  ```VB.net
  Public Sub OnlineSubmit(ByVal e As SubmitEventArgs)
     ' Logic for submitting online goes here.
  End Sub
  Public Sub OfflineSubmit(ByVal e As SubmitEventArgs)
     ' Access and submit to the e-mail connection.
     Dim myDataConnections As DataConnectionCollection = _
        Me.DataConnections
     Dim submitConnection As EmailSubmitConnection = _
        DirectCast(myDataConnections("E-mail Submit"), _
        EmailSubmitConnection)
     submitConnection.Execute
     ' Notify the user that the form was submitted offline.
     Dim myMessage As System.Text.StringBuilder = _
        New System.Text.StringBuilder()
     myMessage.Append("You submitted your Sales Report offline. ")
     myMessage.Append("Your Sales Report is in your outbox ")
     myMessage.Append("and will be submitted when you connect to ")
     myMessage.Append("the network.")
      MessageBox.Show(myMessage.ToString())
     ' The submission was successful.
     e.CancelableArgs.Cancel = False
  End Sub
  ```

4. Add the following **if** statement to the [Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Submit.aspx) event handler function. 
    
  ```cs
  // Check the computer's connection state.
  if (this.Application.MachineOnlineState == MachineState.Online)
  {
     OnlineSubmit(e);
  }
  else
  {
     OfflineSubmit(e);
  }
  ```

  ```VB.net
  ' Check the computer's connection state.
  If (Me.Application.MachineOnlineState = MachineState.Online) Then
     OnlineSubmit(e)
  Else
  {
     OfflineSubmit(e)
  End If
  ```

### Test the code

1. On the **Debug** menu, click **Start Debugging**.
    
2. Fill out the form.
    
3. Start Microsoft Internet Explorer.
    
4. In Internet Explorer, click **Work offline** on the **File** menu. 
    
5. In InfoPath, click **Submit**. You should see a message that the form will be submitted as an e-mail message.
    
6. Click **Send**. You should see a message stating that the form has been submitted offline and will be submitted when you connect to the network.
    
## See also

#### Other resources

[Design a form template for offline use](http://office.microsoft.com/en-us/infopath/HA102117391033.aspx?pid=CH100341121033)

