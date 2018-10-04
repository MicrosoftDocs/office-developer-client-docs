---
title: WITH OWNERACCESS OPTION Declaration (Microsoft Access SQL)
TOCTitle: WITH OWNERACCESS OPTION Declaration (Microsoft Access SQL)
ms:assetid: 82e51071-12b2-e97e-07b4-27ffceda831e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff196724(v=office.15)
ms:contentKeyID: 48545993
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277584
dev_langs:
- sql
f1_categories:
- Office.Version=v15
---

# WITH OWNERACCESS OPTION Declaration (Microsoft Access SQL)


_**Applies to:** Access 2013 | Office 2013_

In a multiuser environment with a secure workgroup, use this declaration with a query to give the user who runs the query the same permissions as the query's owner.

## Syntax

*sqlstatement* WITH OWNERACCESS OPTION

## Remarks

The WITH OWNERACCESS OPTION declaration is optional.

The following example enables the user to view salary information (even if the user does not otherwise have permission to view the Payroll table), provided that the query's owner does have that permission:

``` sql
SELECT LastName, 
FirstName, Salary
FROM Employees 
ORDER BY LastName 
WITH OWNERACCESS OPTION;
```

If a user is otherwise prevented from creating or adding to a table, you can use WITH OWNERACCESS OPTION to enable the user to run a make-table or append query.

If you want to enforce workgroup security settings and users' permissions, do not include the WITH OWNERACCESS OPTION declaration.

This option requires you to have access to the System.mdw file associated with the database. It is useful only in secured multiuser implementations.

