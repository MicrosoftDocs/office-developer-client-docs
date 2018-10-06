---
title: Recordset Object (ADO)
TOCTitle: Recordset Object (ADO)
ms:assetid: 0f963bf8-f066-dc8a-b754-f427de712df1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248865(v=office.15)
ms:contentKeyID: 48543267
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset Object (ADO)


**Applies to**: Access 2013 | Office 2013

Represents the entire set of records from a base table or the results of an executed command. At any time, the **Recordset** object refers to only a single record within the set as the current record.

## Remarks

You use **Recordset** objects to manipulate data from a provider. When you use ADO, you manipulate data almost entirely using **Recordset** objects. All **Recordset** objects consist of records (rows) and fields (columns). Depending on the functionality supported by the provider, some **Recordset** methods or properties may not be available.

ADODB.Recordset is the ProgID that should be used to create a **Recordset** object. Existing applications that reference the outdated ADOR.Recordset ProgID will continue to work without recompiling, but new development should reference ADODB.Recordset.

There are four different cursor types defined in ADO:

  - **Dynamic cursor** — allows you to view additions, changes, and deletions by other users; allows all types of movement through the **Recordset** that doesn't rely on bookmarks; and allows bookmarks if the provider supports them.

  - **Keyset cursor** — behaves like a dynamic cursor, except that it prevents you from seeing records that other users add, and prevents access to records that other users delete. Data changes by other users will still be visible. It always supports bookmarks and therefore allows all types of movement through the **Recordset**.

  - **Static cursor** — provides a static copy of a set of records for you to use to find data or generate reports; always allows bookmarks and therefore allows all types of movement through the **Recordset**. Additions, changes, or deletions by other users will not be visible. This is the only type of cursor allowed when you open a client-side **Recordset** object.

  - **Forward-only cursor** — allows you to only scroll forward through the **Recordset**. Additions, changes, or deletions by other users will not be visible. This improves performance in situations where you need to make only a single pass through a **Recordset**.

Set the [CursorType](cursortype-property-ado.md) property prior to opening the **Recordset** to choose the cursor type, or pass a *CursorType* argument with the [Open](open-method-ado-recordset.md) method. Some providers don't support all cursor types. Check the documentation for the provider. If you don't specify a cursor type, ADO opens a forward-only cursor by default.

If the [CursorLocation](cursorlocation-property-ado.md) property is set to **adUseClient** to open a **Recordset**, the **UnderlyingValue** property on [Field](field-object-ado.md) objects is not available in the returned **Recordset** object. When used with some providers (such as the Microsoft ODBC Provider for OLE DB in conjunction with Microsoft SQL Server), you can create **Recordset** objects independently of a previously defined [Connection](connection-object-ado.md) object by passing a connection string with the **Open** method. ADO still creates a [Connection](connection-object-ado.md) object, but it doesn't assign that object to an object variable. However, if you are opening multiple **Recordset** objects over the same connection, you should explicitly create and open a **Connection** object; this assigns the **Connection** object to an object variable. If you do not use this object variable when opening your **Recordset** objects, ADO creates a new **Connection** object for each new **Recordset**, even if you pass the same connection string.

You can create as many **Recordset** objects as needed.

When you open a **Recordset**, the current record is positioned to the first record (if any) and the [BOF](bof-eof-properties-ado.md) and [EOF](bof-eof-properties-ado.md) properties are set to **False**. If there are no records, the **BOF** and **EOF** property settings are **True**.

You can use the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), **MoveLast**, **MoveNext**, and **MovePrevious** methods; the [Move](move-method-ado.md) method; and the [AbsolutePosition](absoluteposition-property-ado.md), [AbsolutePage](absolutepage-property-ado.md), and [Filter](filter-property-ado.md) properties to reposition the current record, assuming the provider supports the relevant functionality. Forward-only **Recordset** objects support only the [MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) method. When you use the **Move** methods to visit each record (or enumerate the **Recordset**), you can use the **BOF** and **EOF** properties to determine if you've moved beyond the beginning or end of the **Recordset**.

**Recordset** objects can support two types of updating: immediate and batched. In immediate updating, all changes to data are written immediately to the underlying data source once you call the [Update](update-method-ado.md) method. You can also pass arrays of values as parameters with the [AddNew](addnew-method-ado.md) and **Update** methods and simultaneously update several fields in a record.

If a provider supports batch updating, you can have the provider cache changes to more than one record and then transmit them in a single call to the database with the [UpdateBatch](updatebatch-method-ado.md) method. This applies to changes made with the **AddNew**, **Update**, and [Delete](delete-method-ado-recordset.md) methods. After you call the **UpdateBatch** method, you can use the [Status](status-property-ado-recordset.md) property to check for any data conflicts in order to resolve them.


> [!NOTE]
> <P>To execute a query without using a <A href="command-object-ado.md">Command</A> object, pass a query string to the <STRONG>Open</STRONG> method of a <STRONG>Recordset</STRONG> object. However, a <STRONG>Command</STRONG> object is required when you want to persist the command text and re-execute it, or use query parameters.</P>



The [Mode](mode-property-ado.md) property governs access permissions.

The **Fields** collection is the default member of the **Recordset** object. As a result, the following two code statements are equivalent.

    Debug.Print objRs.Fields.Item(0)  ' Both statements print 
    Debug.Print objRs(0)              '  the Value of Item(0).

