---
title: "Sample sandboxed solutions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 415fa0fa-b7b7-4acb-a437-f54c34064004
description: This topic provides two examples that show the kind of code that you can write in an InfoPath sandboxed solution, and how to publish the form template.
---

# Sample sandboxed solutions

InfoPath forms with managed code can be published to the SharePoint sandboxed solution infrastructure from the InfoPath Designer. This topic provides two examples that show the kind of code that you can write in an InfoPath sandboxed solution, and how to publish the form template.
  
## Example 1: Sorting data in an order form

A useful task that you can perform by using code in an InfoPath form is to sort data in a repeating table. To do this, the code reorders the nodes in underlying XML document that is displayed in the InfoPath form. Although the scenario described in this topic is targeted for publishing directly from InfoPath as a sandboxed solution, it can also be deployed as an administrator-approved form template.
  
Before you start, make sure that you meet the following requirements.
  
- You are a site collection administrator on the SharePoint Server 2010 or SharePoint Foundation 2010 site where you want to publish the form.
    
- Check with the farm administrator to make sure that the Microsoft SharePoint Foundation Sandboxed Code Service is running on the server. For more information, see [Publishing Forms with Code](publishing-forms-with-code.md).
    
- The programming language that you have selected for the form template is either **C#** or **Visual Basic** without any earlier version name after it. The InfoPath 2007-compatible and InfoPath 2003-compatible versions of the programming languages and object models are not supported for sandboxed solutions. For more information about how to specify the programming language, see [Develop with Visual Studio](how-to-develop-with-visual-studio.md).
    
Perform the following steps to create a form template that sorts the data in a **Repeating Table** control on the form. 
  
### To create a form template that programmatically sorts data in the form

1. Create a new form template in the InfoPath designer, and add a **Repeating Table** control to the form. The sample code for this example sorts the rows based on the first column in the table, but you can easily modify the code to work with any column. 
    
2. Add a **Button** control to the form. The code to sort the table will be added to the event handler for the button's **Clicked** event, but you could also use another event for this purpose. 
    
3. Select the button, click the **Properties** tab, and then click **Custom Code**. If your form hasn't been saved yet, you are prompted to save it, and then the Code Editor will open with the cursor in the button's event handler.
    
4. Paste the following code into the button's event handler. The code puts the elements from the first column into an array, sorts the array, and then reorders the table based on the sorted array. This code assumes that the data being sorted is string data.
    
   ```cs
    // Put the elements from the first column into an array.
    XPathNavigator root = this.CreateNavigator();
        
    // Create a node iterator which contains only the values that you want to sort.
    // For this form, the entire table is in "group1", each row is a "group2"
    // and the rows are "field1", "field2" and "field3" respectively.
    XPathNodeIterator nodeIterator = root.Select(
        "/my:myFields/my:group1/my:group2/my:field1", this.NamespaceManager);
        
    // Create arrays to use for sorting.
    string[] sortArrayWords = new string[nodeIterator.Count + 1];
    int[] sortArrayKeys = new int[nodeIterator.Count + 1];
    int arrayPosition = 1;
        
    // Populate the arrays for sorting.
    while (nodeIterator.MoveNext()) 
    {
        // Loop until there are no more elements
        sortArrayWords[arrayPosition] = nodeIterator.Current.Value;
        sortArrayKeys[arrayPosition] = arrayPosition;
        arrayPosition += 1;
    }
        
    // Sort the array.
    Array.Sort(sortArrayWords, sortArrayKeys);
    arrayPosition = 0;
        
    // Create new XML to update the table.
    string newTableXML = "";
    // Iterate through the sorted array of keys.
    for (int i = 1; i <= sortArrayWords.Length - 1; i++) 
    {
        nodeIterator = root.Select(
            "/my:myFields/my:group1/my:group2", this.NamespaceManager);
            
        // Go to the right position in the table.
        for (int j = 1; j <= sortArrayKeys[i]; j++) 
        {
            nodeIterator.MoveNext();
        }
            
        // Add the row to the XML.
        newTableXML += nodeIterator.Current.OuterXml;
    }
        
    // Set the table to use the new XML.
    root.SelectSingleNode(
        "/my:myFields/my:group1", this.NamespaceManager).InnerXml = newTableXML;
    
   ```

   ```vb
    ' Put the elements from the first column into an array.
    Dim root As XPathNavigator = Me.CreateNavigator
    ' Create a node iterator which contains only the values that you want to sort
    ' For this form, the entire table is in "group1",
    ' each row is a "group2"
    ' and the rows are "field1", "field2" and "field3" respectively.
    Dim nodeIterator As XPathNodeIterator = root.Select( _
        "/my:myFields/my:group1/my:group2/my:field1", Me.NamespaceManager)
    ' Create arrays to use for sorting.
    Dim sortArrayWords(nodeIterator.Count) As String
    Dim sortArrayKeys(nodeIterator.Count) As Integer
    Dim arrayPosition As Integer = 1
    ' Populate the arrays for sorting.
    While nodeIterator.MoveNext() ' Loop until there are no more elements
        sortArrayWords(arrayPosition) = nodeIterator.Current.Value
        sortArrayKeys(arrayPosition) = arrayPosition
        arrayPosition += 1
    End While
    ' Sort the array.
    Array.Sort(sortArrayWords, sortArrayKeys)
    arrayPosition = 0
    ' Create new XML to update the table.
    Dim newTableXML As String = ""
    ' Iterate through the sorted array of keys.
    For i As Integer = 1 To sortArrayWords.Length - 1
        nodeIterator = root.Select( _
            "/my:myFields/my:group1/my:group2", Me.NamespaceManager)
        ' Go to the right position in the table.
        For j As Integer = 1 To sortArrayKeys(i)
        nodeIterator.MoveNext()
        Next
    ' Add the row to the XML.
    newTableXML &amp;= nodeIterator.Current.OuterXml
    Next
    ' Set the table to use the new XML.
    root.SelectSingleNode("/my:myFields/my:group1", _
        Me.NamespaceManager).InnerXml = newTableXML
   ```

