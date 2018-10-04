﻿---
title: Clone Method Example (VJ++)
TOCTitle: Clone Method Example (VJ++)
ms:assetid: 8d8ac6dc-af73-1e42-fcc2-0c51709ad580
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249621(v=office.15)
ms:contentKeyID: 48546259
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Clone Method Example (VJ++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Clone](clone-method-ado.md) method to create copies of a [Recordset](recordset-object-ado.md) and then lets the user position the record pointer of each copy independently.

``` 
 
// BeginCloneJ 
import com.ms.wfc.data.*; 
import java.io.* ; 
 
public class CloneX 
{ 
 // The main entry point for the application. 
 
 public static void main (String[] args) 
 { 
 CloneX(); 
 System.exit(0); 
 } 
 
 // CloneX function 
 
 static void CloneX() 
 { 
 // Assign SQL statement and connection string to variables. 
 String strSQL = "SELECT stor_name FROM Stores " 
 + "ORDER BY stor_name"; 
 
 String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" 
 + "Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 
 // Define ADO Objects. 
 Recordset[] arstStores = null; 
 
 //Declarations. 
 BufferedReader in = 
 new BufferedReader (new InputStreamReader(System.in)); 
 String line = null; 
 String strMessage; 
 String strFind; 
 int intLoop; 
 boolean booExit = true; 
 
 try 
 { 
 // Open recordset as a static cursor type recordset. 
 arstStores = new Recordset[3]; 
 arstStores[0] = new Recordset(); 
 arstStores[0].setCursorType(AdoEnums.CursorType.STATIC); 
 arstStores[0].setLockType(AdoEnums.LockType.BATCHOPTIMISTIC); 
 arstStores[0].open(strSQL,strCnn,AdoEnums.CursorType.STATIC, 
 AdoEnums.LockType.BATCHOPTIMISTIC,AdoEnums.CommandType.TEXT); 
 
 // Create two clones of the original Recordset. 
 arstStores[1] = (Recordset)arstStores[0].clone 
 (AdoEnums.LockType.BATCHOPTIMISTIC); 
 arstStores[2] = (Recordset)arstStores[0].clone 
 (AdoEnums.LockType.BATCHOPTIMISTIC); 
 
 while(booExit) 
 { 
 // Loop through the array so that on each pass, 
 // the user is searching a different copy of the 
 // same Recordset. 
 for (intLoop = 0; intLoop < 3; intLoop++) 
 { 
 // Ask for search string while showing where 
 // the current record pointer is for each Recordset 
 strMessage = "\nRecordsets from stores table:" + "\n" 
 + " 1 - Original - Record pointer at " 
 + arstStores[0].getField("stor_name").getString() 
 + "\n" + " 2 - Clone - Record pointer at " 
 + arstStores[1].getField("stor_name").getString() 
 + "\n" + " 3 - Clone - Record pointer at " 
 + arstStores[2].getField("stor_name").getString() 
 + "\n"; 
 System.out.println(strMessage); 
 System.out.println("Enter search string for #" 
 + (intLoop+1) + "(Press <Enter> to Exit.)"); 
 
 strFind = in.readLine().trim(); 
 if(strFind.length() == 0) 
 { 
 booExit = false; 
 break; 
 } 
 
 // Find the search string; if there's no 
 // match, jump to the last record. 
 arstStores[intLoop].setFilter("stor_name >= '" + 
 strFind + "'"); 
 if (arstStores[intLoop].getEOF()) 
 { 
 arstStores[intLoop].setFilter 
 (new Integer(AdoEnums.FilterGroup.NONE)); 
 arstStores[intLoop].moveLast(); 
 } 
 } 
 } 
 } 
 catch( AdoException ae ) 
 { 
 // Notify user of any errors that result from ADO. 
 
 // As passing a connection, check for null pointer first. 
 if (arstStores[0] != null) 
 { 
 PrintProviderError(arstStores[0].getActiveConnection()); 
 } 
 else 
 { 
 System.out.println("Exception: " + ae.getMessage()); 
 } 
 } 
 
 // System read requires this catch. 
 catch( java.io.IOException je) 
 { 
 PrintIOError(je); 
 } 
 
 finally 
 { 
 // Cleanup objects before exit. 
 if (arstStores[0] != null) 
 if (arstStores[0].getState() == 1) 
 arstStores[0].close(); 
 if (arstStores[1] != null) 
 if (arstStores[1].getState() == 1) 
 arstStores[1].close(); 
 if (arstStores[2] != null) 
 if (arstStores[2].getState() == 1) 
 arstStores[2].close(); 
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
// EndCloneJ 
```

