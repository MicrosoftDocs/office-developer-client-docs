---
title: Open and Close methods example (VJ++)
TOCTitle: Open and Close methods example (VJ++)
ms:assetid: bdcf4a4a-2f70-ef83-7ab2-39d5625fc7aa
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249920(v=office.15)
ms:contentKeyID: 48547448
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Open and Close methods example (VJ++)


**Applies to**: Access 2013, Office 2013

This example uses the **Open** and [Close](close-method-ado.md) methods on both [Recordset](recordset-object-ado.md) and [Connection](connection-object-ado.md) objects that have been opened.

```java 
 
// BeginOpenJ 
import com.ms.wfc.data.*; 
import java.io.* ; 
import com.ms.com.*; 
 
public class OpenX 
{ 
 // The main entry point for the application. 
 
 public static void main (String[] args) 
 { 
 OpenX(); 
 System.exit(0); 
 } 
 
 // OpenX function 
 
 static void OpenX() 
 { 
 
 // Define ADO Objects. 
 Connection cnConn1 = null; 
 Recordset rstEmployees = null; 
 
 // Declarations. 
 BufferedReader in = 
 new BufferedReader (new InputStreamReader(System.in)); 
 String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" 
 + "Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 Variant varDate; 
 String strHDate; 
 
 try 
 { 
 // Open connection. 
 cnConn1 = new Connection(); 
 cnConn1.open(strCnn); 
 
 // Open Employees table. 
 rstEmployees = new Recordset(); 
 rstEmployees.setCursorType(AdoEnums.CursorType.KEYSET); 
 rstEmployees.setLockType(AdoEnums.LockType.OPTIMISTIC); 
 rstEmployees.open("Employee", cnConn1, 
 AdoEnums.CursorType.KEYSET, 
 AdoEnums.LockType.OPTIMISTIC, 
 AdoEnums.CommandType.TABLE); 
 
 // Assign the first employee record's hire date 
 // to a variable, then change the hire date. 
 varDate = rstEmployees.getField("hire_date").getOriginalValue(); 
 System.out.println("Original data\n"); 
 System.out.println("\tName - Hire Date"); 
 strHDate = rstEmployees.getField("hire_date").getString(); 
 strHDate = strHDate.substring(5,7) + "/" + 
 strHDate.substring(8,10) 
 + "/" + strHDate.substring(2,4); 
 System.out.println("\t" + 
 rstEmployees.getField("fName").getString()+ " " 
 + rstEmployees.getField("lName").getString()+ " - " 
 + strHDate); 
 System.out.println("\nPress <Enter> to continue.."); 
 in.readLine(); 
 rstEmployees.getField("hire_date").setString("1/1/1900"); 
 rstEmployees.update(); 
 System.out.println("Changed data\n"); 
 System.out.println("\tName - Hire Date"); 
 strHDate = rstEmployees.getField("hire_date").getString(); 
 strHDate = strHDate.substring(5,7) + "/" + 
 strHDate.substring(8,10) 
 + "/" + strHDate.substring(0,4); 
 System.out.println("\t" + 
 rstEmployees.getField("fName").getString()+ " " 
 + rstEmployees.getField("lName").getString()+ " - " 
 + strHDate); 
 System.out.println("\nPress <Enter> to continue.."); 
 in.readLine(); 
 
 // Requery Recordset and reset the hire date. 
 rstEmployees.requery(); 
 rstEmployees.getField("hire_date").setValue(varDate); 
 rstEmployees.update(); 
 System.out.println("Data after reset\n"); 
 System.out.println("\tName - Hire Date"); 
 strHDate = rstEmployees.getField("hire_date").getString(); 
 strHDate = strHDate.substring(5,7) + "/" + 
 strHDate.substring(8,10) 
 + "/" + strHDate.substring(2,4); 
 System.out.println("\t" + 
 rstEmployees.getField("fName").getString()+ " " 
 + rstEmployees.getField("lName").getString()+ " - " 
 + strHDate); 
 System.out.println("\nPress <Enter> to continue.."); 
 in.readLine(); 
 } 
 catch( AdoException ae ) 
 { 
 // Notify user of any errors that result from ADO. 
 
 // As passing a Recordset, check for null pointer first. 
 if (rstEmployees != null) 
 { 
 PrintProviderError(rstEmployees.getActiveConnection()); 
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
 if (rstEmployees != null) 
 if (rstEmployees.getState() == 1) 
 rstEmployees.close(); 
 // Cleanup objects before exit. 
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
 
 // PrintIOError Function 
 
 static void PrintIOError( java.io.IOException je) 
 { 
 System.out.println("Error \n"); 
 System.out.println("\tSource = " + je.getClass() + "\n"); 
 System.out.println("\tDescription = " + je.getMessage() + "\n"); 
 } 
} 
// EndOpenJ 
```