5. Publish your form by using the following steps:
    
    1. Click **SharePoint Server** on the **Publish** tab in the Backstage. 
        
    2. Enter the URL of the SharePoint site to publish to, and then click **Next**. 
        
       > [!IMPORTANT]
       > You must be a site collection administrator on this site to publish this form template as a sandboxed solution. 
    
    3. Select **Form Library**, and then click **Next**.
        
    4. Select **Create a new form library**, and then click **Next**.
        
    5. Enter the name and descriptions for your form library, and then click **Next**.
        
    6. Click **Publish**.
    
## Example 2: Managing vendors in a SharePoint list

This example involves programming against the Microsoft SharePoint Foundation 2010 object model. To do that, you must establish a reference to the Microsoft.SharePoint.dll assembly which is installed with a licensed copy of SharePoint Server 2010.
  
Microsoft.SharePoint.Server.dll is installed in C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\ISAPI by default. This DLL must be included in projects where you program against the SharePoint object model. To establish a reference to the Microsoft.SharePoint.dll in a Visual Studio 2012 project, open the **Code Editor**, and then click **Add Reference** on the **Tools** menu. In the **Add Reference** dialog box, click the **Browse** tab, specify the location of the Microsoft.SharePoint.dll file, and then click **OK**. This will copy the Microsoft.SharePoint.dll into the project directory so that you can use SharePoint Foundation 2010 object model members in your InfoPath solution.
  
### Designing the form and developing the code

From code in an InfoPath form, you can use the SharePoint object model to create items in lookup lists. This is useful when you populate a drop-down box from a SharePoint list and want to add new values to it without creating a separate form. This example uses a combo box to show all the values currently in the list and creates programming logic to add the value to the list if it does not already exist.
  
### To create a form template that can add new items to a combo box based on a SharePoint list

1. Create a simple custom list on a SharePoint Server 2010 server, and name it MyList. The following example uses a **Combo Box** bound to the **Title** field of this list. 
    
2. Create a new **Blank Form** in InfoPath Designer, insert a **Combo Box** control on your form, and rename the field bound to the combo box to myCombo.
    
3. Create the data connection to the list that will be used to populate the combo box by using the following steps:
    
    1. On the **Data** tab, click **From SharePoint List** button in the **Get External Data** group. 
        
    2. Enter the URL for the site that contains the list, and then click **Next**.
        
    3. Select the list, and then click **Next**.
        
    4. Select the fields that you want to include, for this example, select Title and ID. Title contains the values for lookup. Click **Next**.
        
    5. Click **Next** on the following screen. 
        
    6. Name the data connection LookupList, and then click **Finish**.
    
4. Populate the values in the combo box from the list by using the following steps:
    
    1. Select the combo box that you created in step 1.
        
    2. Click **Edit Choices** on the **Control Tools Properties** tab of the ribbon. 
        
    3. Select **Get choices from an external data source**.
        
    4. Make sure that **Data source** is set to the data connection that you created in step 2. 
        
    5. Set the value and display name to Title.
        
    6. On the **Browser forms** tab, select **Always** under **Postback settings**, and then click **OK** to close the properties dialog box. 
    
5. Make sure the combo box is still selected, and then click **Changed Event** on the **Developer** tab of the ribbon. 
    
    If your form is not saved yet, you are prompted to save it. And then, the code editor window opens with the cursor in the  `myCombo_Changed` event handler. 
    
