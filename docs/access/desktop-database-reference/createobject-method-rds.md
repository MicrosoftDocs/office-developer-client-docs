---
title: CreateObject method (RDS)
TOCTitle: CreateObject method (RDS)
ms:assetid: 130debe5-31cf-4ab0-5f78-9adaec7d7126
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248905(v=office.15)
ms:contentKeyID: 48543360
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CreateObject method (RDS)

**Applies to**: Access 2013, Office 2013

Creates the proxy for the target business object and returns a pointer to it. The proxy packages and marshals data to the server-side stub for communications with the business object to send requests and data over the Internet. For in-process component objects, no proxies are used, just a pointer to the object is provided.

## Syntax

Remote Data Service supports the following protocols: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM, and in-process.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Protocol</p></th>
<th><p>Syntax</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP</p></td>
<td><p>Set<em>object</em> = <em>DataSpace</em>.CreateObject(&quot;<em>ProgId</em>&quot;, &quot;<em>https://awebsrvr</em>&quot;)</p></td>
</tr>
<tr class="even">
<td><p>HTTPS</p></td>
<td><p>Set<em>object</em> = <em>DataSpace</em>.CreateObject(&quot;<em>ProgId</em>&quot;, &quot;<em>https://awebsrvr</em>&quot;)</p></td>
</tr>
<tr class="odd">
<td><p>DCOM</p></td>
<td><p>Set<em>object</em> = <em>DataSpace</em>.CreateObject(&quot;<em>ProgId</em>&quot;, &quot;<em>computername</em>&quot;)</p></td>
</tr>
<tr class="even">
<td><p>In-process</p></td>
<td><p>Set<em>object</em> = <em>DataSpace</em>.CreateObject(&quot;<em>ProgId</em>&quot;, &quot; &quot;)</p></td>
</tr>
</tbody>
</table>


## Parameters

|Parameter|Description|
|:--------|:----------|
|*Object* |An object variable that evaluates to an object that is the type specified in *ProgID*.|
|*DataSpace* |An object variable that represents an [RDS.DataSpace](dataspace-object-rds.md) object used to create an instance of the new object.|
|*ProgID* |A **String** value that contains the programmatic identifier specifying a server-side business object that implements your application's business rules.|
|*awebsrvr* or *computername* |A **String** value that represents a URL identifying the Internet Information Services (IIS) web server where an instance of the server business object is created.|

## Remarks

The *HTTP protocol* is the standard web protocol; *HTTPS* is a secure web protocol. Use the *DCOM protocol* when running a local-area network without HTTP. The *in-process* protocol is a local dynamic-link library (DLL); it does not use a network.

