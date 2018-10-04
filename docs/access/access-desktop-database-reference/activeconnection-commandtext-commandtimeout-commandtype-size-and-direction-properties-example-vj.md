﻿---
title: ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VJ++)
TOCTitle: ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VJ++)
ms:assetid: 80e69c20-4bad-c036-3b41-cec9d19e37dd
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249550(v=office.15)
ms:contentKeyID: 48545936
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VJ++)


**Applies to**: Access 2013 | Office 2013

This example uses the [ActiveConnection](activeconnection-property-ado.md), [CommandText](commandtext-property-ado.md), [CommandTimeout](commandtimeout-property-ado.md), [CommandType](commandtype-property-ado.md), [Size](size-property-ado.md), and [Direction](direction-property-ado.md) properties to execute a stored procedure.

``` 
 
// BeginActiveConnectionJ 
import com.ms.wfc.data.*; 
import java.io.*; 
 
public class ActiveConnectionX 
{ 
 // The main entry point for the application. 
 
 public static void main (String[] args) 
 { 
 ActiveConnectionX(); 
 System.exit(0); 
 } 
 
 //.ActiveConnectionX function 
 
 static void ActiveConnectionX() 
 { 
 // Define ADO Objects. 
 Connection cnConn1 = null; 
 Command cmdByRoyalty = null; 
 Parameter prmByRoyalty = null; 
 Recordset rstByRoyalty = null; 
 Recordset rstAuthors = null; 
 
 //Declarations. 
 String strCnn; 
 String strAuthorID; 
 String strFName; 
 String strLName; 
 int intRoyalty ; 
 BufferedReader in = new BufferedReader 
 (new InputStreamReader (System.in)); 
 String line = null; 
 
 try 
 { 
 // Open a connection. 
 
 strCnn = "Provider='sqloledb';Data Source='MySqlServer';" 
 + "Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 cnConn1 = new Connection(); 
 cnConn1.open(strCnn,"","",AdoEnums.CommandType.UNSPECIFIED); 
 
 // Define a command object for stored procedure. 
 cmdByRoyalty = new Command(); 
 cmdByRoyalty.setActiveConnection(cnConn1); 
 cmdByRoyalty.setCommandText("byRoyalty"); 
 cmdByRoyalty.setCommandType(AdoEnums.CommandType.STOREDPROC); 
 cmdByRoyalty.setCommandTimeout(15); 
 
 //Define the stored procedure's input parameter. 
 System.out.println ("\nEnter Royalty : "); 
 line = in.readLine().trim(); 
 intRoyalty = Integer.parseInt(line); 
 prmByRoyalty = new Parameter (); 
 prmByRoyalty.setType(AdoEnums.DataType.INTEGER); 
 prmByRoyalty.setSize(3); 
 prmByRoyalty.setDirection(AdoEnums.ParameterDirection.INPUT); 
 prmByRoyalty.setValue(new Integer(intRoyalty)); 
 cmdByRoyalty.getParameters().append(prmByRoyalty); 
 
 // Create a recordset by executing the command. 
 
 rstByRoyalty = cmdByRoyalty.execute(); 
 
 // Open the Authors table to get author names for display. 
 rstAuthors = new Recordset (); 
 rstAuthors.open("authors",strCnn, 
 AdoEnums.CursorType.FORWARDONLY, 
 AdoEnums.LockType.READONLY ,AdoEnums.CommandType.TABLE ); 
 
 // Print current data in the recordset, 
 // adding author names from Authors table. 
 System.out.println("\nAuthors with " + intRoyalty + 
 " percent royalty"); 
 while (!rstByRoyalty.getEOF()) 
 { 
 strAuthorID = rstByRoyalty.getField("au_id").getString(); 
 rstAuthors.setFilter("au_id ='" + strAuthorID + "'"); 
 strFName = rstAuthors.getField("au_fname").getString(); 
 strLName = rstAuthors.getField("au_lname").getString(); 
 System.out.println("\t" + strAuthorID + ", " + strFName 
 + " " + strLName); 
 rstByRoyalty.moveNext(); 
 } 
 System.out.println("\n\nPress <Enter> key to continue."); 
 line = in.readLine(); 
 
 //Cleanup objects before exit. 
 rstByRoyalty.close(); 
 rstAuthors.close(); 
 cnConn1.close(); 
 
 } 
 catch( AdoException ae ) 
 { 
 // Notify user of any errors that result from ADO. 
 
 // Check for null pointer for connection object 
 if(rstByRoyalty.getActiveConnection()==null) 
 System.out.println("Exception: " + ae.getMessage()); 
 if(rstAuthors.getActiveConnection()==null) 
 System.out.println("Exception: " + ae.getMessage()); 
 // As passing a Recordset, check for null pointer first. 
 if (rstByRoyalty != null) 
 { 
 PrintProviderError(rstByRoyalty.getActiveConnection()); 
 } 
 if (rstAuthors != null) 
 { 
 PrintProviderError(rstAuthors.getActiveConnection()); 
 } 
 else 
 { 
 System.out.println("Exception: " + ae.getMessage()); 
 } 
 } 
 
 // This catch is required if input string cannot be converted to 
 // Integer data type. 
 catch ( java.lang.NumberFormatException ne) 
 { 
 System.out.println("\nException: Integer Input required."); 
 } 
 // System Read requires this catch. 
 catch( java.io.IOException je ) 
 { 
 PrintIOError(je); 
 } 
 finally 
 { 
 // Cleanup objects before exit. 
 if (rstByRoyalty != null) 
 if (rstByRoyalty.getState() == 1) 
 rstByRoyalty.close(); 
 if (rstAuthors != null) 
 if (rstAuthors.getState() == 1) 
 rstAuthors.close(); 
 if (cnConn1 != null) 
 if (cnConn1.getState() == 1) 
 cnConn1.close(); 
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
 
 //.PrintIOError Function 
 
 static void PrintIOError( java.io.IOException je) 
 { 
 System.out.println("Error \n"); 
 System.out.println("\tSource = " + je.getClass() + "\n"); 
 System.out.println("\tDescription = " + je.getMessage() + "\n"); 
 } 
} 
 
// EndActiveConnectionJ 
```

