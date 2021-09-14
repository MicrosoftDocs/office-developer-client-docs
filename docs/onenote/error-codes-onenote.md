---
title: "Error codes (OneNote)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 390df5ce-e730-470d-b6e9-0de4a3e904f8
description: "This topic lists the error codes in the OneNote 2013 object model."
---

# Error codes (OneNote)

This topic lists the error codes in the OneNote 2013 object model.
  
|**HResult**|**Value**|**Description**|
|:-----|:-----|:-----|
|hrMalformedXML  <br/> |0x80042000  <br/> |The XML is not well-formed.  <br/> |
|hrInvalidXML  <br/> |0x80042001  <br/> |The XML is invalid.  <br/> |
|hrCreatingSection  <br/> |0x80042002  <br/> |The section could not be created.  <br/> |
|hrOpeningSection  <br/> |0x80042003  <br/> |The section could not be opened.  <br/> |
|hrSectionDoesNotExist  <br/> |0x80042004  <br/> |The section does not exist.  <br/> |
|hrPageDoesNotExist  <br/> |0x80042005  <br/> |The page does not exist.  <br/> |
|hrFileDoesNotExist  <br/> |0x80042006  <br/> |The file does not exist.  <br/> |
|hrInsertingImage  <br/> |0x80042007  <br/> |The image could not be inserted.  <br/> |
|hrInsertingInk  <br/> |0x80042008  <br/> |The ink could not be inserted.  <br/> |
|hrInsertingHtml  <br/> |0x80042009  <br/> |The HTML could not be inserted.  <br/> |
|hrNavigatingToPage  <br/> |0x8004200a  <br/> |The page could not be opened.  <br/> |
|hrSectionReadOnly  <br/> |0x8004200b  <br/> |The section is read-only.  <br/> |
|hrPageReadOnly  <br/> |0x8004200c  <br/> |The page is read-only.  <br/> |
|hrInsertingOutlineText  <br/> |0x8004200d  <br/> |The outline text could not be inserted.  <br/> |
|hrPageObjectDoesNotExist  <br/> |0x8004200e  <br/> |The page object does not exist.  <br/> |
|hrBinaryObjectDoesNotExist  <br/> |0x8004200f  <br/> |The binary object does not exist.  <br/> |
|hrLastModifiedDateDidNotMatch  <br/> |0x80042010  <br/> |The last modified date does not match.  <br/> |
|hrGroupDoesNotExist  <br/> |0x80042011  <br/> |The section group does not exist.  <br/> |
|hrPageDoesNotExistInGroup  <br/> |0x80042012  <br/> |The page does not exist in the section group.  <br/> |
|hrNoActiveSelection  <br/> |0x80042013  <br/> |There is no active selection.  <br/> |
|hrObjectDoesNotExist  <br/> |0x80042014  <br/> |The object does not exist.  <br/> |
|hrNotebookDoesNotExist  <br/> |0x80042015  <br/> |The notebook does not exist.  <br/> |
|hrInsertingFile  <br/> |0x80042016  <br/> |The file could not be inserted.  <br/> |
|hrInvalidName  <br/> |0x80042017  <br/> |The name is invalid.  <br/> |
|hrFolderDoesNotExist  <br/> |0x80042018  <br/> |The folder (section group) does not exist.  <br/> |
|hrInvalidQuery  <br/> |0x80042019  <br/> |The query is invalid.  <br/> |
|hrFileAlreadyExists  <br/> |0x8004201a  <br/> |The file already exists.  <br/> |
|hrSectionEncryptedAndLocked  <br/> |0x8004201b  <br/> |The section is encrypted and locked.  <br/> |
|hrDisabledByPolicy  <br/> |0x8004201c  <br/> |The action is disabled by a policy.  <br/> |
   
||||
|:-----|:-----|:-----|
|hrNotYetSynchronized  <br/> |0x8004201d  <br/> |OneNote has not yet synchronized content.  <br/> |
|hrLegacySection  <br/> |0x8004201E  <br/> |The section is from OneNote 2007 or earlier.  <br/> |
|hrMergeFailed  <br/> |0x8004201F  <br/> |The merge operation failed.  <br/> |
|hrInvalidXMLSchema  <br/> |0x80042020  <br/> |The XML Schema is invalid.  <br/> |
|hrFutureContentLoss  <br/> |0x80042022  <br/> |Content loss has occurred (from future versions of OneNote).  <br/> |
|hrTimeOut  <br/> |0x80042023  <br/> |The action timed out.  <br/> |
|hrRecordingInProgress  <br/> |0x80042024  <br/> |Audio recording is in progress.  <br/> |
|hrUnknownLinkedNoteState  <br/> |0x80042025  <br/> |The linked-note state is unknown.  <br/> |
|hrNoShortNameForLinkedNote  <br/> |0x80042026  <br/> |No short name exists for the linked note.  <br/> |
|hrNoFriendlyNameForLinkedNote  <br/> |0x80042027  <br/> |No friendly name exists for the linked note.  <br/> |
|hrInvalidLinkedNoteUri  <br/> |0x80042028  <br/> |The linked note URI is invalid.  <br/> |
|hrInvalidLinkedNoteThumbnail  <br/> |0x80042029  <br/> |The linked note thumbnail is invalid.  <br/> |
|hrImportLNTThumbnailFailed  <br/> |0x8004202A  <br/> |The importation of linked note thumbnail failed.  <br/> |
|hrUnreadDisabledForNotebook  <br/> |0x8004202B  <br/> |Unread highlighting is disabled for the notebook.  <br/> |
|hrInvalidSelection  <br/> |0x8004202C  <br/> |The selection is invalid.  <br/> |
|hrConvertFailed  <br/> |0x8004202D  <br/> |The conversion failed.  <br/> |
|hrRecycleBinEditFailed  <br/> |0x8004202E  <br/> |Edit failed in the Recycle Bin.  <br/> |
   
The following lists the new error codes for OneNote 2013.
  
|**HResult**|**Value**|**Description**|
|:-----|:-----|:-----|
|hrIMConversationTypeInvalid  <br/> |0x8004202F  <br/> |Returned by **UpdatePageContent** if **IMConversationType** page node property was to a value other than 0,1,2 or 3  <br/> |
|hrAppInModalUI  <br/> |0x80042030  <br/> |A modal dialog is blocking the app.  <br/> |
   
## See also

- [OneNote developer reference](onenote-developer-reference.md)

