﻿---
title: Version Property Example (VJ++)
TOCTitle: Version Property Example (VJ++)
ms:assetid: c4f007b8-177d-967e-7f3b-a8945264099b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249963(v=office.15)
ms:contentKeyID: 48547600
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Version Property Example (VJ++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Version](version-property-ado.md) property of a [Connection](connection-object-ado.md) object to display the current ADO version. It also uses several dynamic properties to show:

  - the current DBMS name and version.

  - OLE DB version.

  - provider name and version.

  - ODBC version.

  - ODBC driver name and version.

<!-- end list -->

``` 
 
// BeginVersionJ 
import com.ms.wfc.data.*; 
import java.io.*; 
 
public class VersionX 
{ 
 // The main entry point of the application. 
 public static void main (String[] args) 
 { 
 VersionX(); 
 System.exit(0); 
 } 
 // VersionX Function 
 static void VersionX() 
 { 
 // Define ADO Objects. 
 Connection cnn1 = null; 
 
 // Declarations. 
 String strCnn = "Driver={SQL Server};Server='MySqlServer';" + 
 "User ID='MyUserID';Password='MyPassword';database='Pubs';"; 
 String strVersionInfo; 
 BufferedReader in = new 
 BufferedReader(new InputStreamReader(System.in)); 
 try 
 { 
 // Open connection. 
 cnn1 = new Connection(); 
 cnn1.open(strCnn); 
 
 strVersionInfo = "\tADO Version:\t\t" + 
 cnn1.getVersion().toString()+"\n"+ 
 "\tDBMS Name:\t\t" + 
 cnn1.getProperties().getItem("DBMS Name").getString() +"\n"+ 
 "\tDBMS Version:\t\t"+ 
 cnn1.getProperties().getItem("DBMS Version").getString() + 
 "\n" + "\tOLE DB Version:\t\t" + 
 cnn1.getProperties().getItem("OLE DB Version").getString()+ 
 "\n" + "\tProvider Name:\t\t" + 
 cnn1.getProperties().getItem("Provider Name").getString() + 
 "\n" + "\tProvider Version:\t" + 
 cnn1.getProperties().getItem("Provider Version"). 
 getString() + "\n" + "\tDriver Name:\t\t" + 
 cnn1.getProperties().getItem("Driver Name").getString() + 
 "\n" + "\tDriver Version:\t\t" + 
 cnn1.getProperties().getItem("Driver Version").getString()+ 
 "\n" + "\tDriver ODBC Version:\t" + 
 cnn1.getProperties().getItem( 
 "Driver ODBC Version").getString()+ "\n"; 
 System.out.println("\n\n" + strVersionInfo); 
 
 System.out.println("Press <Enter> to continue.."); 
 in.readLine(); 
 } 
 // System read requires this catch. 
 catch(java.io.IOException je) 
 { 
 PrintIOError(je); 
 } 
 catch(AdoException ae) 
 { 
 // Notify the user of any errors that result from ADO. 
 
 // As passing a recordset, check for null pointer first. 
 if(cnn1!= null) 
 { 
 PrintProviderError(cnn1); 
 } 
 else 
 { 
 System.out.println("Exception: " + ae.getMessage()); 
 } 
 } 
 finally 
 { 
 // Cleanup objects before exit. 
 if (cnn1 != null) 
 if (cnn1.getState() == 1) 
 cnn1.close(); 
 } 
 
 } 
 // PrintProviderError Function 
 static void PrintProviderError(Connection cnn1) 
 { 
 // Print Provider Errors from Connection Object. 
 // ErrItem is an item object in the Connections Errors Collection. 
 com.ms.wfc.data.Error ErrItem = null; 
 long nCount = 0; 
 int i = 0; 
 
 nCount = cnn1.getErrors().getCount(); 
 
 // If there are any errors in the collection, print them. 
 if ( nCount > 0) 
 { 
 // Collection ranges from 0 to nCount-1. 
 for ( i=0;i<nCount; i++) 
 { 
 ErrItem = cnn1.getErrors().getItem(i); 
 System.out.println("\t Error Number: " + ErrItem.getNumber() 
 + "\t" + ErrItem.getDescription()); 
 } 
 } 
 } 
 // PrintIOError Function 
 static void PrintIOError(java.io.IOException je) 
 { 
 System.out.println("Error: \n"); 
 System.out.println("\t Source: " + je.getClass() + "\n"); 
 System.out.println("\t Description: "+ je.getMessage() + "\n"); 
 } 
} 
// EndVersionJ 
```