6. Add a reference to the Microsoft.SharePoint.dll assembly as described earlier in this topic. For more information about referencing the Microsoft.SharePoint assembly, see [Use SharePoint Object Model Members](how-to-use-sharepoint-object-model-members.md).
    
7. Paste the following code into the  `myCombo_Changed` event handler. 
    
   ```cs
    // Use InfoPath OM's ServerInfo.SharePointSiteUrl property to programmatically
    // specify the site where the form is published.
    using (SPSite FormSite = new SPSite(ServerInfo.SharePointSiteUrl.ToString()))
    {
        using (SPWeb FormWeb = FormSite.OpenWeb())
        {
            // Get the SharePoint list.
            SPList LookupList = FormWeb.Lists["MyList"];
            // Query for the item.
            SPQuery MyQuery = new SPQuery();
            // "Title" is the field (column) to search in the SharePoint list.
            // /my:myFields/my:myCombo is the xpath to the field bound to the Combo Box in the form.
            MyQuery.Query = "<Where><Eq><FieldRef Name='Title' /><Value Type='Text'>" + 
                GetDomValue("/my:myFields/my:myCombo") + "</Value></Eq></Where>";
            SPListItemCollection ReturnedItems = LookupList.GetItems(MyQuery);
            // Add the item to the SharePoint list if no items were returned in the query.
            if (ReturnedItems.Count == 0)
            {
                SPListItem NewItem = LookupList.Items.Add();
                // Set the value of the Title field in the list to the value in Combo Box on the form.
                NewItem["Title"] = GetDomValue("/my:myFields/my:myCombo");
                // Set AllowUnsafeUpdates to 'true' to temporarily allow updates to the database.
                FormWeb.AllowUnsafeUpdates = true;
                NewItem.Update();
                // Set AllowUnsafeUpdates back to 'false' to prevent further updates to the database.
                FormWeb.AllowUnsafeUpdates = false;
            }
        }
    }
   ```

   ```vb
    ' Use InfoPath OM's ServerInfo.SharePointSiteUrl property to specify the site where the form is published.
    Using FormSite As New SPSite(ServerInfo.SharePointSiteUrl.ToString())
        Using FormWeb As SPWeb = FormSite.OpenWeb()
            ' Get the SharePoint list.
            Dim LookupList As SPList = FormWeb.Lists("MyList")
            ' Query for the item.
            Dim MyQuery As New SPQuery()
            ' "Title" is the field (column) to search in the SharePoint list.
            ' my:myFields/my:myCombo is the xpath to the field bound to the Combo Box in the form.
            MyQuery.Query = "<Where><Eq><FieldRef Name='Title' /><Value Type='Text'>" &amp; _
                GetDomValue("/my:myFields/my:myCombo") &amp; "</Value></Eq></Where>"
            Dim ReturnedItems As SPListItemCollection = LookupList.GetItems(MyQuery)
            ' Add the item to the lookup list if no items were returned in the query.
            If ReturnedItems.Count = 0 Then
                Dim NewItem As SPListItem = LookupList.Items.Add()
                ' Set the value of the Title field in the list to the value in Combo Box on the form.
                NewItem("Title") = GetDomValue("/my:myFields/my:myCombo")
                ' Set AllowUnsafeUpdates to 'true' to temporarily allow updates to the database.
                FormWeb.AllowUnsafeUpdates = True
                NewItem.Update()
                ' Set AllowUnsafeUpdates back to 'false' to prevent further updates to the database.
                FormWeb.AllowUnsafeUpdates = False
            End If
        End Using
    End Using
   ```

8. The preceding code example depends on the  `GetDomValue` helper function. Paste the following code for the  `GetDomValue` helper function below the  `myCombo_Changed` event handler function. 
    
   ```cs
    private string GetDomValue(string XpathToGet)
    {
        return this.CreateNavigator().SelectSingleNode(XpathToGet, this.NamespaceManager).Value;
    }
   ```

   ```vb
    Private Function GetDomValue(XpathToGet As String) As String
        Return Me.CreateNavigator().SelectSingleNode(XpathToGet, Me.NamespaceManager).Value
    End Function
   ```

9. Publish your form by using the following steps:
    
    1. Click **SharePoint Server** on the **Publish** tab in the Backstage. 
        
    2. Enter the URL of the SharePoint site to publish to, and then click **Next**. 
        
       > [!IMPORTANT]
       > You must be a site collection administrator on this site to publish this form template as a sandboxed solution. 
    
    3. Select **Form Library**, and then click **Next**.
        
    4. Select **Create a new form library**, and then click **Next**.
        
    5. Enter the name and description for your form library, and then click **Next**.
        
    6. Click **Publish**.
        
    7. After the form is successfully published, open the form from the form library and add a new value into the combo box to test the code. When you exit the myCombo field, the new value will be written to the SharePoint list. 
    

