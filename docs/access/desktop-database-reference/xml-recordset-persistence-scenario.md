---
title: XML Recordset persistence scenario
TOCTitle: XML Recordset persistence scenario
ms:assetid: 08f464da-10ba-b649-7571-766a40da2e04
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248825(v=office.15)
ms:contentKeyID: 48543107
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# XML Recordset persistence scenario

**Applies to**: Access 2013, Office 2013

In this scenario, you will create an Active Server Pages (ASP) application that saves the contents of a **Recordset** object directly to the ASP **Response** object.

> [!NOTE]
> This scenario requires that your server have Internet Information Server 5.0 (IIS) or later installed.

The returned **Recordset** is displayed in Internet Explorer using an [RDS.DataControl](datacontrol-object-rds.md).

The following steps are necessary to create this scenario:

1.  Set up the application.
2.  Get the data.
3.  Send the data.
4.  Receive and display the data.

## Step 1: Set up the application

1. Create an IIS virtual directory named **XMLPersist** with script permissions. 

2. Create two new text files in the folder to which the virtual directory points, one named **XMLResponse.asp**, and the other named **Default.htm**.


## Step 2: Get the data

In this step, you will write the code to open an ADO **Recordset** and prepare to send it to the client. 

1. Open the file XMLResponse.asp with a text editor, such as Windows Notepad, and insert the following code:

   ```vb 
        
        <%@ language="VBScript" %> 
        
        <!-- #include file='adovbs.inc' --> 
        
        <% 
        Dim strSQL, strCon 
        Dim adoRec  
        Dim adoCon  
        Dim xmlDoc  
        
        ' You will need to change "slqServer" below to the name of the SQL  
        ' server machine to which you want to connect. 
        strCon = "Provider=sqloledb;Data Source=sqlServer;Initial Catalog=Pubs;Integrated Security=SSPI;" 
        Set adoCon = server.createObject("ADODB.Connection") 
        adoCon.Open strCon 
        
        strSQL = "SELECT Title, Price FROM Titles ORDER BY Price" 
        Set adoRec = Server.CreateObject("ADODB.Recordset") 
        adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText 
   ```

2. Be sure to change the value of the Data Source parameter in strCon to the name of your Microsoft SQL Server computer.

3. Keep the file open and go on to the next step.

## Step 3: Send the data

Now that you have a **Recordset**, you need to send it to the client by saving it as XML to the ASP **Response** object. 

1. Add the following code to the bottom of XMLResponse.asp:

   ```vb 
    
    Response.ContentType = "text/xml" 
    Response.Expires = 0 
    Response.Buffer = False 
    
    
    Response.Write "<?xml version='1.0'?>" & vbNewLine 
    adoRec.save Response, adPersistXML 
    adoRec.Close 
    Set adoRec=Nothing 
    %> 
   ```

   Notice that the ASP **Response** object is specified as the destination for the **Recordset** [Save](save-method-ado.md) method. The destination of the **Save** method can be any object that supports the **IStream** interface, such as an ADO [Stream](stream-object-ado.md) object, or a file name that includes the complete path to which the **Recordset** is to be saved.

2. Save and close XMLResponse.asp before going to the next step. Also copy the adovbs.inc file from C:\\Program Files\\Common Files\\System\\Ado folder to the same folder where you have the XMLResponse.asp file.

## Step 4: Receive and display the data

In this step, you will create an HTML file with an embedded [RDS.DataControl](datacontrol-object-rds.md) object that points at the XMLResponse.asp file to get the **Recordset**. 

1. Open default.htm with a text editor, such as Windows Notepad, and add the following code. Replace "sqlserver" in the URL with the name of your server computer.

   ```html 
    
    <HTML> 
    <HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD> 
    <BODY> 
    
    <TABLE DATASRC="#RDC1" border="1"> 
    <TR> 
    <TD><SPAN DATAFLD="title"></SPAN></TD> 
    <TD><SPAN DATAFLD="price"></SPAN></TD> 
    </TR> 
    </TABLE> 

    <OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1"> 
    <PARAM NAME="URL" VALUE="XMLResponse.asp"> 
    </OBJECT> 
    
    </BODY> 
    </HTML> 
   ```

2. Close the default.htm file and save it to the same folder where you saved XMLResponse.asp. 

3. Using Internet Explorer 4.0 or later, open the URL `https://<sqlserver>/XMLPersist/default.htm` and observe the results. The data is displayed in a bound DHTML table. 

4. Now open the URL `https://<sqlserver>/XMLPersist/XMLResponse.asp` and observe the results. The XML is displayed.




