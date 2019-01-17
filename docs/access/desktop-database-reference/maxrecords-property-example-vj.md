---
title: MaxRecords property example (VJ++)
TOCTitle: MaxRecords property example (VJ++)
ms:assetid: db8c1187-5e15-2c8a-6308-3468c113d962
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250107(v=office.15)
ms:contentKeyID: 48548106
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# MaxRecords property example (VJ++)


**Applies to**: Access 2013, Office 2013

This example uses the [MaxRecords](maxrecords-property-ado.md) property to open a [Recordset](recordset-object-ado.md) containing the 10 most expensive titles in the ***Titles*** table.

```java 
 
// BeingMaxRecordsJ 
import java.io.*; 
import com.ms.wfc.data.*; 
 
public class MaxRecordsX 
{ 
 // The main entry point for the application. 
 
 public static void main (String[] args) 
 { 
 MaxRecordsX(); 
 System.exit(0); 
 } 
 // MaxRecordsX Function 
 
 static void MaxRecordsX() 
 { 
 // Define ADO Objects 
 Recordset rstTemp = null; 
 
 try 
 { 
 // Declarations 
 BufferedReader in = 
 new BufferedReader(new InputStreamReader(System.in)); 
 
 // Open recordset containing the 10 most expensive 
 // titles in the Titles table. 
 String strCnn = " Provider='sqloledb';Data Source='MySqlServer';"+ 
 " Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 rstTemp = new Recordset(); 
 rstTemp.setMaxRecords(10); 
 rstTemp.open("select title,price from Titles" + 
 " order by price desc", strCnn,AdoEnums.CursorType.FORWARDONLY, 
 AdoEnums.LockType.READONLY, AdoEnums.CommandType.TEXT); 
 
 // Display the contents of the recordset. 
 System.out.println("Top Ten Titles by Price:\n"); 
 while (!rstTemp.getEOF()) 
 { 
 System.out.println(" "+ rstTemp.getField("title").getString() + 
 " - " + rstTemp.getField("Price").getString()); 
 rstTemp.moveNext(); 
 } 
 
 System.out.println("\n\nPress <Enter> to continue.."); 
 in.readLine(); 
 } 
 
 catch(AdoException ae) 
 { 
 // Notify the user of any errors that result from ADO. 
 
 // As passing a connection, check for null pointer first. 
 if (rstTemp!=null) 
 { 
 PrintProviderError(rstTemp.getActiveConnection()); 
 } 
 else 
 { 
 System.out.println("Exception: " + ae.getLocalizedMessage()); 
 } 
 } 
 
 // System read requires this catch. 
 catch(java.io.IOException je) 
 { 
 PrintIOError(je); 
 } 
 
 finally 
 { 
 // Cleanup objects before exit. 
 if (rstTemp != null) 
 if (rstTemp.getState() == 1) 
 rstTemp.close(); 
 } 
} 
 // PrintProviderError Function 
 
 static void PrintProviderError( Connection Cnn1 ) 
 { 
 // Print Provider errors from Connection object. 
 // ErrItem is an item object in the Connections Errors collection. 
 com.ms.wfc.data.Error ErrItem = null; 
 long nCount = 0; 
 int i = 0; 
 
 nCount = Cnn1.getErrors().getCount(); 
 
 // If there are any errors in the collection, print them. 
 if( nCount > 0); 
 { 
 // Collection ranges from 0 to nCount - 1 
 for (i = 0; i< nCount; i++) 
 { 
 ErrItem = Cnn1.getErrors().getItem(i); 
 System.out.println("\t Error number: " + ErrItem.getNumber() 
 + "\t" + ErrItem.getDescription() ); 
 } 
 } 
 
 } 
 
 // PrintIOError Function 
 
 static void PrintIOError( java.io.IOException je) 
 { 
 System.out.println("Error \n"); 
 System.out.println("\tSource = " + je.getClass() + "\n"); 
 System.out.println("\tDescription = " + je.getMessage() + "\n"); 
 } 
} 
// EndMaxRecordsJ 
```

