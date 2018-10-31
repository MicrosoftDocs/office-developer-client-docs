---
title: ActualSize and DefinedSize properties example (VJ++)
TOCTitle: ActualSize and DefinedSize properties example (VJ++)
ms:assetid: 3a25d3b7-df53-66c1-6141-d51cd57aca96
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249145(v=office.15)
ms:contentKeyID: 48544261
ms.date: 10/17/2018
mtps_version: v=office.15
---

# ActualSize and DefinedSize properties example (VJ++)

**Applies to**: Access 2013, Office 2013

This example uses the [ActualSize](actualsize-property-ado.md) and [DefinedSize](definedsize-property-ado.md) properties to display the defined size and actual size of a field.

```java 
 
// BeginActualSizeJ 
import com.ms.wfc.data.*; 
import java.io.*; 
 
public class ActualSizeX 
{ 
 // The main entry point for the application. 
 
 public static void main (String[] args) 
 { 
 ActualSizeX(); 
 System.exit(0); 
 } 
 
 // ActualSizeX function 
 
 static void ActualSizeX() 
 { 
 
 // Define ADO Objects. 
 Recordset rstStores = null; 
 
 // Declarations. 
 BufferedReader in = new 
 BufferedReader(new InputStreamReader(System.in)); 
 String line = null; 
 String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" 
 + "Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 
 String strStoreName; 
 String strMessage; 
 String strDSize,strASize; 
 int intDefinedSize; 
 int intActualSize; 
 int intChoice = 0; 
 
 try 
 { 
 // Open recordset with Stores table. 
 rstStores = new Recordset(); 
 rstStores.open("stores", strCnn, 
 AdoEnums.CursorType.FORWARDONLY , 
 AdoEnums.LockType.READONLY , 
 AdoEnums.CommandType.TABLE); 
 
 // Loop through the Recordset displaying the contents 
 // of the stor_name field, the field's defined size 
 // and it's actual size. 
 
 while ( !(rstStores.getEOF( ))) // continuous loop 
 { 
 // Read data field in the variables. 
 strStoreName = rstStores.getField("stor_name").getString(); 
 intDefinedSize = 
 rstStores.getField("stor_name").getDefinedSize(); 
 strDSize = Integer.toString(intDefinedSize); 
 intActualSize = rstStores.getField 
 ("stor_name").getActualSize (); 
 strASize = Integer.toString(intActualSize); 
 
 // Display current record information. 
 strMessage = "\nStore name: " + strStoreName + "\n" 
 + "Defined Size : " + strDSize + "\n" 
 + "Actual Size : " + strASize; 
 
 System.out.println(strMessage); 
 System.out.println("\nPress <Enter> key to continue."); 
 in.readLine(); 
 rstStores.moveNext(); 
 } 
 } 
 catch( AdoException ae ) 
 { 
 // Notify user of any errors that result from ADO. 
 
 // Check for null pointer for connection object. 
 if (rstStores.getActiveConnection()==null) 
 System.out.println("Exception: " + ae.getMessage()); 
 // As passing a Recordset, check for null pointer first. 
 if (rstStores != null) 
 { 
 PrintProviderError(rstStores.getActiveConnection()); 
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
 if (rstStores != null) 
 if (rstStores.getState() == 1) 
 rstStores.close(); 
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
// EndActualSizeJ 
```

