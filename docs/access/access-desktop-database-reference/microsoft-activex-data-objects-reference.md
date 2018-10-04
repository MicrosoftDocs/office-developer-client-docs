---
title: Microsoft ActiveX Data Objects Reference
TOCTitle: Microsoft ActiveX Data Objects Reference
ms:assetid: 235fc575-8a2e-913c-fa3d-bb86256733f9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249010(v=office.15)
ms:contentKeyID: 48543728
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Microsoft ActiveX Data Objects Reference


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Purpose  
RDS  
ADO MD  
ADOX  
Main Components of ADO 2.5  
Feedback  

## Purpose

Microsoft ActiveX Data Objects (ADO) enable your client applications to access and manipulate data from a database server through an OLE DB provider. Its primary benefits are ease of use, high speed, low memory overhead, and a small disk footprint. ADO supports key features for building client/server and Web-based applications.

## RDS

ADO also features Remote Data Service (RDS), by which you can move data from a server to a client application or Web page, manipulate the data on the client, and return updates to the server in a single round trip.

## ADO MD

Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) provides easy access to multidimensional data from languages such as Microsoft Visual Basic, Microsoft Visual C++, and Microsoft Visual J++. ADO MD extends Microsoft ActiveX Data Objects (ADO) to include objects specific to multidimensional data, such as the CubeDef and Cellset objects. With ADO MD you can browse multidimensional schema, query a cube, and retrieve the results.

Like ADO, ADO MD uses an underlying OLE DB provider to gain access to data. To work with ADO MD, the provider must be a multidimensional data provider (MDP) as defined by the OLE DB for OLAP specification. MDPs present data in multidimensional views as opposed to tabular data providers (TDPs) that present data in tabular views. Refer to the documentation for your OLAP OLE DB provider for more detailed information on the specific syntax and behaviors supported by your provider.

## ADOX

Microsoft ActiveX Data Objects Extensions for Data Definition Language and Security (ADOX) is an extension to the ADO objects and programming model. ADOX includes objects for schema creation and modification, as well as security. Because it is an object-based approach to schema manipulation, you can write code that will work against various data sources regardless of differences in their native syntaxes.

ADOX is a companion library to the core ADO objects. It exposes additional objects for creating, modifying, and deleting schema objects, such as tables and procedures. It also includes security objects to maintain users and groups and to grant and revoke permissions on objects.

## Main Components of ADO 2.5

[Programmer's Guide](ado-programmer-s-guide.md)

An introduction to using ADO, RDS, ADO MD, and ADOX.

[Programmer's Reference](https://msdn.microsoft.com/en-us/library/jj248831\(v=office.15\))

This section of the ADO documentation contains topics for each ADO, RDS, ADO MD, and ADOX object, collection, property, dynamic property, method, event, and enumeration.

## Feedback

You can send feedback about ADO documentation or samples directly to the ADO documentation team.

