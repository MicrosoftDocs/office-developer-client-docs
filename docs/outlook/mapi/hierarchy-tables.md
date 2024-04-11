---
title: "Hierarchy Tables"
description: A hierarchy table contains information about the folders in a message store or the containers in an address book container.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: b8aa6b36-d6e5-4e1f-8ac5-5d6a78a70bf8
---

# Hierarchy Tables
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A hierarchy table contains information about the folders in a message store or the containers in an address book container. Each row of a hierarchy table contains a set of columns with information about one folder or address book container. Hierarchy tables are primarily used by clients and implemented by message store providers to show a tree of folders and subfolders and implemented by address book providers to show a tree of containers in the address book. Containers that cannot hold subcontainers, as indicated by the absence of the AB_SUBCONTAINERS flag in their **PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property, do not implement a hierarchy table.
  
A hierarchy table can be accessed by calling:
  
- [IMAPIContainer::GetHierarchyTable](imapicontainer-gethierarchytable.md).

    - Or -

- [IMAPIProp::OpenProperty](imapiprop-openproperty.md) passing **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) as the property tag and IID_IMAPITable as the interface identifier.

Containers and folders must support both techniques for retrieving table properties. It is unacceptable for service providers to support only one way to access these tables because clients expect to have the choice. 
  
> [!IMPORTANT]
> Store providers are not guaranteed to honor the sort order set specified for hierarchy tables.
  
The call to **IMAPIProp::OpenProperty** involves accessing the hierarchy table by opening its corresponding property, **PR_CONTAINER_HIERARCHY**. Although **PR_CONTAINER_HIERARCHY** cannot be retrieved through a folder or container's [IMAPIProp::GetProps](imapiprop-getprops.md) method, it is included in the property tag array that is returned by the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method.
  
 **PR_CONTAINER_HIERARCHY** can also be used to include or exclude a hierarchy table from a copy operation. If a client specifies **PR_CONTAINER_HIERARCHY** in the *lpExcludeProps* parameter for [IMAPIProp::CopyTo](imapiprop-copyto.md) in a copy operation, the new folder or container will not support the hierarchy table of the original folder or container.
  
The following properties make up the required column set in a hierarchy table:
  
||Value |
|:-----|:-----|
|**PR_COMMENT** ([PidTagComment](pidtagcomment-canonical-property.md))  <br/> |**PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md))  <br/> |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |**PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |**PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |**PR_STATUS** ([PidTagStatus](pidtagstatus-canonical-property.md))  <br/> |
   
 **PR_DISPLAY_NAME** contains the name for the container or folder that should appear in the display of the hierarchy.
  
 **PR_ENTRYID** is the entry identifier associated with this container or folder. It is expected to be a long-term entry identifier. Clients and MAPI can pass this entry identifier to **OpenEntry** to open the container or folder and view its contents by calling [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md).
  
 **PR_DEPTH** is a numeric value that indicates the level of indentation for this container or folder with zero being the top level. The deeper in the hierarchy a container or folder resides, the higher the value for its **PR_DEPTH** property. Clients use the **PR_DEPTH** property to display a hierarchy table appropriately so that users can clearly see parent and child relationships. Container or folder depth is always relative to the container or folder implementing the hierarchy table.
  
 **PR_OBJECT_TYPE** is always set to MAPI_ABCONT for address book hierarchy tables and MAPI_FOLDER for folder hierarchy tables.
  
 **PR_DISPLAY_TYPE** is a numeric value that relates to how a container or folder is displayed in the hierarchy table. It is mainly used for display purposes, to differentiate visually between types of containers or folders. Many message store and address book providers use icons for the different display types. It is up to the provider to supply these icons; MAPI does not supply defaults.
  
MAPI defines many values for **PR_DISPLAY_TYPE**, some that are valid for folders and others that are used with the hierarchy tables of address book containers. Typically, a folder's **PR_DISPLAY_TYPE** is set to DT_FOLDER to indicate a default folder icon, DT_FOLDER_LINK to indicate an icon that represents a link to another folder, or DT_FOLDER_SPECIAL to indicate an icon that is application-specific. DT_FOLDER_LINK is used with search-results folders.
  
In addition to these required columns, address book hierarchy tables must include the **PR_CONTAINER_FLAGS** property. **PR_CONTAINER_FLAGS** indicates various attributes about a container in the hierarchy and is used to distinguish one container from another.
  
An optional property for address book hierarchy tables is the **PR_AB_PROVIDER_ID** ([PidTagAbProviderId](pidtagabproviderid-canonical-property.md)) property.
  
Message-store hierarchy tables include these properties in their required column set:
  
- **PR_FOLDER_TYPE** ([PidTagFolderType](pidtagfoldertype-canonical-property.md))
    
- **PR_SUBFOLDERS** ([PidTagSubfolders](pidtagsubfolders-canonical-property.md))
    
- **PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))
    
- **PR_CONTENT_UNREAD** ([PidTagContentUnreadCount](pidtagcontentunreadcount-canonical-property.md))

Address book providers must support the following **IMAPITable** methods in their hierarchy table implementations because they are required by the MAPI integrated address book:
  
|Method |Method |
|:-----|:-----|
|[IMAPITable::QueryColumns](imapitable-querycolumns.md) <br/> |[IMAPITable::QueryPosition](imapitable-queryposition.md) <br/> |
|[IMAPITable::SeekRow](imapitable-seekrow.md) <br/> |[IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md) <br/> |
|[IMAPITable::FindRow](imapitable-findrow.md) <br/> |[IMAPITable::Restrict](imapitable-restrict.md) <br/> |
|[IMAPITable::CreateBookmark](imapitable-createbookmark.md) <br/> |[IMAPITable::FreeBookmark](imapitable-freebookmark.md) <br/> |
|[IMAPITable::QueryRows](imapitable-queryrows.md) <br/> | <br/> |

## See also

[MAPI Tables](mapi-tables.md)
