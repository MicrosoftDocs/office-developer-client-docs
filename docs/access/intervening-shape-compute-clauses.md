---
title: "Intervening Shape COMPUTE Clauses"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 3e9dcef2-776c-0365-4a92-68e325f7dbb5
description: "It is valid to embed one or more COMPUTE clauses between the parent and child in a parameterized shape command, as in the following example:"
---

# Intervening Shape COMPUTE Clauses

It is valid to embed one or more COMPUTE clauses between the parent and child in a parameterized shape command, as in the following example:
  
```
 
SHAPE {select au_lname, state from authors} APPEND 
 ((SHAPE 
 (SHAPE 
 {select * from authors where state = ?} rs 
 COMPUTE rs, ANY(rs.state) state, ANY(rs.au_lname) au_lname 
 BY au_id) rs2 
 COMPUTE rs2, ANY(rs2.state) BY au_lname) 
RELATE state TO PARAMETER 0) 

```


