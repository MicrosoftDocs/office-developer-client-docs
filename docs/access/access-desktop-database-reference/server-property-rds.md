---
title: Server Property (RDS)
TOCTitle: Server Property (RDS)
ms:assetid: 17519dbe-a43a-1d0d-22c1-dc0def2f63ab
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248926(v=office.15)
ms:contentKeyID: 48543448
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Server Property (RDS)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Indicates the Internet Information Services (IIS) name and communication protocol.

You can set the **Server** property at design time in the [RDS.DataControl](datacontrol-object-rds.md) object's OBJECT tags, or at run time in scripting code.

## Syntax

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Protocol</p></th>
<th><p>Design-time syntax</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP</p></td>
<td><pre><code>&lt;PARAM NAME=&quot;Server&quot; VALUE=&quot;http://awebsrvr:port&quot;&gt;</code></pre>
<p></p></td>
</tr>
<tr class="even">
<td><p>HTTPS</p></td>
<td><pre><code>&lt;PARAM NAME=&quot;Server&quot; VALUE=&quot;https://awebsrvr:port&quot;&gt;</code></pre>
<p></p></td>
</tr>
<tr class="odd">
<td><p>DCOM</p></td>
<td><pre><code>&lt;PARAM NAME=&quot;Server&quot; VALUE=&quot;computername&quot;&gt;</code></pre>
<p></p></td>
</tr>
<tr class="even">
<td><p>In-process</p></td>
<td><pre><code>&lt;PARAM NAME=&quot;Server&quot; VALUE=&quot;&quot;&gt;</code></pre>
<p></p></td>
</tr>
</tbody>
</table>


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Protocol</p></th>
<th><p>Run-time syntax</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP</p></td>
<td><pre><code>DataControl.Server=&quot;http://awebsrvr:port&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>HTTPS</p></td>
<td><pre><code>DataControl.Server=&quot;https://awebsrvr:port&quot;</code></pre></td>
</tr>
<tr class="odd">
<td><p>DCOM</p></td>
<td><pre><code>DataControl.Server=&quot;computername&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>In-process</p></td>
<td><pre><code>DataControl.Server=&quot;&quot;</code></pre></td>
</tr>
</tbody>
</table>


## Parameters

  - *awebsrvr* or *computername*

  - A **String** value that contains an Internet or intranet path, or computer name, if the server is on a remote computer; or, an empty string if the server is on the local computer.

  - *port*

  - Optional. A port that is used to connect to an IIS server. The port number is set in Internet Explorer (on the **Tools** menu, click **Internet Options**, and then select the **Connection** tab) or in IIS.

  - *DataControl*

  - An object variable that represents an **RDS.DataControl** object.

## Remarks

The server is the location where the **RDS.DataControl** request (that is, a query or update) is processed. By default, all requests are processed by the [RDSServer.DataFactory](datafactory-object-rdsserver.md) object, [MSDFMAP.Handler](datafactory-customization.md) component, and [MSDFMAP.INI](understanding-the-customization-file.md) file on the specified server. Remember that when changing servers to reconcile settings in the old and new **MSDFMAP.INI** files. Incompatibilities may cause requests that succeed on one server to fail on another. If the Server property is set to "", these objects will be used on the local machine.

