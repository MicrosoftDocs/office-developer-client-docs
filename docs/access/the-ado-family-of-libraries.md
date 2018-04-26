---
title: "The ADO Family of Libraries"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 9e794509-d0a8-2e5b-02a8-65e26f059c4e
description: "Three major libraries make up the ADO family: ADO (including RDS), ADO MD, and ADOX."
---

# The ADO Family of Libraries

Three major libraries make up the ADO family: ADO (including RDS), ADO MD, and ADOX.
  
## ADO

ADO enables your client applications to access and manipulate data from a database server through an OLE DB provider. The primary benefits of ADO are ease of use, high speed, low memory overhead, and a small disk footprint. ADO supports key features for building client/server and Web-based applications.
  
ADO also features Remote Data Service (RDS), by which you can move data from a server to a client application or Web page, manipulate the data on the client, and return updates to the server in a single round trip.
  
## ADO MD

Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) provides easy access to multidimensional data from languages such as Microsoft Visual Basic, Microsoft Visual C++, and Microsoft Visual J++. ADO MD extends ADO to include objects specific to multidimensional data, such as the **CubeDef** and **Cellset** objects. With ADO MD you can browse multidimensional schema, query a cube, and retrieve the results. 
  
Like ADO, ADO MD uses an underlying OLE DB provider to gain access to data. To work with ADO MD, the provider must be a multidimensional data provider (MDP) as defined by the OLE DB for OLAP specification. MDPs present data in multidimensional views as opposed to tabular data providers (TDPs) that present data in tabular views. Refer to the documentation for your OLE DB for OLAP provider for more detailed information about the specific syntax and behaviors supported by your provider.
  
## ADOX

Microsoft ActiveX Data Objects Extensions for Data Definition Language and Security (ADOX) is an extension to the ADO objects and programming model. ADOX includes objects for schema creation and modification as well as security. Because it is an object-based approach to schema manipulation, you can write code that will work against various data sources regardless of differences in their native syntaxes.
  
ADOX is a companion library to the core ADO objects. It exposes additional objects for creating, modifying, and deleting schema objects, such as tables and procedures. It also includes security objects to maintain users and groups, and to grant and revoke permissions on objects.
  

