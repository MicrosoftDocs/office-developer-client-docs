---
title: Stat Method - ActiveX Data Objects (ADO)
TOCTitle: Stat method (ADO)
ms:assetid: d3d3976b-14d4-dee0-412d-a37bc72fbfd3
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250056(v=office.15)
ms:contentKeyID: 48547916
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Stat method (ADO)


**Applies to**: Access 2013, Office 2013

Retrieves information about a **Stream** object.

## Syntax

Long *stream*.Stat(*StatStg*, *StatFlag*)

## Return value

A long value indicating the status of the operation.

## Parameters

  - *StatStg*

  - A STATSTG structure that will be filled in with information about the stream. The implementation of the Stat method used by the ADO Stream object does not fill in all of the fields of the structure.

  - *StatFlag*

  - Specifies that this method does not return some of the members in the STATSTG structure, thus saving a memory allocation operation. Values are taken from the STATFLAG enumeration.  
      
    The STATFLAG enumeration has two values
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Constant</p></th>
    <th><p>Value</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>STATFLAG_DEFAULT</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>STATFLAG_NONAME</p></td>
    <td><p>1</p></td>
    </tr>
    </tbody>
    </table>


## Remarks

The version of the Stat method implemented for the ADO Stream object fills in the following fields of the STATSTG structure:

  - *pwcsName*

  - A string containing the name of the stream, if one is available and the StatFlag value STATFLAG\_NONAME was not specified.

  - *cbSize*

  - Specifies the size in bytes of the stream or byte array.

  - *mtime*

  - Indicates the last modification time for this storage, stream, or byte array.

  - *ctime*

  - Indicates the creation time for this storage, stream, or byte array.

  - *atime*

  - Indicates the last access time for this storage, stream or byte array.

If STATFLAG\_NONAME is specified in the StatFlag parameter, the name of the stream is not returned.

If STATFLAG\_NONAME was not specified in the StatFlag parameter, and there is no name available for the current stream, this value will be E\_NOTIMPL.

