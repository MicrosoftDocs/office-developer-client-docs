---
title: "Project Server error codes"
manager: soliver
ms.date: 09/17/2015
ms.audience: Developer
f1_keywords:
- error codes
- errors
- Project Server errors
- PSErrorID
- PSI errors
keywords:
- psi, error codes,Error codes, Project Server,PSErrorID,Project Server Interface, error codes,Project Server, error codes
ms.assetid: db78a09c-ebef-47cc-8623-40abe117aa08
description: "This topic contains tables of error codes for the Project Server Interface (PSI) in Project Server 2013. The tables are arranged by functional area and by error code range."
ms.localizationpriority: high
---

# Project Server error codes

This topic contains tables of error codes for the Project Server Interface (PSI) in Project Server 2013. The tables are arranged by functional area and by error code range.
   
Project Server 2013 processes and PSI methods have error code numbers that are generally arranged by functional area. The [Microsoft.Office.Project.Server.Library.PSErrorID](https://msdn.microsoft.com/library/microsoft.office.project.server.library.pserrorid_di_pj14mref(v=office.14).aspx) enumeration is duplicated in [WebSvcProject.PSErrorID](https://msdn.microsoft.com/library/office/websvcproject.pserrorid_di_pj14mref.aspx); they list the error codes in alphabetical order by name. This topic lists the error codes in tables that are arranged by the PSI class or functional area and by the error identifier (ID) number. 
  
> [!NOTE]
>  Many of the error codes are general and can have multiple possible causes. For more information about errors, you can do the following: 
> - For ASMX-based applications, use **System.Web.Services.Protocols.SoapException** with the **PSClientError** object to show a list or hierarchy of errors in a PSI method call. See [Error Code Example for ASMX](#pj15_ErrorCodes_ASMXExample). 
> - For WCF-based applications, you can use **System.ServiceModel.FaultException** to get a **PSClientError** object and also to get additional error information. See [Error Code Example for WCF](#pj15_ErrorCodes_WCFExample). 
> - Use the application event log on the Project Server computer.
> - Use the Unified Logging Service (ULS) trace logs. For an explanation, see the *Checking Errors* section in [Getting Started with Development for Project 2010](https://msdn.microsoft.com/library/gg607685.aspx). 
> - For more information about using ULS logs, see the Project Support blog article [Project Server 2010: What to Expect when you get the Unexpected](https://blogs.msdn.com/b/brismith/archive/2010/03/24/project-server-2010-what-to-expect-when-you-get-the-unexpected.aspx), and search the blog for "reading ULS logs." 
> - To help find or watch for specific issues in ULS data, use the [ULS Viewer](https://www.codeproject.com/Articles/458052/ULS-Log-Viewer). 
> - Use the Microsoft SQL Server Profiler to help catch or monitor database errors. For more information, see [SQL Server Profiler](https://msdn.microsoft.com/library/3ad5f33d-559e-41a4-bde6-bb98792f7f1a.aspx). 
> - Many of the error codes are used only internally. For example, because the **ExchangeSync** and **PWA** web services are not supported for third-party development, you are not likely to see error codes from methods in those areas, such as the **Rules** and **StatusReports** methods. However, tables in this article include all Project Server error codes for completeness. 
  
## Table 1. Error code functional areas and related number ranges

|Project Server functional area|Error code number ranges|
|:-----|:-----|
|[Table 3: General error codes](#pj15_ErrorCodes_General) <br/> |0 - 99; 500 - 999; 9131; 10000 - 10099; 20000 - 20099; 26000 - 26099  <br/> |
|[Table 4: Active cache](#pj15_ErrorCodes_ActiveCache) <br/> |12000 - 12099  <br/> |
|[Table 5: Active Directory synchronization](#pj15_ErrorCodes_ActiveDirectory) <br/> |27000 - 27999  <br/> |
|[Table 6: Admin web service](#pj15_ErrorCodes_Admin) <br/> |16600 - 16699; 19011, 19012, and 19032; 20003; and 25000 - 25099  <br/> |
|[Table 7: Archive (backup and restore)](#pj15_ErrorCodes_Archive) <br/> |25000 - 25999; and 29000 - 29099  <br/> |
|[Table 8: Assignments](#pj15_ErrorCodes_Assignments) <br/> |120 - 199  <br/> |
|[Table 9: Calendar](#pj15_ErrorCodes_Calendar) <br/> |77; and 13000 - 13999  <br/> |
|[Table 10: Cube Build Service (CBS)](#pj15_ErrorCodes_CBS) <br/> |17000 - 17999  <br/> |
|[Table 11: Check in - check out](#pj15_ErrorCodes_CICO) <br/> |10100 - 10199  <br/> |
|[Table 12: Custom fields](#pj15_ErrorCodes_CustomFields) <br/> |11500 - 11999  <br/> |
|[Table 13: Lookup tables](#pj15_ErrorCodes_LookupTables) <br/> |11000 - 11499  <br/> |
|[Table 14: Miscellaneous](#pj15_ErrorCodes_Miscellaneous) <br/> |11000 - 11499  <br/> |
|[Table 15: Notifications](#pj15_ErrorCodes_Notifications) <br/> |16000 - 16599  <br/> |
|[Table 16: Optimizer](#pj15_ErrorCodes_Optimizer) (project portfolio analysis)  <br/> |29000 - 29999  <br/> |
|[Table 17: Planner](#pj15_ErrorCodes_Planner) (project portfolio analysis)  <br/> |28000 - 28999  <br/> |
|[Table 18: Projects](#pj15_ErrorCodes_Projects) <br/> |100 - 499; 1000 - 1199; 9100 - 9199; and 23000 - 23999  <br/> |
|[Table 19: Reporting Data Service](#pj15_ErrorCodes_RDS) (RDS)  <br/> |24000 - 24999  <br/> |
|[Table 20: Resources](#pj15_ErrorCodes_Resources) <br/> |2000 - 2999  <br/> |
|[Table 21: Resource plans](#pj15_ErrorCodes_ResourcePlans) <br/> |30000 - 30999  <br/> |
|[Table 22: Rules](#pj15_ErrorCodes_Rules) <br/> |21000 - 21099  <br/> |
|[Table 23: Security](#pj15_ErrorCodes_Security) <br/> |19000 - 19099  <br/> |
|[Table 24: Server events](#pj15_ErrorCodes_Events) <br/> |19033; and 22000 - 22999  <br/> |
|[Table 25: Statusing](#pj15_ErrorCodes_Statusing) <br/> |3100 - 3199  <br/> |
|[Table 26: Status reports](#pj15_ErrorCodes_StatusReports) <br/> |12100 - 12299  <br/> |
|[Table 27: Tasks](#pj15_ErrorCodes_Tasks) <br/> |7000 - 7099  <br/> |
|[Table 28: Timesheets](#pj15_ErrorCodes_Timesheets) <br/> |3200 - 3299  <br/> |
|[Table 29: User delegation](#pj15_ErrorCodes_UserDelegation) <br/> |43000 - 43500  <br/> |
|[Table 30: Workflow](#pj15_ErrorCodes_Workflow) <br/> |35000 - 35999: Workflow  <br/> |
|[Table 31: WSSInterop and ObjectLinkProvider (SharePoint integration)](#pj15_ErrorCodes_WSS) <br/> |16400 - 16499: SharePoint integration and project workspaces  <br/> 18000 - 18099: Object Link Provider and SharePoint project import  <br/> |
   
## Table 2. Error code table by number range

|Error code range|Error code table|
|:-----|:-----|
|0 - 99  <br/> |[Table 3: General error codes](#pj15_ErrorCodes_General), except 77 is in [Table 9: Calendar](#pj15_ErrorCodes_Calendar) <br/> |
|100 - 119  <br/> |[Table 18: Projects](#pj15_ErrorCodes_Projects) <br/> |
|120 - 199  <br/> |[Table 8: Assignments](#pj15_ErrorCodes_Assignments) <br/> |
|500 - 999  <br/> |[Table 3: General error codes](#pj15_ErrorCodes_General) <br/> |
|1000 - 1199  <br/> |[Table 18: Projects](#pj15_ErrorCodes_Projects) <br/> |
|2000 - 2999  <br/> |[Table 20: Resources](#pj15_ErrorCodes_Resources) <br/> |
|3100 - 3199  <br/> |[Table 25: Statusing](#pj15_ErrorCodes_Statusing) <br/> |
|3200 - 3299  <br/> |[Table 28: Timesheets](#pj15_ErrorCodes_Timesheets) <br/> |
|7000 - 7099  <br/> |[Table 27: Tasks](#pj15_ErrorCodes_Tasks) <br/> |
|9100 - 9199  <br/> |[Table 18: Projects](#pj15_ErrorCodes_Projects), except 9131 is in [Table 3: General error codes](#pj15_ErrorCodes_General) <br/> |
|10000 - 10099  <br/> |[Table 3: General error codes](#pj15_ErrorCodes_General) <br/> |
|10100 - 10199  <br/> |[Table 11: Check in - check out](#pj15_ErrorCodes_CICO) <br/> |
|11000 - 11499  <br/> |[Table 13: Lookup tables](#pj15_ErrorCodes_LookupTables) <br/> |
|11500 - 11999  <br/> |[Table 12: Custom fields](#pj15_ErrorCodes_CustomFields) <br/> |
|12000 - 12099  <br/> |[Table 4: Active cache](#pj15_ErrorCodes_ActiveCache) <br/> |
|12100 - 12299  <br/> |[Table 26: Status reports](#pj15_ErrorCodes_StatusReports) <br/> |
|13000 - 13999  <br/> |[Table 9: Calendar](#pj15_ErrorCodes_Calendar) <br/> |
|16000 - 16399  <br/> |[Table 15: Notifications](#pj15_ErrorCodes_Notifications) <br/> |
|16400 - 16499  <br/> |[Table 31: WssInterop and Object Link Provider (SharePoint integration)](#pj15_ErrorCodes_WSS) <br/> |
|16600 - 16699  <br/> |[Table 6: Admin web service](#pj15_ErrorCodes_Admin) <br/> |
|17000 - 17999  <br/> |[Table 10: Cube Build Service (CBS)](#pj15_ErrorCodes_CBS) <br/> |
|18000 - 18099  <br/> |[Table 31: SharePoint integration](#pj15_ErrorCodes_WSS) <br/> |
|19000 - 19099  <br/> |[Table 23: Security](#pj15_ErrorCodes_Security), except 19011, 19012, and 19032 are security-related codes in [Table 6: Admin web service](#pj15_ErrorCodes_Admin) <br/> |
|20000 - 20099  <br/> |[Table 3: General error codes](#pj15_ErrorCodes_General), except 20003 is in [Table 6: Admin web service](#pj15_ErrorCodes_Admin) <br/> |
|21000 - 21099  <br/> |[Table 22: Rules](#pj15_ErrorCodes_Rules) <br/> |
|22000 - 22999  <br/> |[Table 24: Server events](#pj15_ErrorCodes_Events) <br/> |
|23000 - 23999  <br/> |[Table 18: Projects](#pj15_ErrorCodes_Projects) <br/> |
|24000 - 24999  <br/> |[Table 19: Reporting Data Service](#pj15_ErrorCodes_RDS) (RDS)  <br/> |
|25000 - 25999  <br/> |[Table 7: Archive (backup and restore)](#pj15_ErrorCodes_Archive), except 25004, 25006 are in [Table 6: Admin web service](#pj15_ErrorCodes_Admin) <br/> |
|26000 - 26099  <br/> |[Table 3: General error codes](#pj15_ErrorCodes_General) <br/> |
|27000 - 27999  <br/> |[Table 5: Active Directory synchronization](#pj15_ErrorCodes_ActiveDirectory) <br/> |
|28000 - 28999  <br/> |[Table 17: Planner](#pj15_ErrorCodes_Planner) (Project portfolio analysis)  <br/> |
|29000 - 29999  <br/> |[Table 16: Optimizer](#pj15_ErrorCodes_Optimizer) (Project portfolio analysis), except 29021 is in [Table 7: Archive](#pj15_ErrorCodes_Archive) <br/> |
|30000 - 30999  <br/> |[Table 21: Resource plans](#pj15_ErrorCodes_ResourcePlans) <br/> |
|31000 - 31999  <br/> 32000 - 32100  <br/> |[Table 14: Miscellaneous](#pj15_ErrorCodes_Miscellaneous) (Auditing; not used)  <br/> Project detail pages  <br/> |
|35000 - 35999  <br/> 40000 - 40499  <br/> |[Table 30: Workflow](#pj15_ErrorCodes_Workflow) <br/> |
|40500 - 40999  <br/> 42000 - 42999  <br/> |[Table 14: Miscellaneous](#pj15_ErrorCodes_Miscellaneous) (**ExchangeSync**; internal use)  <br/> Project Web App timeline  <br/> |
|43000 - 43500  <br/> |[Table 29: User delegation](#pj15_ErrorCodes_UserDelegation) <br/> |
|50000 - 51999  <br/> |[Table 14: Miscellaneous](#pj15_ErrorCodes_Miscellaneous) (Database errors)  <br/> |

<a name="pj15_ErrorCodes_General"></a>

## Table 3. General error codes

|General error code|Description|
|:-----|:-----|
|NoError = 0; Success = 0  <br/> |No error, or success. |
|GeneralRequestInvalidParameter = 6  <br/> |One of the request nodes or parameters is either not valid, or not valid within the context of the request. |
|GeneralInvalidValue = 11  <br/> |Request value not valid; for example, a GUID specified as 0. |
|GeneralStartDateGTorEQFinishDate = 26  <br/> |The specified date range is not valid. |
|GeneralQueueOperationInProcess = 29  <br/> |Generic error for an operation still being processed in the queue. |
|GeneralUnhandledException = 42  <br/> |An unhandled exception occurred. |
|GeneralDuplicateGUIDSpecified = 66  <br/> |There is a duplicate GUID in the request. |
|GeneralDateNotValid = 69  <br/> |Dates must be in the range of 1/1/1984 to 12/12/2049. |
|GeneralCostInvalid = 70  <br/> |A cost parameter is not valid. |
|GeneralWorkInvalid = 71  <br/> |A work parameter is not valid. |
|GeneralDurationInvalid = 72  <br/> |A duration parameter is not valid. |
|GeneralUnitsInvalid = 73  <br/> |The specified unit is not valid. |
|GeneralOnlyInsertsAllowed = 74  <br/> |Only inserts are allowed. |
|GeneralOnlyUpdatesAllowed = 75  <br/> |Only updates are allowed. |
|GeneralSessionInvalid = 76  <br/> |The session parameter is not valid. |
|GeneralDependencyUidInvalid = 78  <br/> |The dependency GUID is not valid. |
|GeneralNumberInvalid = 79  <br/> |A number is not valid. |
|GeneralInvalidDataStore = 80  <br/> |The specified database does not exist. Use a database in [DataStoreEnum](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.DataStoreEnum.aspx). |
|GeneralDurationOrWorkFormatInvalid = 513  <br/> |The work duration or format is not valid. |
|GeneralRateFormatInvalid = 518  <br/> |The rate format is not valid. |
|GeneralQueueException = 9131  <br/> |Exception: There is a general error in the Queuing Service. |
|GeneralItemDoesNotExist = 10000  <br/> |A specified item does not exist. |
|GeneralLCIDInvalid = 10001  <br/> |The locale identifier (language ID) is not valid. |
|GeneralRowDoesNotExist = 10002  <br/> |The specified row in a **DataTable** does not exist. |
|GeneralInvalidColumnValue = 20000  <br/> |A column value in a **DataTable** is not valid. |
|GeneralInvalidDataRowState = 20001  <br/> |A **DataRow** state is not valid. |
|GeneralDuplicatedNames = 20004  <br/> |There is a duplicate name. Names must be unique. |
|GeneralReadOnlyColumn = 20005  <br/> |The column is read-only. |
|GeneralReadOnlyRow = 20006  <br/> |The row is read-only. |
|GeneralNotNullColumn = 20007  <br/> |The column cannot be null. |
|GeneralObjectAlreadyExists = 20008  <br/> |The object already exists. |
|GeneralInvalidObject = 20009  <br/> |The object is not valid. |
|GeneralSecurityAccessDenied = 20010  <br/> |Access is denied because of security permissions. |
|GeneralInvalidOperation = 20011  <br/> |The operation is not valid. |
|GeneralInvalidCharacters = 20012  <br/> |Some characters are not valid. In addition to the TAB character, the following characters are not valid in a project name: `\ / " : ; < > | , . ' ? * #` <br/> |
|GeneralNameTooLong = 20013  <br/> |The name is too long. |
|GeneralNameCannotBeBlank = 20014  <br/> |The name cannot be blank. Do not use a null or empty string. |
|GeneralInvalidOperationOnReadOnlyValue = 20016  <br/> |The attempted operation on a read-only value is not valid. |
|GeneralInvalidDateOverlap = 20018  <br/> |The request contains overlapping dates. |
|GeneralParameterCannotBeNull = 20020  <br/> |The parameter cannot be null. |
|GeneralDescTooLong = 20021  <br/> |The description is too long. |
|GeneralCategoryPermissionDenied = 20022  <br/> |The category permission is denied. |
|GeneralNotLicensed = 20024  <br/> |User is not licensed for Project Server. |
|GeneralGlobalPermissionDenied = 20023  <br/> |The global permission is denied. |
|GeneralActionCanceledByEventHandler = 22000  <br/> |The event handler canceled the action. |
|GeneralActionCanceledBecauseServerEventServiceNotFound = 22001  <br/> |The Project Server Event Service is not found. |
|GeneralActionCanceledBecauseServerEventServiceProblem = 22002  <br/> |There is a problem in the Project Server Event Service. |
|GeneralQueueJobFailed = 26000  <br/> |The queue job failed. |
|GeneralQueueInvalidJobUID = 26001  <br/> |The job GUID for the queue is not valid. |
|GeneralQueueInvalidTrackingUID = 26002  <br/> |The tracking GUID for the queue is not valid. |
|GeneralQueueInvalidJobInfoUID = 26003  <br/> |The job information GUID for the queue is not valid. |
|GeneralQueueInvalidCorrelationUID = 26004  <br/> |The queue correlation GUID is not valid. |
|GeneralQueueCorrelationBlocked = 26005  <br/> |The queue correlation is blocked. |
|GeneralQueueInvalidMessageType = 26006  <br/> |The queue message type is not valid. |
|GeneralQueueInvalidJobState = 26007  <br/> |The queue job state is not valid. |
|GeneralQueueInvalidGroupState = 26008  <br/> |The group state in the queue is not valid. |
|GeneralQueueInvalidGroupPriority = 26009  <br/> |The group priority in the queue is not valid. |
|GeneralQueueInvalidCorrelationPriority = 26010  <br/> |The correlation priority in the queue is not valid. |
|GeneralQueueInvalidQueueID = 26011  <br/> |The queue identification number is not valid. |
|GeneralQueueInvalidAdminAction = 26012  <br/> |The **Admin** action is not valid for the queue. |
|GeneralQueueInvalidStatType = 26013  <br/> |The queue status type is not valid. |
|GeneralQueueInvalidBlockPolicy = 26014  <br/> |The queue blocking policy is not valid. |
|GeneralQueueCannotRetryJob = 26015  <br/> |The queue cannot retry the job. |
|GeneralQueueInvalidSetting = 26016  <br/> |A setting for the queue is not valid. |
|GeneralQueueInvalidRendezvousUID = 26017  <br/> |The queue rendezvous GUID is not valid. |
|GeneralDalErrorGettingConnectionStrings = 26018  <br/> |Error getting connection strings for the data access layer (DAL). |
|GeneralDalErrorConnectingToDatabase = 26019  <br/> |Error in the DAL connecting to the database. |
|GeneralDalInvalidArgumentCountCreatingFilter = 26020  <br/> |The number of arguments for creating a filter is not valid. |
|GeneralDataTableCannotBeNull = 26024  <br/> |A **DataTable** cannot be **null**. |
|GeneralDatasetConstraints = 26025  <br/> |Error in **DataSet** constraints. |
|GeneralInvalidDataSetStructure = 26027  <br/> |The **DataSet** structure is not valid. |
|GeneralDalNoRowsUpdated = 26028  <br/> |No rows are updated in the data access layer (DAL). |
|GeneralDataTableCannotBeEmpty = 26029  <br/> |The **DataTable** cannot be empty. |
|GeneralWSSContentDBNotWritable = 26030  <br/> |Cannot write to the SharePoint content database. Either the content database is read-only or there is a lock at the site-collection level. |
|GeneralSPValidateFormDigestError = 26031  <br/> |Error validating the form digest in a Project Web App callback, usually because of a timeout. |
|GeneralDelegationActiveForCurrentUser = 26032  <br/> |The current user has an active delegation. This error is raised by web methods in the **WinProj** service for Project Professional. |

<a name="pj15_ErrorCodes_ActiveCache"></a>

## Table 4. Active cache

|Active cache error code|Description|
|:-----|:-----|
|ActiveCacheInvalidDataFormat = 12000  <br/> |The data format is not valid. |
|ActiveCacheUnsupportedDataFormatVersion = 12001  <br/> |The data format version is unsupported. |
|ActiveCacheInvalidQueuedMessageType = 12003  <br/> |The queued message type is not valid. |
|ActiveCacheNullQueuedMessage = 12004  <br/> |The queued message is null. |
|ActiveCacheQueuedMessageExecutionError = 12005  <br/> |There is an execution error for the queued message. |
|ActiveCacheInvalidDataSize = 12006  <br/> |The data size is not valid. |
|ActiveCacheQueueJobAlreadyStarted = 12007  <br/> |The queue job is already started. |
|ActiveCacheInvalidQueuedMessageFormat = 12008  <br/> |The message format in the queue is not valid. |
|ActiveCacheUnsupportedQueuedMessageVersion = 12009  <br/> |The message version in the queue is not valid. |
|ActiveCacheUnsupportedQueueDataType = 12011  <br/> |The data type in the queue is unsupported. |
|ActiveCacheInvalidVersionStampForSave = 12012  <br/> |The version stamp for the save operation is not valid. |
|ActiveCacheProjectTypeMismatch = 12013  <br/> |The project type does not match the expected type. |
|ActiveCacheDataValidationFailed = 12014  <br/> |Data validation failed. |
|ActiveCacheUnsupportedProjectProfessionalVersion = 12015  <br/> |The Project Professional version is unsupported. |
|ActiveCacheGeneralSQLException = 12016  <br/> |There is a general SQL error. |

<a name="pj15_ErrorCodes_ActiveDirectory"></a>

## Table 5. Active Directory synchronization

|Active Directory synchronization error code|Description|
|:-----|:-----|
|AdSyncUpdateTimerJobFailed = 27002  <br/> |The update timer job failed for synchronization with Active Directory directory services. |
|AdSyncDeleteTimerJobFailed = 27003  <br/> |The delete timer job failed for synchronization with Active Directory. |
|AdSyncAdConnectFail = 27006  <br/> |Cannot connect with Active Directory. |
|AdMaximumGroupsCountExceeded = 27007  <br/> |The maximum groups count was exceeded. |
|SRAInvalidVersion = 27300  <br/> |SRA invalid version. |
|SRADelayedUpgradeFailed = 27301  <br/> |The SRA asynchronous update action failed. |
|(27000 - 27999)  <br/> |Other synchronization errors for Active Directory are not enumerated within Project Server. |

<a name="pj15_ErrorCodes_Admin"></a>

## Table 6. Admin web service

|Admin web service error code|Description|
|:-----|:-----|
|AdminViewNameAlreadyExists = 16600  <br/> |The view name already exists. Names must be unique. |
|AdminViewInvalidDividerPosition = 16601  <br/> |The divider position is not valid. |
|AdminViewDataWasTampered = 16602  <br/> |The data has been altered. |
|AdminViewMaxDisplayedFieldsNumberExceeded = 16603  <br/> |The display exceeds the maximum number of fields. |
|AdminViewCannotDeleteDefaultView = 16604  <br/> |Cannot delete the default view. |
|AdminViewCannotCopyDefaultView = 16605  <br/> |Cannot copy the default view. |
|AdminLocalCustomFieldInvalid = 19011  <br/> |The local custom field is not valid. |
|AdminEnterpriseCustomFieldInvalid = 19012  <br/> |The enterprise custom field is not valid. |
|AdminNTAccountNotFound = 19032  <br/> |The Windows (NTLM) account is not found. |
|AdminUnableToMerge = 20003  <br/> |Unable to merge the data. |
|AdminDeleteArchivedProjectsFailed = 25004  <br/> |The delete operation for archived projects failed. |
|AdminUpdateArchiveScheduleFailed = 25006  <br/> |Failed to update the archive schedule. |
|AdminArchiveScheduleFailed = 28018  <br/> |The archive schedule failed. |
|AdminReadArchivedProjectsListFailed = 28019  <br/> |Failed to read the list of archived projects. |
|AdminReadArchiveScheduleFailed = 28020  <br/> |Failed to read the archive schedule. |
|AdminUserAccountNameNull = 28021  <br/> |The user account name is null. |
|AdminIsWindowsUserNull = 28022  <br/> |The Windows (NTLM) user account appears to be null. |
|AdminInvalidTimePeriodState = 28023  <br/> |The timeperiod state is not valid. |
|AdminGlobalUpdateFailed = 28024  <br/> |The enterprise global update failed during the call to **SetServerCurrency**. |
|AdminGlobalCheckedOut = 28025  <br/> |The enterprise global template is already checked out during the call to **SetServerCurrency**. |
|AdminInvalidDatabaseTimeout = 28026  <br/> |Timeout due to a database that is not valid. |
|AdminInvalidDatabaseTimeoutType = 28027  <br/> |Timeout due to a database type that is not valid. |
|AdminInvalidEntityType = 28028  <br/> |The entity type is not valid. See [EntityCollection](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.EntityCollection.aspx). |
|AdminInvalidCompatibilityModeChange = 28029  <br/> |The change to the compatibility mode is not valid. |
|AdminInvalidCompatibilityMode = 28030  <br/> |The compatibility mode is not valid. |
|AdminInvalidProjectProfessionalVersions = 28031  <br/> |The set of Project Professional versions is not valid. |
|AdminInvalidProjectProfessionalVersion = 28032  <br/> |The Project Professional version is not valid. |
|AdminTooManyProjectProfessionalVersions = 28033  <br/> |Too many Project Professional versions are specified. |
|AdminDuplicateProjectProfessionalMajorVersions = 28034  <br/> |There are duplicates in the Project Professional major versions. You can specify only one version for each major release, beginning with Project Professional 2007. |
|AdminInvalidServerFlags = 28035  <br/> |One or more flags in Project Server settings are not valid. |
|AdminNullProjectProfessionalVersions = 28036  <br/> |One or more Project Professional versions are null. |

<a name="pj15_ErrorCodes_Archive"></a>

## Table 7. Archive web service

|Archive web service (backup and restore) error code|Description|
|:-----|:-----|
|ArchiveProjectFailure = 25000  <br/> |The project archive operation failed. |
|ArchiveProjectsFailed = 25001  <br/> |Cannot save any of the projects in the Archive database. |
|ArchiveProjectFailed = 25002  <br/> |Cannot save the project archive. |
|RestoreProjectFailed = 25003  <br/> |Cannot restore the project. |
|ArchiveResourcesFailed = 25007  <br/> |Cannot save the resources archive. |
|ArchiveCustomFieldsFailed = 25008  <br/> |Cannot save the custom fields archive. |
|RestoreCustomFieldsFailed = 25009  <br/> |Cannot restore the custom fields. |
|ArchiveSystemSettingsFailed = 25010  <br/> |Cannot save system settings archive. |
|RestoreSystemSettingsFailed = 25011  <br/> |Cannot restore the system settings. |
|ArchiveCategoriesFailed = 25012  <br/> |Cannot save the security categories archive. |
|RestoreCategoriesFailed = 25013  <br/> |Cannot restore the security categories. |
|ArchiveViewsFailed = 25014  <br/> |Cannot save the views archive. |
|RestoreViewsFailed = 25015  <br/> |Cannot restore the views. |
|ArchiveGlobalProjectFailed = 25016  <br/> |Cannot save the enterprise global archive. |
|RestoreGlobalProjectFailed = 25017  <br/> |Cannot restore the enterprise globa ltemplate. |
|ArchiveInvalidRetentionPolicyValue = 25018  <br/> |The archive retention policy value is not valid. |
|ArchiveCustomFieldsFailure = 25019  <br/> |Cannot read the custom fields archive. |
|ArchiveGlobalProjectFailure = 25020  <br/> |Cannot read the enterprise global archive. |
|ArchiveResourcesFailure = 25021  <br/> |Cannot read the resources archive. |
|ArchiveSystemSettingsFailure = 25022  <br/> |Cannot read the system settings archive. |
|ArchiveViewsFailure = 25023  <br/> |Cannot read the views archive. |
|ArchiveCategoriesFailure = 25024  <br/> |Cannot read the security categories archive. |
|ResourcePlanPublishFailure = 25025  <br/> |Cannot publish the resource plan. |
|RestoreCategoriesFailure = 25026  <br/> |Cannot restore the security categories from the archive. |
|RestoreCustomFieldsFailure = 25027  <br/> |Cannot restore the custom fields from the archive. |
|RestoreGlobalProjectFailure = 25028  <br/> |Cannot restore the enterprise global template from the archive. |
|RestoreProjectFailure = 25029  <br/> |Cannot restore the project from the archive. |
|RestoreResourcesFailure = 25030  <br/> |Cannot restore the resources from the archive. |
|RestoreSystemSettingsFailure = 25031  <br/> |Cannot restore the system settings from the archive. |
|RestoreViewsFailure = 25032  <br/> |Cannot restore the views from the archive. |
|ArchiveReadProjectArchiveRetentionSettingFailed = 25033  <br/> |Failed to read the project archive retention settings. |
|RestoreResourcesFailed = 29021  <br/> |Cannot restore the resources. |

<a name="pj15_ErrorCodes_Assignments"></a>

## Table 8. Assignment

|Assignment error code|Description|
|:-----|:-----|
|AssignmentNotFound = 120  <br/> |Assignment not found. |
|AssignmentWrongTrackingMethod = 122  <br/> |The assignment has the wrong tracking method. |
|AssignmentWorkTypeInvalid = 127  <br/> |The assignment work type is not valid. |
|AssignmentRateTableInvalid = 130  <br/> |The rate table for the assignment is not valid. |
|AssignmentAlreadyExists = 131  <br/> |The assignment already exists. |
|AssignmentDuplicateSpecified = 132  <br/> |There is a duplicate assignment. |
|AssignmentUidInvalid = 133  <br/> |The assignment GUID is not valid. |
|AssignmentDelayInvalid = 134  <br/> |The assignment delay is not valid. |
|AssignmentCannotEditSummaryTask = 135  <br/> |A summary task cannot be edited for assignments. |
|AssignmentInvalid = 136  <br/> |The assignment is not valid. |
|AssignmentFieldsInvalidForBudget = 137  <br/> |The assignment fields are not valid for the budget. |
|AssignmentAlreadyAssignedToResource = 138  <br/> |The resource already had the assignment. |
|AssignmentInvalidOwner = 139  <br/> |The assignment owner is not valid. |

<a name="pj15_ErrorCodes_Calendar"></a>

## Table 9. Calendar

|Calendar error code|Description|
|:-----|:-----|
|CalendarUidInvalid = 77  <br/> |The calendar GUID is not valid. |
|CalendarOnlyOneShiftIsNull = 13000  <br/> |Only one shift is null. |
|CalendarRecurrenceDaysShouldBeNull = 13001  <br/> |Recurrence days should be null. |
|CalendarRecurrenceMonthDayShouldBeNull = 13002  <br/> |The recurrence month and day should be null. |
|CalendarRecurrenceMonthShouldBeNull = 13003  <br/> |The recurrence month should be null. |
|CalendarRecurrenceMonthShouldNotBeNull = 13004  <br/> |The recurrence month should not be null. |
|CalendarRecurrencePositionShouldBeNull = 13005  <br/> |The recurrence position should be null. |
|CalendarRecurrencePositionShouldNotBeNull = 13006  <br/> |The recurrence position should not be null. |
|CalendarRecurrenceDaysShouldNotBeNull = 13007  <br/> |The recurrence days should not be null. |
|CalendarInvalidRecurrenceFrequency = 13008  <br/> |The recurrence frequency is not valid. |
|CalendarInvalidRecurrenceType = 13009  <br/> |The recurrence type is not valid. |
|CalendarInvalidRecurrenceDays = 13010  <br/> |The recurrence days are not valid. |
|CalendarInvalidCombinationOfMonthDayAndPosition = 13011  <br/> |The combination of month, day, and position is not valid. |
|CalendarInvalidRecurrencePosition = 13012  <br/> |The recurrence position is not valid. |
|CalendarCannotModifyExceptionsForCalendarBeingDeleted = 13013  <br/> |The calendar exceptions cannot be modified when a calendar is being deleted. |
|CalendarExceptionConflict = 13014  <br/> |There is a conflict in the calendar exceptions. |
|CalendarBadDateValue = 13015  <br/> |The date is not valid. |
|CalendarNotFound = 13021  <br/> |The calendar is not found. |
|CalendarAlreadyExists = 13022  <br/> |The calendar already exists. |
|CalendarNameShouldNotBeNull = 13023  <br/> |The calendar name is null. |
|CalendarInternalError = 13025  <br/> |There is an internal error in the calendar operation. |
|CalendarNameTooLong = 13027  <br/> |The calendar name is too long. |
|CalendarInvalidCalendarName = 13028  <br/> |The calendar name is not valid. |
|CalendarStandardCalendarNotFound = 13031  <br/> |The standard calendar is not found. |
|CalendarInvalidShifts = 13032  <br/> |The shifts are not valid. |
|CalendarCannotDeleteCalendarUsedByProject = 13033  <br/> |Cannot delete a calendar that is being used in a project. |
|CalCalendarUniqueIdToDuplicateShouldBeNull = 13035  <br/> |The GUID should be null to duplicate a calendar. |
|CalendarInvalidBaseCalendarUniqueId = 13037  <br/> |The base calendar GUID is not valid. |
|CalendarInvalidUniqueIdToDuplicate = 13038  <br/> |The GUID is not valid to duplicate a calendar. |
|CalendarUnusedCalendarException = 13039  <br/> |The calendar exception does not have a corresponding calendar. Occurs when using the **UpdateResources** method if there is an entry in the **ResourceDataSet.CalendarExceptions** table, but no **BaseCalendarUniqueId** for that resource in the **Resources** table. |
|CalendarCannotDeleteStandardCalendar = 13040  <br/> |The standard calendar cannot be deleted. |
|CalendarCannotRenameStandardCalendar = 13041  <br/> |The standard calendar cannot be renamed. |
|CalendarCannotDeleteCalendarUsedByEnterpriseResource = 13042  <br/> |The calendar is in use by an enterprise resource and cannot be deleted. |
|CalendarFilterInvalid = 13043  <br/> |The filter is not valid for a calendar. |

<a name="pj15_ErrorCodes_CBS"></a>

## Table 10. CubeAdmin and Cube Build Service

|CubeAdmin and Cube Build Service (CBS) error code|Description|
|:-----|:-----|
|CBSGeneralFailure = 17001  <br/> |Failure in the Cube Build Service (CBS). This is a general error code that could result from many different causes. |
|CBSDsoNotInstalled = 17002  <br/> |The CBS needs the Decision Support Objects (DSO) component installed for Analysis Services. |
|CBSASConnectionFailure = 17003  <br/> |The CBS failed to connect to the Analysis Services server. |
|CBSOlapProcessingFailure = 17004  <br/> |The OLAP cube processing failed. |
|CBSMetadataProcessingFailure = 17005  <br/> |Processing of the cube metadata failed. |
|CBSASServerLockTimeOut = 17006  <br/> |The Analysis Services server lock timed out. |
|CBSOlapDatabaseSetupFailure = 17007  <br/> |Setup of the OLAP cube database failed. |
|CBSASEntityLimitation = 17008  <br/> |Exceeded the number of entities that Analysis Services can use. |
|CBSRequestInvalidArguments = 17009  <br/> |One or more arguments in the CBS request are not valid. |
|CBSQueueingRequestFailed = 17010  <br/> |The CBS failed to submit the job to the queue. |
|CBSUpdateCubeCalculatedMeasureDefintionError = 17011  <br/> |There is an error in a cube calculated member. |
|CBSAttemptToOverwrite = 17013  <br/> |Cannot overwrite data in the cube. |
|CBSCustomFieldCannotBeAddedAsDimension = 17014  <br/> |The custom field cannot be a cube dimension. |
|CBSCustomFieldFailedToBeAddedAsDimension = 17015  <br/> |Failed to add the custom field as a dimension in the cube. |
|CBSCustomFieldCannotBeAddedAsMeasure = 17016  <br/> |The custom field cannot be a cube measure. |
|CBSCustomFieldFailedToBeAddedAsMeasure = 17017  <br/> |Failed to add the custom field as a measure in the cube. |
|CBSDsoTranslatorNotFound = 17018  <br/> |The Decision Support Objects translator is not found. |
|CBSUpdateOlapDBOperationFailure = 17019  <br/> |Failed to update the OLAP database. |
|CBSOlapDBInvalidArguments = 17020  <br/> |One or more arguments for the OLAP database are not valid. |
|CBSOlapDatabaseReadSettingListFailed = 17021  <br/> |Failed to read the OLAP database list of settings. |
|CBSOlapDatabaseReadSettingFailed = 17022  <br/> |Failed to read the OLAP database setting. |
|CBSDeleteOlapDatabaseSetting = 17023  <br/> |Error in deleting the OLAP database setting. |
|CBSSetDefaultOlapDatabase = 17024  <br/> |Error in setting the default OLAP database. |
|CBSSetOlapDatabaseEnabled = 17025  <br/> |Error in enabling the OLAP database. |
|CBSGetDefaultOlapDatabase = 17026  <br/> |Error in getting the default OLAP database. |
|CBSCustomFieldFailedToBeAddedAsDimensionOrMeasure = 17027  <br/> |Cannot add custom field as a dimension or measure. |
|CBSOlapDatabaseAssocFieldsSettings = 17028  <br/> |Error in OLAP database associated fields settings. |
|CBSUpdateOlapDBOperationDuplicateOrFailure = 17029  <br/> |Failure or duplicate of OLAP database update operation. |
|CBSErrorReadingDefaultDatabase = 17030  <br/> |Error reading the default OLAP database. |
|CBSCreateOlapDBOperationFailure = 17031  <br/> |Failed to create the OLAP database operation. |
|CBSSetCubeFieldsSettingsFromListForGroupMeasureFailed = 17032  <br/> |Failed to set the list for group measure settings of the cube fields. |
|CBSErrorReadingCubeDepartments = 17033  <br/> |Error reading departments in the OLAP cube. |
|CBSErrorMaxOlapDatabaseCountReached = 17034  <br/> |Reached the maximum OLAP database count. |
|CBSErrorReadingCubeFieldsSettings = 17035  <br/> |Error reading cube fields settings. |

<a name="pj15_ErrorCodes_CICO"></a>

## Table 11. Check in and check out

|Check in - check out error code|Description|
|:-----|:-----|
|CICOCheckedOutToOtherUser = 10100  <br/> |Checked out to another user. |
|CICOAlreadyCheckedOutToYou = 10101  <br/> |Already checked out to you. |
|CICONotCheckedOut = 10102  <br/> |Not checked out. |
|CICOCheckedOutInOtherSession = 10103  <br/> |Checked out in another session. |
|CICOInvalidSessionGuid = 10104  <br/> |The session GUID is not valid. |
|CICOAlreadyCheckedOutInSameSession = 10105  <br/> |Already checked out in the same session. |
|CICOCannotCheckOutVisibilityModeProjectWithMppInDocLib = 10106  <br/> |Cannot check out visibility mode project with an mpp file in the doc library. |

<a name="pj15_ErrorCodes_CustomFields"></a>

## Table 12. Custom field

|Custom field error code|Description|
|:-----|:-----|
|CustomFieldInvalidPropertyType = 11500  <br/> |The property type is not valid. |
|CustomFieldInvalidScope = 11503  <br/> |The custom field scope is not valid. |
|CustomFieldScopesMustBeIdentical = 11504  <br/> |The scopes must be identical. |
|CustomFieldInvalidEntityUID = 11505  <br/> |The custom field entity GUID is not valid. |
|CustomFieldHasInvalidPropertiesForNonLookupTableCF = 11506  <br/> |The properties are not valid for a custom field with no lookup table. |
|CustomFieldNonExistentWeightsTableUID = 11507  <br/> |The weights table GUID does not exist. |
|CustomFieldInvalidName = 11508  <br/> |The custom field name is not valid. |
|CustomFieldInvalidDefault = 11510  <br/> |The default value for the custom field is not valid. |
|CustomFieldInvalidLookupTableUID = 11511  <br/> |The lookup table GUID is not valid. |
|CustomFieldTypeDoesNotMatchLookupTableMask = 11512  <br/> |Custom field type does not match lookup table mask. |
|CustomFieldCannotHaveNonLeafNodeDefault = 11513  <br/> |The custom field default value must be a leaf node. |
|CustomFieldMatchingOnlyAvailableForResources = 11514  <br/> |Matching custom field is available only for resources. |
|CustomFieldUIDCannotMatchLookupTableUID = 11516  <br/> |The GUID does not match a lookup table GUID. |
|CustomFieldUIDAlreadyExists = 11517  <br/> |The custom field GUID already exists. |
|CustomFieldIDAlreadyExists = 11518  <br/> |The custom field identification number already exists. |
|CustomFieldNameAlreadyExists = 11519  <br/> |The custom field name already exists. |
|CustomFieldInvalidEntity = 11520  <br/> |The entity is not valid for the custom field. |
|CustomFieldMaskDoesNotMatchEntityType = 11521  <br/> |The code mask does not match the entity type. |
|CustomFieldLowerOrderBitsOutOfRange = 11522  <br/> |The lower order bits are out of range. |
|CustomFieldInvalidMaxValues = 11523  <br/> |One or more maximum values are not valid. |
|CustomFieldCannotModifyCertainValuesOnceDefined = 11524  <br/> |Certain values cannot be modified after they are defined. |
|CustomFieldNonExistentPID = 11526  <br/> |The custom field property identification number does not exist. |
|CustomFieldCannotChangeBuiltInFields = 11527  <br/> |Cannot change the Project Server built-in fields, such as Cost Type, State, and RBS. |
|CustomFieldSecondaryUidCannotEqualUid = 11528  <br/> |The secondary GUID cannot equal the primary GUID. |
|CustomFieldCannotHaveSecondaryUIDorIDForThisEntityType = 11529  <br/> |The custom field cannot have a secondary GUID or a GUID for this type of entity. |
|CustomFieldNameMatchesIntrinsicField = 11530  <br/> |The custom field name matches an intrinsic field. |
|CustomFieldInvalidAggregationType = 11531  <br/> |The aggregation type is not valid. |
|CustomFieldProjectFormulaFieldsMustUseFormulaAggregation = 11532  <br/> |The project formula fields must use formula aggregation. |
|CustomFieldMustSpecifyEitherIDorUID = 11700  <br/> |Must specify the custom field identification number or GUID. |
|CustomFieldInvalidID = 11701  <br/> |The custom field identification number is not valid. |
|CustomFieldInvalidUID = 11702  <br/> |The custom field GUID is not valid. |
|CustomFieldInvalidType = 11703  <br/> |The custom field type is not valid. |
|CustomFieldInvalidTypeColumnFilledIn = 11704  <br/> |The custom field type column value is not valid. See example in [Error Code Example for WCF](#pj15_ErrorCodes_WCFExample). |
|CustomFieldCodeValueDoesNotMatchLookupTable = 11706  <br/> |The code value does not match the lookup table. |
|CustomFieldCodeValueIsNotLeafNode = 11707  <br/> |The code value is not a leaf node of the lookup table. |
|CustomFieldRowAlreadyExists = 11708  <br/> |The custom field row already exists. |
|CustomFieldRowDoesNotMatchCorrespondingDefinitionInDB = 11710  <br/> |The custom field row does not match the database definition. |
|CustomFieldCodeValueAlreadyUsed = 11711  <br/> |The code value is already used. |
|CustomFieldMaxValuesExceeded = 11712  <br/> |Maximum custom field values exceeded. |
|CustomFieldRequiredValueNotProvided = 11713  <br/> |A required custom field value is not provided. See example in [Error Code Example for WCF](#pj15_ErrorCodes_WCFExample). |
|CustomFieldCannotChangeLookupTable = 11715  <br/> |Cannot change the custom field lookup table. |
|CustomFieldFilterInvalid = 11716  <br/> |The custom field filter is not valid. |
|CustomFieldRolldownInvalidOnFormulaFields = 11717  <br/> |A roll down cannot occur on a formula custom field. |
|CustomFieldFormulaFieldCannotBeRequired = 11718  <br/> |The formula field cannot be required. |
|CustomFieldFormulaFieldCannotBeWorkflowControlled = 11719  <br/> |The formula field cannot be controlled by a workflow. |
|CustomFieldCannotSetValueOnFormulaFields = 11720  <br/> |Cannot set value on formula fields. |
|CustomFieldNewPerRequestLimitExcedeed = 11721  <br/> |Exceeded request limit for new custom fields. The limit is [NEW_CF_PER_REQUEST_LIMIT](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.CustomField.NEW_CF_PER_REQUEST_LIMIT.aspx) in one request. |
|CustomFieldNameIsReservedName = 11722  <br/> |A custom field name cannot be a reserved name. |
|CustomFieldNameInvalidForOlapMeasure = 11723  <br/> |The custom field name is not valid for an OLAP cube measure. |
|CustomFieldNameInvalidForOlapDimension = 11724  <br/> |The custom field name is not valid for an OLAP cube dimension. |
|CustomFieldSettingsInvalidForOlapMeasure = 11725  <br/> |The custom field settings are not valid for an OLAP cube measure. |
|CustomFieldSettingsInvalidForOlapDimension = 11726  <br/> |The custom field settings are not valid for an OLAP cube dimension. |
|CustomFieldCannotAddRelativeImportanceField = 11727  <br/> |Cannot add a relative importance field. |
|CustomFieldCannotAddProjectImpactField = 11728  <br/> |Cannot add a project impact field. |
|CustomFieldInvalidDepartmentUid = 11731  <br/> |The department GUID in the custom field is not valid. |
|CustomFieldCannotModifyDepartmentUidOnBuiltinFields = 11732  <br/> |The department GUID cannot be modified on built-in custom fields. |
|CustomFieldCannotHaveBothLookupTableAndMultilineText = 11733  <br/> |A custom field cannot include both a lookup table and multiline text. |
|CustomFieldCannotHaveBothFormulaAndMultilineText = 11734  <br/> |A custom field cannot include both a formula and multiline text. |
|CustomFieldDescriptionExceedsLimit = 11735  <br/> |The custom field description is too long. Maximum length of the **MD_PROP_DESCRIPTION** property is 1000 characters. |
|CustomFieldOnlyTextFieldsCanHaveMultilineText = 11736  <br/> |Only text custom fields can have multiline text. |
|CustomFieldOnlyProjectFieldsCanHaveMultilineText = 11737  <br/> |Only project custom fields can have multiline text. |
|CustomFieldCannotChangeWorkflowControlledBehaviorForNonProjectCustomFields = 11738  <br/> |A custom field cannot change the behavior of non-project custom fields that are controlled by a workflow. |
|CustomFieldIsWorkflowControlledAndCannotBeChanged = 11739  <br/> |The custom field is controlled by a workflow and cannot be changed. |
|CustomFieldCannotHaveRequiredFlagWhenWorkflowControlledFlagIsSet = 11740  <br/> |The custom field cannot be required when it is controlled by a workflow. |
|CustomFieldFormulaCreatesCircularReference = 11742  <br/> |The custom field formula creates a circular reference. |
|CustomFieldFormulaContainsInvalidFieldReference = 11743  <br/> |The custom field formula contains a field reference that is not valid. |
|CustomFieldFormulaContainsErrors = 11744  <br/> |The custom field formula contains one or more errors. |
|CustomFieldLocalCustomFieldNotDefined = 11745  <br/> |The local custom field is not defined. |
|CustomFieldGraphicalIndicatorContainsErrors = 11746  <br/> |The custom field graphical indicator contains errors. |
|CustomFieldGraphicalIndicatorContainsInvalidFieldReference = 11747  <br/> |The custom field graphical indicator contains a field reference that is not valid. |
|CustomFieldGraphicalIndicatorTypeMismatch = 11748  <br/> |There is a type mismatch for the custom field graphical indicator. |
|CustomFieldFormulaFieldCannotReferenceWorkflowControlledField = 11749  <br/> |A field in the formula cannot reference a field controlled by a workflow. |
|CustomFieldWorkflowCustomFieldBeingReferencedByFormula = 11750  <br/> |A formula is trying to reference a workflow custom field. |

<a name="pj15_ErrorCodes_LookupTables"></a>

## Table 13. Lookup table

|Lookup table error code|Description|
|:-----|:-----|
|LookupTableMaskNotDefined = 11000  <br/> |The lookup table code mask is not defined. |
|LookupTableMaskHasTooManyValues = 11001  <br/> |The lookup table code mask has too many values. |
|LookupTableMaskHasGaps = 11002  <br/> |The lookup table code mask has gaps. |
|LookupTableMaskSequenceTypeLimitedToOneLevelDeep = 11003  <br/> |The code mask sequence type is limited to one level. |
|LookupTableMaskSequenceTypeInvalid = 11004  <br/> |The code mask sequence type is not valid. |
|LookupTableMaskSequenceRequiresAnyLength = 11005  <br/> |The code mask sequence requires a length of  _Any_. |
|LookupTableMaskSeparatorTooLong = 11006  <br/> |The code mask separator has too many characters. |
|LookupTableMaskLevelMustBeBlankAcrossLCIDs = 11007  <br/> |The code mask level must be blank across the locale identifiers (language IDs). |
|LookupTableMaskSeparatorInvalid = 11008  <br/> |A code mask separator character is not valid. |
|LookupTableMaskBlankSeparatorInvalidAfterAnyLengthSequence = 11009  <br/> |A blank separator character is not valid after a sequence length of  _Any_. |
|LookupTableMaskSequenceLengthInvalid = 11010  <br/> |The code mask sequence length is not valid. |
|LookupTableMaskLevelMustBeOneOrMore = 11011  <br/> |The code mask must be level 1 or greater. |
|LookupTableItemDoesNotFitMask = 11050  <br/> |The lookup table item does not fit the code mask definition. |
|LookupTableItemContainsSeparator = 11051  <br/> |The lookup table item contains a separator character. |
|LookupTableItemFullValueTooLong = 11052  <br/> |The full value of the lookup table item is too long. |
|LookupTableDuplicateSiblingsDisallowed = 11053  <br/> |Duplicate siblings in the lookup table are not allowed. |
|LookupTableSortOrderIndexInvalid = 11054  <br/> |The lookup table sort order index is not valid. |
|LookupTableSortOrderIndexDuplicate = 11055  <br/> |Duplicate lookup table sort order index. |
|LookupTableSortOrderTypeInvalid = 11056  <br/> |The lookup table sort order type is not valid. |
|LookupTableSortOrderMustComeAfterParentSortOrder = 11057  <br/> |The sort order must come after the parent sort order. |
|LookupTableSortOrderMustComeBeforeParentNextSiblingSortOrder = 11058  <br/> |The sort order must come before the parent of the next sibling sort order. |
|LookupTableInvalidCookieLength = 11060  <br/> |The cookie length for a lookup table is not valid. |
|LookupTableMustHaveValuesForPrimaryLCIDorJustOneValue = 11061  <br/> |The lookup table must have values for the primary locale identifier (language ID), or just one value. When you create a multilanguage lookup table, for example, add only one mask value for each level, or first add the value for the primary LCID. |
|LookupTableLCIDNotSupportedInLookupTableLanguages = 11062  <br/> |The locale identifier (language ID) is not included in lookup table languages. |
|LookupTableInvalidDescriptionLength = 11063  <br/> |The description length of a lookup table item is not valid. |
|LookupTableCannotChangeBuiltInTables = 11064  <br/> |Cannot change the built-in lookup tables. |
|LookupTableCannotChangeTypeOnceCreated = 11065  <br/> |Cannot change the lookup table type after the lookup table is created. |
|LookupTableCannotDeleteLTWithDependantCustomField = 11066  <br/> |Cannot delete a lookup table that is used in a custom field. |
|LookupTableAllLevelsNotFilled = 11067  <br/> |All lookup table levels must be filled. |
|LookupTableDuplicateName = 11068  <br/> |Lookup table names must be unique. |
|LookupTableInvalidName = 11069  <br/> |The lookup table name is not valid. |
|LookupTableDuplicateSiblingPhoneticsDisallowed = 11071  <br/> |Cannot have duplicate sibling phonetics in a lookup table. |
|LookupTableItemInvalidLookupTable = 11073  <br/> |An item in the lookup table is not valid. |
|LookupTableInvalidPhoneticsLength = 11074  <br/> |The length of the phonetics field is not valid. |
|LookupTableAlreadyExists = 11076  <br/> |The lookup table already exists. |
|LookupTableInvalidUID = 11078  <br/> |The lookup table GUID is not valid. |
|LookupTableFilterInvalid = 11079  <br/> |The lookup table filter is not valid. |
|LookupTableLanguageParameterInvalidWithXmlFilter = 11080  <br/> |A language parameter is not valid with a lookup table  _xmlFilter_ parameter. |
|LookupTableInvalidParentStructUid = 11081  <br/> |The GUID for a lookup table parent structure is not valid. |
|LookupTableItemContainsListSeparator = 11082  <br/> |The lookup table item contains a list separator. |
   
Error codes in Table 14 include items for project detail pages (PDPs), Exchange synchronization, the Project Web App timeline, and database errors. Many of the miscellaneous error codes in Table 14 are used internally.
  
> [!NOTE]
> The auditing error codes are not used in Project Server 2013. 

<a name="pj15_ErrorCodes_Miscellaneous"></a>

## Table 14. Miscellaneous error codes

|Miscellaneous error code|Description|
|:-----|:-----|
|AuditingUpdateFailure = 31000  <br/> |Not used. |
|AuditingCannotDeleteFeature = 31001  <br/> |Not used. |
|AuditingCannotAddFeature = 31002  <br/> |Not used. |
|AuditingFeatureIsNoLongerAudited = 31003  <br/> |Not used. |
|AuditingItemIsNotYetAvailable = 31004  <br/> |Not used. |
|AuditingInvalidFeatureUid = 31005  <br/> |Not used. |
|AuditingInvalidStoreForSelectedFeature = 31006  <br/> |Not used. |
|AuditingInvalidStore = 31007  <br/> |Not used. |
|AuditingVersionNameTooLong = 31008  <br/> |Not used. |
|AuditingBeginVersionFailure = 31009  <br/> |Not used. |
|AuditingEndVersionFailure = 31010  <br/> |Not used. |
|ProjectDetailPagesStrategicImpactRatingRequired = 32000  <br/> |A strategic impact rating is required for the project detail page. |
|ProjectDetailPagesMissingPDPLinks = 32001  <br/> |Missing links to the project detail pages. |
|ProjectDetailPagesUnavailableWorker = 32002  <br/> |Project drilldown load failed. No workers available. |
|ProjectDetailPagesFailedToLoadProjectInWorker = 32003  <br/> |The worker failed to load. |
|AppPermissionInvalidAppPermissionId = 32300  <br/> |There is a problem with the app permission id. |
|InvariantValidationPSIFailed = 40000  <br/> |Returned by **PWA** methods if any private methods return **ValidationMethodFailed**. Internal use. |
|ValidationMethodFailed = 40001  <br/> |Returned by private **PWA** methods when they detect database inconsistencies. Internal use. |
|GeneralExchangeSyncError = 40500  <br/> |General error in the Microsoft Exchange synchronization. Internal use. |
|ExchangeSyncRootFolderCreationFailed = 40501  <br/> |Failed to create the root folder in Microsoft Exchange synchronization. |
|ExchangeSyncTaskFolderCreationFailed = 40502  <br/> |Failed to create the task folder. |
|ExchangeSyncCouldNotGetRootFolder = 40503  <br/> |Could not get the root folder. |
|ExchangeSyncCouldNotLoadTaskObject = 40504  <br/> |Could not load the task object. |
|ExchangeSyncNewExchangeTaskCreationFailed = 40505  <br/> |Creation of a new task failed in Exchange synchronization. |
|ExchangeSyncFailedToUpdateCacheForUser = 40506  <br/> |Failed to update the Exchange synchronization cache for the user. |
|ExchangeSyncFailedToUpdateExchangeTask = 40507  <br/> |Failed to update the task in Microsoft Exchange. |
|ExchangeSyncSubscriptionUpdateFailed = 40508  <br/> |Failed to update the Exchange synchronization subscription. |
|ExchangeSyncEWSUrlFailed = 40509  <br/> |The Microsoft Exchange web service URL failed. |
|ExchangeSyncExchangeUrlRefreshFailed = 40510  <br/> |Failed to refresh the Exchange URL. |
|ExchangeSyncExchangeSubscriptionUpdateForUserFailed = 40511  <br/> |Failed to update the Exchange subscription for the user. |
|ExchangeSyncGeneralProcessingFailure = 40512  <br/> |General processing failure in Microsoft Exchange synchronization. |
|ExchangeSyncDeletionOfTasksInExchangeFailure = 40513  <br/> |Failed to delete tasks in Exchange synchronization. |
|ExchangeSyncAttemptedSyncOfInvalidConfiguredResource = 40514  <br/> |Tried to synchronize a resource with a configuration that is not valid. |
|ExchangeSyncRetrievalOfEWSUrlCausedException = 40515  <br/> |An exception occurred during retrieval of the Exchange web service. |
|TimelineViewDataDoesNotExist = 42000  <br/> |Data does not exist for the timeline view in Project Web App. |
|DatabaseUndefinedError = 50000  <br/> |The database is not defined. |
|DatabaseCannotInsertDuplicateKeyError = 50001  <br/> |The database cannot insert a duplicate key. |

<a name="pj15_ErrorCodes_Notifications"></a>

## Table 15. Notification

|Notification error code|Description|
|:-----|:-----|
|NotificationReminderUnknown = 16050  <br/> |Unknown reminder notification. |
|NotificationReminderParentNotSubscribed = 16051  <br/> |There is no subscription to the parent of the reminder notification. |
|NotificationReminderParentNotFound = 16052  <br/> |Parent of the reminder notification is not found. |
|NotificationReminderChildStillSubscribed = 16053  <br/> |There is still a subscription to the child of the notification reminder. |
|NotificationReminderChildNotFound = 16054  <br/> |Child of the reminder notification is not found. |
|NotificationEMailDeliveryFailed = 16080  <br/> |Notification email message delivery failed. |
|NotificationQueueMessageFailed = 16082  <br/> |Notification queue message failed. |
|NotificationXSLTTransformationError = 16084  <br/> |Error in the notification XSLT transformation. |
   
All error codes in Table 16 are for the Optimizer, which is a component used in project portfolio analysis.

<a name="pj15_ErrorCodes_Optimizer"></a>

## Table 16. Optimizer (project portfolio analysis)

|Optimizer error code|Description|
|:-----|:-----|
|OptimizerDepInvalidDepType = 29000  <br/> |The optimizer **DEPENDENCY_TYPE** value in the [OptimizerDependencyDataSet.OptimizerDependenciesRow](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.OptimizerDependencyDataSet.OptimizerDependenciesRow.aspx) is not valid. See [Optimizer.DependencyTypes](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Optimizer.DependencyTypes.aspx). |
|OptimizerDepInvalidEntityType = 29001  <br/> |The entity type is not valid. See the [Entities](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.EntityCollection.Entities.aspx) property. |
|OptimizerDepInvalidPosition = 29003  <br/> |The [POSITION](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.OptimizerDependencyDataSet.OptimizerDependencyDetailsRow.POSITION.aspx) value is not valid. |
|OptimizerDepDuplicateDependentProjects = 29004  <br/> |There are duplicate projects in the [OptimizerDependencyDataSet.OptimizerDependencyDetailsDataTable](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.OptimizerDependencyDataSet.OptimizerDependencyDetailsDataTable.aspx). |
|OptimizerDepInvalidDependency = 29005  <br/> |The Optimizer dependency is not valid. |
|OptimizerDepCircularDependency = 29006  <br/> |There is a circular dependency. |
|OptimizerCannotDeleteDependency = 29007  <br/> |The dependency cannot be deleted. |
|OptimizerCannotCreateDependency = 29008  <br/> |The dependency cannot be created. |
|OptimizerCannotUpdateDependency = 29009  <br/> |The dependency cannot be updated. |
|OptimizerCannotCreateMultipleDependencies = 29010  <br/> |Cannot create multiple dependencies. |
|OptimizerCannotUpdateMultipleDependencies = 29011  <br/> |Cannot update multiple dependencies. |
|OptimizerEngineMatrixNotFilled = 29100  <br/> |The Optimizer does not have enough data for calculation. |
|OptimizerEngineCustomFieldIsNotAConstraint = 29101  <br/> |The custom field is not a constraint for the Optimizer. |
|OptimizerCouldNotCalculatePrioritiesFromCustomFields = 29102  <br/> |Cannot calculate priorities from the specified custom fields. |
|OptimizerEngineBinaryInfeasibleSolution = 29103  <br/> |The Optimizer calculation results in an infeasible solution. |
|OptimizerEngineBinaryNumericalError = 29104  <br/> |There is a numerical error in the Optimizer calculation. |
|OptimizerEngineBinaryTimedOut = 29105  <br/> |The Optimizer calculation timed out. |
|OptimizerEngineBinaryMaxedIterations = 29106  <br/> |The Optimizer calculation reached the maximum number of iterations. |
|OptimizerEngineBinarySubOptimal = 29107  <br/> |The Optimizer calculation results are not optimal. |
|OptimizerEngineBinaryInternalError = 29108  <br/> |There is an internal error in the Optimizer calculation. |
|OptimizerInvalidRange = 29200  <br/> |The date range for the optimizer is not valid. |
|OptimizerNonNormalizedWeights = 29201  <br/> |**WEIGHT** values in the [AnalysisDataSet.AnalysisPriorityDataDataTable](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.AnalysisDataSet.AnalysisPriorityDataDataTable.aspx) are not normalized. |
|OptimizerCannotEditPrioritization = 29300  <br/> |Cannot edit the driver prioritization. |
|OptimizerCannotDeletePrioritization = 29301  <br/> |Cannot delete the driver prioritization. |
|OptimizerCannotCreatePrioritization = 29302  <br/> |Cannot create the driver prioritization. |
|OptimizerCannotUpdatePrioritization = 29303  <br/> |Cannot update the driver prioritization. |
|OptimizerCannotCalculateDriverPriorities = 29304  <br/> |Cannot calculate driver priorities. |
|OptimizerCannotCreateMultiplePrioritizations = 29305  <br/> |Cannot create multiple driver prioritizations. |
|OptimizerCannotUpdateMultiplePrioritizations = 29306  <br/> |Cannot update multiple driver prioritizations. |
|OptimizerDriverRelationsNotFilled = 29307  <br/> |The DriverRelationsRow data is not complete. |
|OptimizerDriversNotFilled = 29308  <br/> |There is not enough information in the project drivers for a solution. |
|OptimizerDriverRelationsInvalidInversedValue = 29309  <br/> |There are inverse values in the [DriverPrioritizationDataSet.DriverRelationsRow](https://msdn.microsoft.com/library/WebSvcDriver.DriverPrioritizationDataSet.DriverRelationsRow.aspx). |
|OptimizerCannotCreatePrioritizationUsingInactiveDrivers = 29310  <br/> |There is an inactive driver specified in the [DriverPrioritizationDataSet.DriverRelationsRow](https://msdn.microsoft.com/library/WebSvcDriver.DriverPrioritizationDataSet.DriverRelationsRow.aspx). Check the **DRIVER1_UID** and **DRIVER2_UID** properties. |
|OptimizerCannotChangePrioritizationType = 29311  <br/> |Cannot change the prioritization type. |
|OptimizerCannotSpecifyPriorityValuesForCalculatedPrioritizations = 29312  <br/> |If a priority is calculated, you cannot specify the priority value. |
|OptimizerCannotNormalizePriorityValues = 29313  <br/> |Priority values cannot be normalized. |
|OptimizerTooManyDriversInPrioritization = 29314  <br/> |There are too many business drivers in the prioritization. |
|OptimizerInvalidProjectImpactValue = 29400  <br/> |The project impact value is not valid. |
|OptimizerCannotDeleteDriver = 29401  <br/> |The project driver cannot be deleted. |
|OptimizerCannotCreateDriver = 29402  <br/> |The project driver cannot be created. |
|OptimizerCannotUpdateDriver = 29403  <br/> |The project driver cannot be updated. |
|OptimizerCannotEditDriver = 29404  <br/> |The project driver cannot be edited. |
|OptimizerCannotCreateMultipleDrivers = 29405  <br/> |Cannot create multiple drivers. |
|OptimizerCannotUpdateMultipleDrivers = 29406  <br/> |Cannot update multiple drivers. |
|OptimizerInvalidRelativeImportanceValue = 29407  <br/> |The relative importance value is not valid. |
|OptimizerInvalidDriverUid = 29500  <br/> |The driver GUID is not valid. |
|OptimizerInvalidEntityType = 29501  <br/> |The entity type is not valid for the Optimizer. |
|OptimizerInvalidProjectUid = 29502  <br/> |The project GUID is not valid. |
|OptimizerInvalidCustomFieldUid = 29503  <br/> |The custom field GUID is not valid for the Optimizer. |
|OptimizerInvalidHardConstraintUid = 29504  <br/> |The hard constraint GUID is not valid. |
|OptimizerInvalidAnalysisUid = 29505  <br/> |The analysis GUID is not valid. |
|OptimizerDriverFilterInvalid = 29506  <br/> |The driver filter is not valid. |
|OptimizerPrioritizationFilterInvalid = 29507  <br/> |The prioritization filter is not valid. |
|OptimizerCannotLoadOptimizationEngine = 29508  <br/> |The Optimizer calculation engine cannot be loaded. |
|OptimizerAnalysisFilterInvalid = 29509  <br/> |The analysis filter is not valid. |
|OptimizerSolutionFilterInvalid = 29510  <br/> |The solution filter for the Optimizer is not valid. |
|OptimizerDependenciesFilterInvalid = 29511  <br/> |The dependencies filter for the Optimizer is not valid. |
|OptimizerInvalidSolutionUid = 29512  <br/> |The solution GUID for the Optimizer is not valid. |
|OptimizerInvalidViewUid = 29513  <br/> |The view GUID for the Optimizer is not valid. |
|OptimizerInvalidAnalysisType = 29600  <br/> |The type of portfolio analysis is not valid. |
|OptimizerInvalidPrioritizationType = 29601  <br/> |The prioritization type for the Optimizer is not valid. |
|OptimizerCannotDeleteAnalysis = 29602  <br/> |Cannot delete the portfolio analysis. |
|OptimizerCannotCreateAnalysis = 29603  <br/> |Cannot create the portfolio analysis. |
|OptimizerCannotUpdateAnalysis = 29604  <br/> |Cannot update the portfolio analysis. |
|OptimizerInvalidPrioritizationUid = 29607  <br/> |The prioritization GUID is not valid. |
|OptimizerCannotCreateMultipleAnalyses = 29608  <br/> |Cannot create multiple portfolio analyses. |
|OptimizerCannotUpdateMultipleAnalyses = 29609  <br/> |Cannot update multiple portfolio analyses. |
|OptimizerCannotCalculateProjectPriorities = 29610  <br/> |The Optimizer cannot calculate project priorities. |
|OptimizerCannotDeleteAnalysisProjectImpact = 29611  <br/> |Cannot delete project impact in the portfolio analysis. |
|OptimizerCannotChangeAnalysisProjects = 29612  <br/> |Cannot change projects in the portfolio analysis. |
|OptimizerCannotChangePriorityData = 29613  <br/> |Cannot change priority data. |
|OptimizerCannotEditAnalysis = 29614  <br/> |Cannot edit the portfolio analysis. |
|OptimizerInvalidPlannerData = 29615  <br/> |The Planner data is not valid for the Optimizer. |
|OptimizerCannotChangeImpactData = 29616  <br/> |Cannot change the project impact data. |
|OptimizerInvalidProjectsNumber = 29617  <br/> |The number of projects is not valid. |
|OptimizerCannotAddImpactCFUIDToCFAnalysis = 29618  <br/> |Cannot add the project impact custom field GUID ([PROJECT_IMPACT_CF_UID](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.AnalysisDataSet.AnalysisRow.PROJECT_IMPACT_CF_UID.aspx) ) for portfolio analysis. |
|OptimizerInvalidDepartmentUid = 29619  <br/> |The [DEPARTMENT_UID](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.AnalysisDataSet.AnalysisRow.DEPARTMENT_UID.aspx) is not valid. |
|OptimizerTooManyProjectsInAnalysis = 29620  <br/> |There are too many projects in the analysis. |
|QueueAnalysisCannotDeleteAnalysis = 29680  <br/> |The [QueueDeleteAnalyses](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueDeleteAnalyses.aspx) method cannot delete the analysis. |
|QueueAnalysisCannotCreateAnalysis = 29681  <br/> |The [QueueCreateAnalysis](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueCreateAnalysis.aspx) method cannot create the analysis. |
|QueueAnalysisCannotUpdateAnalysis = 29682  <br/> |The [QueueUpdateAnalysis](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueUpdateAnalysis.aspx) method cannot update the analysis. |
|AnalysisMismatchedJobList = 29690  <br/> |The analysis job list is mismatched. |
|OptimizerInvalidForceInLookupTableUid = 29691  <br/> |The lookup table GUID cannot be forced in. |
|OptimizerInvalidForceOutLookupTableUid = 29692  <br/> |The lookup table GUID cannot be forced out. |
|OptimizerDuplicateForceLookupTableUids = 29693  <br/> |There are duplicate forced lookup table GUIDs. |
|OptimizerInvalidDecisionResult = 29701  <br/> |The decision result is not valid. |
|OptimizerInvalidForcedStatus = 29702  <br/> |The forced status is not valid. |
|OptimizerCannotDeleteSolution = 29703  <br/> |The [QueueDeleteOptimizerSolutions](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueDeleteOptimizerSolutions.aspx) method cannot delete the Optimizer solution. |
|OptimizerCannotCreateSolution = 29704  <br/> |The [QueueCreateOptimizerSolution](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueCreateOptimizerSolution.aspx) method cannot create a the Optimizer solution. |
|OptimizerCannotUpdateSolution = 29705  <br/> |The [QueueUpdateAnalysis](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.QueueUpdateAnalysis.aspx) method cannot update the Optimizer solution. |
|OptimizerCannotCalculateSolutionStrategicAlignment = 29706  <br/> |The Optimizer cannot calculate the solution for strategic alignment. |
|OptimizerCannotCreateMultipleSolutions = 29707  <br/> |The Optimizer cannot create multiple solutions. |
|OptimizerCannotUpdateMultipleSolutions = 29708  <br/> |The Optimizer cannot update multiple solutions. |
|OptimizerCannotAddPrioritizationToCFAnalysis = 29709  <br/> |The Optimizer cannot add a prioritization to a custom field for the analysis. |
|OptimizerTableIsReadOnly = 29710  <br/> |The Optimizer table is read-only. |
|OptimizerSolutionCreateMessageFailed = 29711  <br/> |The Optimizer failed to make a "solution created" message. |
|OptimizerSolutionDeleteMessageFailed = 29712  <br/> |The Optimizer failed to make a "solution deleted" message. |
|OptimizerCannotCalculateEfficientFrontier = 29714  <br/> |The Optimizer cannot calculate the efficient frontier for the analysis. |
|OptimizerCannotUpdateSolutionProperties = 29715  <br/> |Cannot update the solution properties. |
|OptimizerInvalidConstraintPosition = 29716  <br/> |The constraint position in the Optimizer is not valid. |
|OptimizerInvalidHardConstraintPosition = 29717  <br/> |The hard constraint position in the Optimizer is not valid. |
|OptimizerInvalidConstraintLimit = 29718  <br/> |The constraint limit in the Optimizer is not valid. |
|OptimizerInvalidConstraintValue = 29719  <br/> |The constraint value is not valid. |
|OptimizerInvalidSolutionProjectsSet = 29720  <br/> |The set of projects in the solution is not valid. |
|OptimizerCannotCommitSolution = 29721  <br/> |The [CommitOptimizerSolution](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.CommitOptimizerSolution.aspx) method cannot commit the solution. |
|OptimizerInvalidInputData = 29723  <br/> |The input data for the Optimizer is not valid. |
|OptimizerInvalidConstraintSet = 29724  <br/> |The constraint set for the Optimizer is not valid. |
|OptimizerCannotUpdateAnalysisMetrics = 29725  <br/> |Cannot update the analysis metrics. |
|OptimizerSolutionMismatchedJobList = 29726  <br/> |The job list in the solution is mismatched. |
|OptimizerInvalidForceLookupTableValue = 29727  <br/> |The force lookup table value is not valid. |
|OptimizerCannotCreateSolutionWhileAnalysisUpdateIsPending = 29728  <br/> |Cannot create an Optimizer solution while an analysis update is pending. |
|OptimizerProjectSelectorAtLeastOne = 29800  <br/> |There must be at least one project selected for the Optimizer. |
   
The error codes in Table 17 are for the Planner, which is a component used in project portfolio analysis.

<a name="pj15_ErrorCodes_Planner"></a>

## Table 17. Planner (project portfolio analysis)

|Planner error code|Description|
|:-----|:-----|
|PlannerSolutionMessageDeleteFailed = 28000  <br/> |Queue error: the message to delete the planner solution failed. |
|PlannerSolutionMessageCreateFailed = 28001  <br/> |Queue error: the message to create the planner solution failed. |
|PlannerInvalidRBSValueUid = 28002  <br/> |The GUID for a resource breakdown structure value is not valid in the Planner data. |
|PlannerInvalidCustomFieldUid = 28003  <br/> |The GUID for a custom field is not valid. |
|PlannerHorizonInvalid = 28004  <br/> |The Planner time horizon is not valid. A time horizon is the period specified for capacity planning. |
|PlannerHorizonTooBig = 28005  <br/> |The time horizon is too far in the future. |
|PlannerInvalidBookingType = 28006  <br/> |The resource booking type is not valid. |
|PlannerInvalidTimeScale = 28007  <br/> |The time scale is not valid. |
|PlannerInvalidProjectSNET = 28008  <br/> |The "start no earlier than" date for the project is not valid. |
|PlannerInvalidProjectFNLT = 28009  <br/> |The "finish no later than" date for the project is not valid. |
|PlannerInvalidAnalysisStartDate = 28010  <br/> |The [START_DATE](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionProjectRequirementsByRoleRow.START_DATE.aspx) for the project is not valid. |
|PlannerInvalidAnalysisDuration = 28011  <br/> |The [DURATION](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionProjectsRow.DURATION.aspx) is not valid for portfolio analysis. |
|PlannerInvalidHorizonStartDate = 28012  <br/> |The start date of the time horizon is not valid. |
|PlannerInvalidHorizonEndDate = 28013  <br/> |The end date of the time horizon is not valid. |
|PlannerInvalidHorizonTimeScale = 28014  <br/> |The time scale of the time horizon is not valid. |
|PlannerInvalidAnalysisType = 28015  <br/> |The type of portfolio analysis is not valid. |
|PlannerHorizonStartDateDoesNotMatchTimeScale = 28016  <br/> |The start date of the time horizon does not match the time scale. |
|PlannerHorizonEndDateDoesNotMatchTimeScale = 28017  <br/> |The end date of the time horizon does not match the time scale. |
|PlannerAnalysisNoCapacityData = 28037  <br/> |There is no resource capacity data for the portfolio analysis. |
|PlannerInvalidSolutionUid = 28100  <br/> |The analysis solution GUID is not valid. |
|PlannerInvalidOptimizerSolutionUid = 28101  <br/> |The Optimizer solution GUID is not valid. |
|PlannerInvalidLookupTableValueUid = 28102  <br/> |The lookup table value GUID is not valid. |
|PlannerInvalidEfficientFrontierUid = 28103  <br/> |The [FRONTIER_UID](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionEfficientFrontierRow.FRONTIER_UID.aspx) is not valid. |
|PlannerInvalidProjectUid = 28104  <br/> |The project GUID is not valid. |
|PlannerInvalidAllocationThreshold = 28105  <br/> |The allocation threshold is not valid. |
|PlannerInvalidHiringType = 28109  <br/> |The [HIRING_TYPE](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionsRow.HIRING_TYPE.aspx) is not valid. See [Planner.PlannerHiringType](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Planner.PlannerHiringType.aspx). |
|PlannerInvalidConstraintType = 28110  <br/> |The [CONSTRAINT_TYPE](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionsRow.CONSTRAINT_TYPE.aspx) is not valid. See [Planner.ConstraintType](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Planner.ConstraintType.aspx). |
|PlannerInvalidConstraintValue = 28111  <br/> |The [CONSTRAINT_VALUE](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionsRow.CONSTRAINT_VALUE.aspx) is not valid. |
|PlannerInvalidRateTable = 28112  <br/> |The [RATE_TABLE](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionsRow.RATE_TABLE.aspx) is not valid. |
|PlannerInvalidSolutionForConstraint = 28113  <br/> |The Planner solution is not valid for the constraint. Too many projects are forced in during the first pass of the planner. |
|PlannerInvalidSolutionForDependencies = 28114  <br/> |The Planner solution is not valid because there are too many projects for considering business dependencies or conflicts. This error occurs in the second pass. |
|PlannerInvalidSolutionForScheduling = 28115  <br/> |The Planner solution is not valid for scheduling because there are circular dependencies. |
|PlannerInvalidAnalysisUid = 28116  <br/> |The [ANALYSIS_UID](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PlannerSolutionDataSet.SolutionsRow.ANALYSIS_UID.aspx) is not valid. |
|PlannerInvalidProjectStartDate = 28200  <br/> |The project start date is not valid. |
|PlannerInvalidProjectEndDate = 28201  <br/> |The project end date is not valid. |
|PlannerInvalidProjectDuration = 28202  <br/> |The project duration is not valid. |
|PlannerInvalidProjectFNLTDate = 28203  <br/> |The "finish no later than" date for the project is not valid. |
|PlannerInvalidProjectSNETDate = 28204  <br/> |The "start no earlier than" date for the project is not valid. |
|PlannerCannotCreateSolution = 28900  <br/> |The Planner cannot create a solution. |
|PlannerCannotUpdateSolution = 28901  <br/> |The Planner cannot update the solution. |
|PlannerCannotDeleteSolution = 28902  <br/> |The Planner cannot delete the solution. |
|PlannerCannotCreateMultipleSolutions = 28903  <br/> |The Planner cannot create multiple solutions. |
|PlannerCannotUpdateMultipleSolutions = 28904  <br/> |The Planner cannot update multiple solutions. |
|PlannerTableIsReadOnly = 28907  <br/> |The **DataTable** is read-only. |
|PlannerCannotCommitSolution = 28908  <br/> |The Planner cannot commit the solution to the database. |
|PlannerFieldIsReadOnly = 28909  <br/> |The field is read-only. |
|PlannerProjectNotInParentSolution = 28910  <br/> |The project is not in the parent solution. |
|PlannerProjectNotSelectedInParentSolution = 28911  <br/> |The project is not selected in the parent solution. |
|PlannerProjectNotInParentAnalysis = 28912  <br/> |The project is not in the parent portfolio analysis. |
|PlannerProjectBeyondHorizon = 28913  <br/> |The project extends beyond the time horizon. |
|PlannerResourceAllocationInternalError = 28915  <br/> |There is an internal error in the resource allocation. |
|PlannerResourceAllocationInfeasibleSolution = 28916  <br/> |The resource allocation is an infeasible solution. |
|PlannerProjectEndDateViolatesDependency = 28917  <br/> |The project end date violates a dependency. |
|PlannerInvalidProjectsSet = 28919  <br/> |The set of projects is not valid. |
|PlannerInvalidInputData = 28920  <br/> |The Planner has input data that is not valid. |
|PlannerDecimalOverflowError = 28921  <br/> |There is a decimal overflow error in the Planner. |
|PlannerSolutionMismatchedJobList = 28922  <br/> |The solution has a mismatched job list. |
|PlannerInvalidForceLookupTableValue = 28923  <br/> |The forced value of a lookup table is not valid. |
|PlannerNoHiredResource = 28924  <br/> |There is no resource hired for the proposal. |

<a name="pj15_ErrorCodes_Projects"></a>

## Table 18. Project

|Project error code|Description|
|:-----|:-----|
|ProjectGlobalNotFound = 100  <br/> |Cannot find the enterprise global template. |
|ProjectGlobalCannotBeDeleted = 101  <br/> |Cannot delete the enterprise global template. |
|ProjectNotFound = 1000  <br/> |Project not found. |
|ProjectAlreadyExists = 1001  <br/> |Project already exists. |
|ProjectCheckedoutToOtherUser = 1002  <br/> |The project is checked out to another user. |
|ProjectTypeInvalidForCreate = 1003  <br/> |The project type for the create operation is not valid. |
|ProjectParametersInvalid = 1004  <br/> |One or more project parameters are not valid. |
|ProjectNotCheckedoutToUser = 1006  <br/> |Project not checked out to user. |
|ProjectCheckedout = 1007  <br/> |Project checked out. |
|ProjectTypeInvalid = 1008  <br/> |The project type is not valid. |
|ProjectIDInvalid = 1009  <br/> |The project identification number is not valid. |
|ProjectNameTooLong = 1014  <br/> |Project name is too long. |
|ProjectManagerNameTooLong = 1015  <br/> |Project manager name is too long. |
|ProjectNameInvalid = 1016  <br/> |Project name is not valid. |
|ProjectStartDateMissing = 1025  <br/> |Project start date is missing. |
|ProjectNameMissing = 1026  <br/> |Project name is missing. |
|ProjectVersionMissing = 1027  <br/> |Project version is missing. |
|ProjectDoesNotExist = 1028  <br/> |Project does not exist. |
|ProjectMultipleProjectsInvalid = 1029  <br/> |Multiple projects are not valid. |
|ProjectHasWriteLock = 1030  <br/> |Project has a write lock in the database. |
|ProjectHasPendingWriteLock = 1031  <br/> |Project has a pending write lock. |
|ProjectHasNoReadLock = 1032  <br/> |Project does not have a read lock. |
|ProjectHasReadLock = 1033  <br/> |Project has a read lock. |
|ProjectNameAlreadyExists = 1034  <br/> |Project name already exists. |
|ProjectOptCriticalSlackLimitInvalid = 1035  <br/> |The optional critical slack limit is not valid. |
|ProjectOptCurrencyPositionInvalid = 1036  <br/> |The optional currency position is not valid. |
|ProjectOptCurrencyDigitsInvalid = 1037  <br/> |The optional currency digits are not valid. |
|ProjectOptCurrencySymbolTooLong = 1038  <br/> |The optional currency symbol is too long. |
|ProjectCannotDelete = 1039  <br/> |Cannot delete the project. Only regular or template server-side projects can be deleted. |
|ProjectCannotAdd = 1040  <br/> |Cannot use the **AddToProject** method on the server-side project. |
|ProjectOptCurrencySymbolInvalid = 1041  <br/> |The optional currency symbol is not valid. |
|ProjectHasNoWriteLock = 1042  <br/> |The project does not have a write lock. |
|ProjectFilterInvalid = 1043  <br/> |The project filter is not valid. |
|ProjectTooLarge = 1044  <br/> |The project proposal is too large. |
|ProjectOptCurrencyCodeNot3Chars = 1045  <br/> |The optional currency code is not three characters. |
|ProjectOptCurrencyCodeInvalid = 1046  <br/> |The currency code is not valid in the project options. |
|ProjectActualsAreProtected = 1047  <br/> |The project actuals are protected. |
|ProjectTemplateNotFound = 1048  <br/> |Project template not found. |
|ProjectCurrencyCodeInvalid = 1049  <br/> |The currency code is not valid. |
|ProjectCannotEditCostResource = 1050  <br/> |Cannot edit cost resource. |
|ProjectIsNotPublished = 1051  <br/> |Project not published. |
|ProjectExceededLWPTaskLimit = 1052  <br/> |Exceeded the task limit for a project proposal (a lightweight project). |
|ProjectOptFinishDateInvalid = 1053  <br/> |The finish date in the project options is not valid. |
|ProjectExceededItemsLimit = 1054  <br/> |Exceeded the limit of items to process. The Project Server service application cannot use **ProjectDataSet** to add or update more than 1000 items total in all tables. To process more than 1000 items, use multiple calls, for example, to **QueueUpdateProject**. |
|ProjectColumnNotReadOnly = 1055  <br/> |The column is not read-only. |
|ProjectInvalidOwner = 1056  <br/> |The project owner is not valid. |
|ProjectCantEditPctWrkCompForNonWrkRscs = 1057  <br/> |Cannot edit **PctWorkComplete** for a task that has no real work assignments. |
|ProjectCannotEditMaterialResource = 1058  <br/> |Cannot edit the material resource. |
|ProjectCannotEditFieldWhenTaskHasNoWorkAssignment = 1059  <br/> |Cannot edit the field because the task has no work assignment. |
|ProjectSubProjectNotFound = 1070  <br/> |. No subprojects were found. |
|ProjectResourceNotFound = 1100  <br/> |Resource not found. |
|ProjectResourceAlreadyExists = 1101  <br/> |Resource already exists. |
|ProjectCannotReplaceResourceWithSelf = 1106  <br/> |Cannot replace resource with same object. |
|ProjectCannotChangeLockedTrackingMethod = 1107  <br/> |Cannot change because the tracking method is locked. |
|ProjectInvalidColumnForCompatibilityMode = 1108  <br/> |The column for the compatibility mode is not valid. |
|ProjectUpdateInvalidUpdateSequenceNumber = 1151  <br/> |The sequence number in the project update is not valid. |
|ProjectUpdateDuplicateUpdateSequenceNumber = 1152  <br/> |Duplicate sequence number in the project update. |
|ProjectUpdateNullUpdateSequenceNumber = 1153  <br/> |Null sequence number in the project update. |
|ProjectUpdateNullUpdateColumnNames = 1154  <br/> |Null column names in the project update. |
|ProjectUpdateInvalidProjectUID = 1155  <br/> |The project GUID is not valid in the project update. |
|ProjectUpdateInvalidColumnForUpdate = 1156  <br/> |The column is not valid for the project update. |
|ProjectUpdateCannotEditColumn = 1157  <br/> |Cannot edit the column in the project update. |
|ProjectUpdateNoChangesToValidateAndSchedule = 1158  <br/> |The project update contains no changes that can be validated and scheduled. |
|LinkNotFound = 1159  <br/> |The link is not found. |
|ProjectUpdateInvalidColumnValue = 1160  <br/> |The column value is not valid in the project update. |
|ProjectCannotDeleteItem = 1161  <br/> |Cannot delete the project item. |
|ProjectUpdateCannotComputeOptIndex = 1162  <br/> |Cannot compute the optimizing index in the project update. |
|ProjectCannotUpdateDueToVisibilityMode = 1163  <br/> |Cannot update because project is in visibility mode. |
|ProjectNodeConsistencyException = 9132  <br/> |Exception: The node is not consistent. |
|ProjectSchedulingEngineException = 9133  <br/> |Exception in the scheduling engine. |
|ProjectFormulaCalculationException = 9134  <br/> |Exception in formula calculation. |
|ProjectUpdateDatabaseException = 9135  <br/> |Exception in database update. |
|ProjectDeleteException = 9136  <br/> |Exception in deleting project. |
|ProjectOperationException = 9137  <br/> |Exception in project operation. |
|ProjectCannotComunicateWithPCS = 9138  <br/> |Failed to communicate with the PCS worker. |
|ProjectPCSSessionInvalid = 9139  <br/> |Project in an engine session failed to open. |
|ProjectPublishFailure = 23000  <br/> |Failure in the queue while publishing project. |
|ProjectCurrencyConflict = 23001  <br/> |There is a conflict in the specified currency. |
|ProjectPublishFailed = 23002  <br/> |Publishing project failed when being enqueued. |
|ProjectReversePublishFailed = 23003  <br/> |The project publish operation failed when it was being enqueued. |
|ProjectReversePublishFailure = 23004  <br/> |Reverse publish of project failed during queue processing. |
|ProjectArchiveRetentionDeleteFailure = 23005  <br/> |Failure deleting project due to archive retention. |
|ProjectDeleteFailure = 23006  <br/> |Failure deleting project. |
|ProjectPublishEnqueueFailure = 23007  <br/> |Failure of project publishing when being enqueued. |
|ProjectCheckinFailure = 23008  <br/> |Check in of project failed during queue processing. |
|ProjectCheckinFailed = 23009  <br/> |Check in of project failed when being enqueued. |
|ProjectCheckoutFailed = 23010  <br/> |The user does not have project checkout permission. |
|ProjectPublishSummaryEnqueueFailure = 23011  <br/> |Publish summary failure when being enqueued. |
|ProjectPublishSummaryFailed = 23012  <br/> |Publish summary failure. |
|ProjectUpdateScheduledProjectFailure = 26026  <br/> |Failure of project scheduling update during queue processing. |
|ProjectSyncProjectEnterpriseEntitiesFailure = 26033  <br/> |Failure to synchronize project enterprise entities during queue processing. |
|GeneralDalDatabaseIsReadOnly = 26034  <br/> |Project drilldown load failed. Database is read-only. |
|GeneralDatabaseCommunicationError = 26035  <br/> |There can be many different causes, such as network or authentication problems. |

<a name="pj15_ErrorCodes_RDS"></a>

## Table 19. Reporting Data Service (RDS)

|RDS error code|Description|
|:-----|:-----|
|ReportingAttributeCubeSettingsChangedMessageFailed = 24000  <br/> |The RDS change message failed for a cube settings attribute. |
|ReportingBaseCalendarChangeMessageFailed = 24001  <br/> |The RDS change message failed for a base calendar. |
|ReportingCustomFieldMetadataChangeMessageFailed = 24002  <br/> |The RDS change message failed for custom field metadata. |
|ReportingEntityUserViewChangedMessageFailed = 24003  <br/> |The RDS change message failed for an entity user view. |
|ReportingFiscalPeriodChangeMessageFailed = 24004  <br/> |The RDS change message failed for a fiscal period. |
|ReportingLookupTableChangeMessageFailed = 24005  <br/> |The RDS change message failed for a lookup table. |
|ReportingProjectChangeMessageFailed = 24006  <br/> |The RDS change message failed for a project. |
|ReportingResourceCapacityUpdateMessageFailed = 24007  <br/> |The RDS update message failed for resource capacity. |
|ReportingResourceChangeMessageFailed = 24008  <br/> |The RDS change message failed for a resource. |
|ReportingTimesheetAdjustMessageFailed = 24009  <br/> |The RDS adjust message failed for a timesheet. |
|ReportingTimesheetClassCreateMessageFailed = 24010  <br/> |The RDS create message failed for a timesheet class. |
|ReportingTimesheetDeleteMessageFailed = 24011  <br/> |The RDS delete message failed for a timesheet. |
|ReportingTimesheetPeriodDeleteMessageFailed = 24012  <br/> |The RDS delete message failed for a timesheet period. |
|ReportingTimesheetPeriodMessageFailed = 24013  <br/> |The RDS message failed for a timesheet period. |
|ReportingTimesheetSaveMessageFailed = 24014  <br/> |The RDS save message failed for a timesheet. |
|ReportingTimesheetStatusChangeMessageFailed = 24015  <br/> |The RDS change message failed for timesheet status. |
|ReportingWSSSyncMessageFailed = 24016  <br/> |The RDS message failed for SharePoint synchronization. |
|ReportingGetSPWebFailed = 24017  <br/> |The RDS failed to get the SharePoint web value. |
|ReportingWssSyncListFailed = 24018  <br/> |The RDS failed to synchronize with the SharePoint list. |
|ReportingWssTransferLinksFailed = 24019  <br/> |The RDS failed to transfer SharePoint links. |
|ReportingQueueMessageSubmitFailed = 24020  <br/> |The RDS failed to submit a message to the queue. |
|ReportingWssSyncHRefFailed = 24021  <br/> |The RDS failed to synchronize with the SharePoint HRef value. |
|ReportingSyncGlobalDataMessageFailed = 24022  <br/> |The RDS message to synchronize with the enterprise global data failed. |
|ReportingRDBRefreshMessageFailed = 24023  <br/> |The RDS message to refresh the RDB failed. |
|ReportingAttributeCubeDepartmentsChangedMessageFailed = 24024  <br/> |The RDS message failed to change the department attribute for the OLAP cube. |
|ReportingTimesheetProjectAggregationMessageFailed = 24025  <br/> |The RDS message failed to aggregate projects for timesheet tables in the RDB. |
|ReportingRdbBulkDataSyncMessageFailed = 24026  <br/> |The RDS message failed for bulk data synchronization in the RDB. |
|ReportingWorkflowMetadataSyncMessageFailed = 24027  <br/> |The RDS message failed to synchronize workflow metadata. |
|ReportingProjectWorkflowInformationSyncMessageFailed = 24028  <br/> |The RDS message failed to synchronize project workflow information. |
|ReportingEptSyncMessageFailed = 24029  <br/> |The RDS message failed to synchronize the enterprise project template. |
|ReportingSummaryProjectPublishMessageFailed = 24030  <br/> |The RDS message failed to publish the summary project. |
|ReportingSolutionCommitedDecisionChangedMessageFailed = 24031  <br/> |The RDS message failed to change the committed decision for the solution. |
|ReportingDelayedUpgradeFailed = 24032  <br/> |The RDB delayed upgrade failed. |

<a name="pj15_ErrorCodes_Resources"></a>

## Table 20. Resource

|Resource error code|Description|
|:-----|:-----|
|ResourceNotFound = 2000  <br/> |Resource not found. |
|ResourceAlreadyExists = 2001  <br/> |Resource already exists. |
|ResourceCheckedoutToOtherUser = 2002  <br/> |Resource checked out to another user. |
|ResourceUIDInvalid = 2011  <br/> |The resource GUID is not valid. |
|ResourceNameInvalid = 2016  <br/> |The resource name is not valid. |
|ResourceNameTooLong = 2017  <br/> |Resource name is too long. |
|ResourceInitialsTooLong = 2018  <br/> |Resource initials are too long. |
|ResourceCheckedout = 2025  <br/> |The resource is checked out. |
|ResourceNTAccountInvalid = 2026  <br/> |The resource Windows (NTLM) account is not valid. |
|ResourceNameAlreadyInUse = 2027  <br/> |Resource name is already used. Names must be unique. |
|ResourceNTAccountAlreadyInUse = 2028  <br/> |The resource NTLM account is already used. |
|ResourceAdGuidAlreadyInUse = 2029  <br/> |The resource GUID is already used. |
|ResourceHasActuals = 2031  <br/> |The resource has actuals. |
|ResourceNTAccountTooLong = 2035  <br/> |The NTLM account is too long. |
|ResourceEMailAddressTooLong = 2036  <br/> |The resource email address is too long. |
|ResourceCodeTooLong = 2037  <br/> |The resource code is too long. |
|ResourceGroupTooLong = 2038  <br/> |The resource group is too long. |
|ResourceWorkGroupInvalid = 2039  <br/> |The resource workgroup is not valid. |
|ResourceTypeInvalid = 2040  <br/> |The resource type is not valid. |
|ResourceNonWorkResourceWithEMailInvalid = 2044  <br/> |A non-working resource cannot have an email address. |
|rsResourceNameHasTrailingOrLeadingWhitespace = 2046  <br/> |The resource name has leading or trailing white space. |
|ResourceCannotDeleteCallingUserAccount = 2047  <br/> |The user cannot delete his own account. |
|ResourceInitialsInvalid = 2048  <br/> |The resource initials are not valid. |
|ResourceAccrueAtInvalid = 2049  <br/> |The value for accrual is not valid. |
|ResourceNonMaterialResourceCannotHaveMaterialLabel = 2050  <br/> |A non-material resource cannot have a material label. |
|ResourceMaterialResourceCannotHaveCertainFields = 2051  <br/> |A material resource cannot have certain fields. |
|ResourceAvailFromAvailToOverlap = 2052  <br/> |Overlap of available from and available to dates. |
|ResourceInvalidEmailLanguage = 2053  <br/> |The email language is not valid. |
|ResourceBookingTypeInvalid = 2055  <br/> |The booking type is not valid. |
|ResourceCannotReplaceMaterialResourceWithNonMaterialResource = 2056  <br/> |Cannot replace material resource with non-material resource. |
|ResourceCannotUpdateEnterpriseResource = 2057  <br/> |Cannot update enterprise resource. |
|rsResourceCannotAddLocalWithSameNameAsEnterprise = 2058  <br/> |Cannot add local resource with the same name as an enterprise resource. |
|ResourceCannotSetRateOnCostResource = 2059  <br/> |Cannot set a rate on a cost resource. |
|ResourceCannotSetRateOnMaterialResource = 2060  <br/> |Cannot set a rate on a material resource. |
|ResourceCannotSetCanLevelOnNonWorkResource = 2061  <br/> |Cannot set the level on a non-work resource. |
|ResourceCannotDeleteThisUser = 2062  <br/> |Cannot delete this user. |
|ResourceCannotDeactivateSelf = 2063  <br/> |A resource cannot deactivate herself. |
|ResourceAvailabilityDateRangesOverlap = 2064  <br/> |Resource availability date ranges overlap. |
|ResourceAvailabilityOutsideTheHireAndTerminationDateRange = 2065  <br/> |The resource availability date is outside the hire and termination date range. |
|ResourceFilterInvalid = 2066  <br/> |The filter for a resource is not valid. |
|ResourceSegmentWithThisEffectiveDateDoesNotExist = 2067  <br/> |Cannot delete a resource rate that has not been saved. |
|ResourceSegmentWithThisEffectiveDateAlready = 2068  <br/> |A segment with this effective date already exists. |
|ResourceUserHasItemCheckedOutToItStill = 2069  <br/> |The user has an item still checked out. |
|ResourceInvalidHireDate = 2070  <br/> |The hire date is not valid. |
|ResourceInvalidTerminationDate = 2071  <br/> |The termination date is not valid. |
|ResourceCannotChangeExistingResourceType = 2072  <br/> |Cannot change a resource type. |
|ResourceCannotSetTimesheetManagerOnSpecifiedResource = 2073  <br/> |Cannot set the timesheet manager on the specified resource. |
|ResourceInvalidTimesheetManager = 2074  <br/> |The timesheet manager is not valid. |
|ResourceInvalidAssignmentOwner = 2075  <br/> |The assignment owner is not valid. |
|ResourceCannotCreateCostResource = 2076  <br/> |Cannot create cost resource. |
|ResourceInvalidRbsValue = 2077  <br/> |The RBS value is not valid. |
|ResourceCannotSetAssignmentOwnerOnSpecifiedResource = 2078  <br/> |Cannot set assignment owner on the specified resource. |
|ResourceFieldsInvalidForBudget = 2079  <br/> |One or more fields for the budget are not valid. |
|ResourceHyperlinkInvalid = 2080  <br/> |The resource hyperlink is not valid. |
|ResourceAuthorizationValidOnlyOnWorkResources = 2081  <br/> |The authorization is valid only on work resources. |
|ResourceIsProjectOwner = 2082  <br/> |Cannot delete resource because resource is the project owner. |
|ResourceIsTimesheetManager = 2083  <br/> |Cannot delete resource because resource is the timesheet manager. |
|ResourceIsDefaultAssignmentOwner = 2084  <br/> |Cannot delete resource because resource is the default assignment owner. |
|ResourceIsAssignmentOwner = 2085  <br/> |Cannot delete resource because resource is the assignment owner. |
|ResourceIsUsedInResourcePlan = 2086  <br/> |Cannot delete resource because resource is used in the resource plan. |
|ResourceCannotDeleteEnterpriseResource = 2087  <br/> |Cannot delete enterprise resource, for unknown reason. |
|ResourceSetResourceAuthorizationFailed = 2088  <br/> |Failed to set resource authorization. |
|ResourceTooManyResourcesSpecifiedToDelete = 2089  <br/> |Cannot delete the number of resources specified. |
|ResourceTooManyResourcesReturned = 2090  <br/> |The method cannot handle that number of resources. |
|ResourceCannotDeleteWorkflowProxyUser = 2091  <br/> |The workflow proxy user cannot be deleted. |
|ResourceInvalidEmailWithExchangeSync = 2092  <br/> |The email is not valid for synchronization with Microsoft Exchange Server. |
|ResourceInvalidResourceTypeWithExchangeSync = 2093  <br/> |The resource type is not valid for synchronization with Exchange Server. |
|ResourceInvalidPrincipalNameWithExchangeSync = 2094  <br/> |The resource principal name is not valid for synchronization with Exchange Server. |
|ResourceInvalidAuthenticationTypeWithExchangeSync = 2095  <br/> |The resource authentication type is not valid for synchronization with Exchange Server. |
|ResourceExchangeSyncFlagAndPrincipalNameMismatch = 2096  <br/> |Mismatch between the Exchange Server synchronization flag and the principal name for the resource. |
|ResourceUnsupportedUserUpdateInSharePointSecurityMode = 2097  <br/> |User creation is unsupported in SharePoint Security Mode. |

<a name="pj15_ErrorCodes_ResourcePlans"></a>

## Table 21. Resource plan

|Resource plan error code|Description|
|:-----|:-----|
|ResourcePlanProjectPublishIncomplete = 30000  <br/> |Did not complete publishing the project for the resource plan. |
|ResourcePlanInvalidResourceType = 30001  <br/> |The resource type in the resource plan is not valid. |
|ResourcePlanInactiveResourcesDisallowed = 30002  <br/> |Inactive resources are not allowed in a resource plan. |
|ResourcePlanFilterInvalid = 30003  <br/> |The resource plan filter is not valid. |
|ResourcePlanSaveFailure = 30004  <br/> |Failed to save resource plan. |
|ResourcePlanCheckinFailure = 30005  <br/> |Failed to check in the resource plan. |
|ResourcePlanDeleteFailure = 30006  <br/> |Failed to delete the resource plan. |
|ResourcePlanInvalidUtilizationType = 30007  <br/> |The resource plan utilization type is not valid. |
|ResourcePlanInvalidTimescale = 30008  <br/> |The resource plan timescale is not valid. |
|ResourcePlanMismatchedJobList = 30009  <br/> |Mismatch in resource plan job list. |
|ResourcePlanAlreadyExists = 30010  <br/> |Resource plan already exists. |
|ResourcePlanInvalidProjectUID = 30011  <br/> |The project GUID for the resource plan is not valid. |
|ResourcePlanResourceAlreadyExists = 30012  <br/> |The resource already exists in the resource plan. |
   
The error codes in Table 22 are for **Rules** methods in the **PWA** web service. They are used internally. 

<a name="pj15_ErrorCodes_Rules"></a>

## Table 22. Rules

|Rules error code|Description|
|:-----|:-----|
|RulesNameTooLong = 21001  <br/> |The name of the approval rule is too long. Internal use only in Project Web App. |
|RulesDescriptionTooLong = 21002  <br/> |The rule description is too long. Internal use only in Project Web App. |
|RulesInvalidRuleType = 21003  <br/> |The rule type is not valid. Internal use only in Project Web App. |
|RulesInvalidConditionType = 21004  <br/> |The condition type for a rule is not valid. Internal use only in Project Web App. |
|RulesInvalidOperatorType = 21005  <br/> |The operator type for a rule is not valid. Internal use only in Project Web App. |
|RulesInvalidListItemType = 21007  <br/> |The list item type for a rule is not valid. Internal use only in Project Web App. |
|RulesNameInvalidCharacters = 21008  <br/> |There are one or more characters in the rule name that are not valid. Internal use only in Project Web App. |
|RulesDescriptionInvalidCharacters = 21009  <br/> |There are one or more characters in the rule description that are not valid. Internal use only in Project Web App. |
|RulesInvalidValueType = 21010  <br/> |The value type in the rule is not valid. Internal use only in Project Web App. |

<a name="pj15_ErrorCodes_Security"></a>

## Table 23. Security

|Security error code|Description|
|:-----|:-----|
|SecurityGroupCouldNotBeCreated = 19001  <br/> |Cannot create security group. |
|SecurityFieldAccessIDInvalid = 19003  <br/> |The security field access code identification number is not valid. |
|SecurityCannotUpdateFacForNonExistentCategory = 19004  <br/> |Security category does not exist; cannot update the field access code. |
|SecurityDuplicateCategoryUid = 19005  <br/> |Duplicate security category GUID. |
|SecurityDuplicateGroupUid = 19006  <br/> |Duplicate security group GUID. |
|SecurityDuplicateTemplateUid = 19007  <br/> |Duplicate security template GUID. |
|SecurityInvalidTemplateUidRef = 19008  <br/> |The security template GUID is not valid. |
|SecurityInvalidGlobalPermission = 19009  <br/> |The global security permission is not valid. |
|SecurityInvalidCategoryPermission = 19010  <br/> |The security category permission is not valid. |
|SecurityUpdatedGroupNotFound = 19013  <br/> |Updated security group not found. |
|SecurityUpdatedCategoryNotFound = 19014  <br/> |Updated security category not found. |
|SecurityUpdatedTemplateNotFound = 19015  <br/> |Updated security template not found. |
|SecurityGroupMemberNotFound = 19016  <br/> |Security group member not found. |
|SecurityUserNotFound = 19018  <br/> |Project Server user not found. |
|SecurityNoCategoryRelationForPermission = 19019  <br/> |Security category relation not found for the permission. |
|SecurityCannotDeleteDefaultGroup = 19020  <br/> |Cannot delete default security group. |
|SecurityCannotDeleteDefaultCategory = 19021  <br/> |Cannot delete default security category. |
|SecurityCategoryCouldNotBeCreated = 19022  <br/> |Cannot create security category. |
|SecurityNoCategoryForPermission = 19023  <br/> |Security category not found for the permission. |
|SecurityNoCategoryForObject = 19024  <br/> |Security category not found for the object. |
|SecurityNoCategoryForRule = 19025  <br/> |Security category not found for the rule. |
|SecurityNoGroupForPermission = 19026  <br/> |Security group not found for the permission. |
|SecurityCannotSetPermissionForFieldGroup = 19027  <br/> |Cannot set permission for the security group field. |
|SecurityInvalidFieldGroup = 19028  <br/> |The security group field is not valid. |
|SecurityCannotSetOrgPermission = 19029  <br/> |Cannot set the security organization permission. |
|SecurityInvalidOrgPermission = 19030  <br/> |The security organization permission is not valid. |
|SecurityInvalidSecurityRule = 19031  <br/> |The security rule is not valid. |
|SecurityTemplateNotFound = 19034  <br/> |Security template not found. |
|SecurityInvalidObjectType = 19035  <br/> |The security object type is not valid. |
|SecurityDuplicateUid = 19036  <br/> |The security object GUID is a duplicate. |
|SecurityObjectNotFound = 19037  <br/> |The security object is not found. |
|SecurityInvalidCategoryUidRef = 19080  <br/> |The security category GUID is not valid. |
|SecurityInvalidProjectUidRef = 19081  <br/> |The project GUID for the security object is not valid. |
|SecurityInvalidGroupUidRef = 19082  <br/> |The security group GUID is not valid. |
|SecurityInvalidUserUidRef = 19083  <br/> |The user GUID for the security object is not valid. |
|SecurityInvalidCategoryPermissionUidRef = 19084  <br/> |The permission GUID for the security category is not valid. |
|SecurityInvalidGlobalPermissionUidRef = 19085  <br/> |The security global permission GUID is not valid. |
|SecurityInvalidResourceUidRef = 19086  <br/> |The resource GUID for the security object is not valid. |
|SecurityDeleteNotSupportedBySetMethod = 19087  <br/> |The method cannot delete the security object. |
|SecurityInvalidProjectCategoryPermissionUidRef = 19088  <br/> |The project category permission GUID is not valid. |
|SecurityCannotModifyCoreProjectCategoryDataInUpdate = 19089  <br/> |The security update method cannot modify the core project category data. |
|SecurityProjectCategoryEntitiesDoNotAllowInPlaceChanges = 19090  <br/> |Security category entities cannot be changed in an update. |
|SecurityCategoryCannotAddRelationForDeletedCategory = 19091  <br/> |Cannot add a relation for a deleted security category. |
|SecurityCategoryCannotAddPermissionForDeletedCategory = 19092  <br/> |Cannot add a permission for a deleted security category. |
|SecurityCategoryCannotAddPermissionForDeletedRelation = 19093  <br/> |Cannot add a permission for a deleted security category relation. |
|SecurityCategoryCannotDeleteRelationForNewlyAddedCategory = 19094  <br/> |Cannot delete the relation for a newly added security category. |
|SecurityCategoryCannotDeletePermissionForNewlyAddedCategory = 19095  <br/> |Cannot delete the permission for a newly added security category. |
|SecurityCategoryCannotDeletePermissionForNewlyAddedRelation = 19096  <br/> |Cannot delete the permission for a newly added relation in a security category. |
|SecurityCategoryCannotHaveDuplicateUserOrGroupUidsForRelation = 19097  <br/> |Cannot have duplicate user or group UIDs for a security category relation. |
|SecurityCategoryPermissionMustHaveMatchingRelation = 19098  <br/> |A category permission must have a matching security category relation. |
|SecurityCategoryProjectAlreadyHasSecurityProjectCategory = 19099  <br/> |The list of selected categories already has a project security category. |

<a name="pj15_ErrorCodes_Events"></a>

## Table 24. Project Server event

|Project Server event error code|Description|
|:-----|:-----|
|ServerEventInvalidEventId = 19033  <br/> |The Project Server event identification number is not valid. |
|ServerEventServiceNotFound = 22003  <br/> |The Project Server Eventing service is not found. This error is not used in Project Server code, but it maps to a raw Unified Logging Service (ULS) event. |
|ServerEventRemoteCouldNotReachProxy = 22005  <br/> |The remote Project Web App could not reach the proxy Project Server event manager. This error is not used in Project Server code, but it maps to a raw ULS event. |
|ServerEventManagerCouldNotReachRemote = 22006  <br/> |The Project Server event manager could not reach the remote Project Web App. This error is not used in Project Server code, but it maps to a raw ULS event. |
|ServerEventHandlerNotSigned = 22007  <br/> |The Project Server event handler is not signed. |
|ServerEventHandlerMalformedAssemblyName = 22008  <br/> |The assembly name for the Project Server event handler is not valid. |
|ServerEventHandlerOrderInvalid = 22009  <br/> |The order for the Project Server event handler is not valid. |
|ServerEventHandlerDuplicateEntry = 22010  <br/> |Duplicate entry for the Project Server event handler. |
|ServerEventHandlerNotFound = 22011  <br/> |Project Server event handler not found. |
|ServerEventHandlerDuplicateName = 22012  <br/> |Duplicate name for the Project Server event handler. |
|ServerEventHandlerNullAssemblyNameAndEndpointUrl = 22013  <br/> |Validate that there is either an endpoint URL or an assembly name. |

<a name="pj15_ErrorCodes_Statusing"></a>

## Table 25. Statusing web service 

|Statusing web service error code|Description|
|:-----|:-----|
|StatusingInvalidEntity = 3102  <br/> |The entity for **Statusing** is not valid. |
|StatusingGetDataForTaskFailed = 3103  <br/> |Failed to get data for task status. |
|StatusingGetTaskOrAssnCntrFailed = 3104  <br/> |Failed to get task or Assignment Center for status. |
|StatusingInvalidPIDForProjCntr = 3105  <br/> |The **Statusing** property identification number for Project Center is not valid. |
|StatusingDeleteAssnFailed = 3106  <br/> |Failed to delete assignment in **Statusing** process. |
|StatusingAssnSaveFailed = 3107  <br/> |Failed to save assignment in **Statusing** process. |
|StatusingTaskSaveFailed = 3108  <br/> |Failed to save task in **Statusing** process. |
|StatusingInvalidPID = 3109  <br/> |The **Statusing** property identification number is not valid. |
|StatusingSetDataValueInvalid = 3111  <br/> |The **Statusing** data value is not valid. |
|StatusingSetDataFailed = 3112  <br/> |Failed to set **Statusing** data value. |
|StatusingInvalidDelegationStart = 3113  <br/> |The start time for an assignment in the **DelegateAssignments** method is not valid. |
|StatusingApprovalUpdateFailed = 3114  <br/> |Failed to update status approval. |
|StatusingInvalidApprovalType = 3115  <br/> |The status approval type is not valid. |
|StatusingInternalError = 3116  <br/> |Internal processing error in a **Statusing** method. |
|StatusingInvalidUpdateData = 3117  <br/> |The update data in a **Statusing** method is not valid. |
|StatusingProjectUpdateFailed = 3118  <br/> |**Statusing** update of project failed. |
|StatusingInvalidPreviewData = 3119  <br/> |The **Statusing** preview data is not valid. |
|StatusingInvalidTransaction = 3120  <br/> |The **Statusing** transaction is not valid. |
|StatusingTooManyResults = 3121  <br/> |Too many results. More than 5000 rows would be returned when reading timephased status data. |
|StatusingInvalidInterval = 3122  <br/> |The interval in a **Statusing** method is not valid. The interval must in minutes and must be greater than zero. |
|StatusingApplyUpdatesFailed = 3123  <br/> |Failed to apply **Statusing** updates when enqueuing the request. |
|StatusingApplyUpdatesFailure = 3124  <br/> |Failed to apply **Statusing** updates during queue processing. |
|StatusingInvalidWorkData = 3125  <br/> |The work data for **Statusing** is not valid. |
|StatusingMissingNameAttribute = 3126  <br/> |Missing name attribute for **Statusing**. |
|StatusingInvalidNameAttribute = 3127  <br/> |The name attribute for **Statusing** is not valid. |
|StatusingInvalidData = 3128  <br/> |The **Statusing** data is not valid. |
|StatusingInvalidChangelist = 3130  <br/> |The XML data is not valid in the _changexml_ parameter of the **UpdateStatus** method. |
|StatusingInsufficientAssignmentRights = 3131  <br/> |**SetAssignmentWorkData** cannot update an assignment because the user does not have permission. |
|StatusingInvalidChangeNumber = 3132  <br/> |The **Statusing** change number is not valid. |
|StatusingPidNotEditable = 3133  <br/> |The **Statusing** property identification number is not editable. |
|StatusingCannotSetTimephasedDataInManualTasks = 3134  <br/> |Cannot set timephased data in manual tasks for **Statusing**. |
|StatusingCannotChangeTaskMode = 3135  <br/> |Cannot change the task mode for **Statusing**. |
   
The error codes in Table 26 are for **StatusReports** methods in the **PWA** web service. They are used internally in Project Web App. 

<a name="pj15_ErrorCodes_StatusReports"></a>

## Table 26. StatusReports 

|Status report error code|Description|
|:-----|:-----|
|StatusReportsUnknownError = 12100  <br/> |Unknown error in **StatusReports**. |
|StatusReportsPeriodUnmatched = 12101  <br/> |Cannot match the status report period. |
|StatusReportsPeriodUnavailable = 12102  <br/> |The status report period is unavailable. |
|StatusReportsInvalidFormInput = 12103  <br/> |Data in the status report form is not valid. |

<a name="pj15_ErrorCodes_Tasks"></a>

## Table 27. Task 

|Task error code|Description|
|:-----|:-----|
|TaskIDInvalid = 7001  <br/> |The task GUID is not valid. |
|TaskNameTooLong = 7003  <br/> |Task name too long. |
|TaskTypeInvalid = 7005  <br/> |The task type is not valid. |
|TaskPriorityInvalid = 7006  <br/> |The task priority is not valid. |
|TaskConstraintTypeInvalid = 7007  <br/> |The task constraint type is not valid. |
|TaskNameInvalid = 7008  <br/> |The task name is not valid. |
|TaskConstraintTypeRequiresConstraint = 7010  <br/> |The task requires a constraint type. |
|TaskConstraintTypeCannotHaveConstraintDate = 7011  <br/> |Cannot have a constraint date for the type of constraint. |
|TaskSummaryTaskCannotBeMilestone = 7013  <br/> |The summary task cannot be a milestone. |
|TaskFixedCostAccrualInvalid = 7014  <br/> |The fixed cost accrual for a task is not valid. |
|TaskPercentCompleteInvalid = 7015  <br/> |The task percent complete value is not valid. |
|TaskWorkPercentCompleteInvalid = 7016  <br/> |The task work percent complete value is not valid. |
|TaskPhysicalPercentCompleteInvalid = 7017  <br/> |The task physical percent complete value is not valid. |
|TaskLinkTypeInvalid = 7018  <br/> |The task link type is not valid. |
|TaskAlreadyExists = 7019  <br/> |The task already exists. |
|TaskLinkAlreadyExists = 7020  <br/> |The task link already exists. |
|TaskNotFound = 7021  <br/> |Task not found. |
|TaskLinkNotFound = 7022  <br/> |Task link not found. |
|TaskLinkLagInvalid = 7023  <br/> |The lag time on a task link is not valid. |
|TaskUnableToInsert = 7025  <br/> |Cannot insert a task. |
|TaskAddPositionInvalid = 7026  <br/> |The add position for a task is not valid. |
|TaskOutlineLevelInvalid = 7027  <br/> |The task outline level is not valid. |
|TaskDurationFormatInvalid = 7028  <br/> |The task duration format is not valid. |
|TaskCannotAddWhereSpecified = 7029  <br/> |Cannot add task where specified. |
|TaskEarnedValueMethodInvalid = 7030  <br/> |The method for task earned value is not valid. |
|TaskCannotModifyProjectSummary = 7031  <br/> |Cannot modify project summary task. |
|TaskCannotDeleteProjectSummary = 7032  <br/> |Cannot delete project summary task. |
|TaskCannotSetActualCost = 7033  <br/> |Cannot set actual cost for task. |
|TaskLevelingDelayInvalid = 7034  <br/> |The leveling delay for a task is not valid. |
|TaskCannotEditSummary = 7035  <br/> |Cannot edit summary task. |
|TaskCannotCreateSubTasksUnderTasksWithAssignments = 7036  <br/> |Cannot create subtasks under a task that has assignments. |
|TaskCannotDeleteSubProject = 7037  <br/> |Cannot delete subproject for the task. |
|TaskCannotEditExternal = 7038  <br/> |Cannot edit external task. |
|TaskCannotDeleteExternal = 7039  <br/> |Cannot delete an external task. |
|TaskLinkCannotDeleteExternal = 7040  <br/> |Cannot delete a link to an external task. |
|TaskCannotModifyNullTask = 7041  <br/> |Cannot modify a null task. |
|TaskCannotModifyLeafTaskWithNoAssignment = 7042  <br/> |Cannot modify a leaf task that has no assignment. |
|TaskCannotModifyExternalTask = 7043  <br/> |Cannot modify an external task. |
|TaskStatusManagerInvalid = 7044  <br/> |The task status manager is not valid. |
|TaskLinkCyclicDependency = 7045  <br/> |The task link has a cyclic dependency. |
|TaskCannotCreateOrModifySubTasksUnderTasksWithAssignments = 7046  <br/> |Cannot create or modify subtasks under a summary task that has assignments. |
|TaskLinkCannotEditExternal = 7047  <br/> |Cannot edit the link to an external task. |

<a name="pj15_ErrorCodes_Timesheets"></a>

## Table 28. Timesheet 

|Timesheet error code|Description|
|:-----|:-----|
|TimesheetMaxHourPerDayExceeded = 3201  <br/> |Exceeded maximum hours per day for timesheet. |
|TimesheetHoursPerTSLimitExceeded = 3202  <br/> |Exceeded the limit for number of hours in a timesheet. |
|TimesheetUnverifiedTSLineNotAllowed = 3203  <br/> |An unverified timesheet line is not allowed in this case. |
|TimesheetIncorrectMode = 3204  <br/> |The timesheet mode is not valid. |
|TimesheetInvalidApprover = 3205  <br/> |The timesheet approver is not valid. |
|TimesheetFutureReportingNotAllowed = 3206  <br/> |Reporting of future items not allowed for timesheet. |
|TimesheetIncorrectPeriod = 3208  <br/> |The timesheet period is not valid. |
|TimesheetPeriodClosed = 3209  <br/> |Timesheet period closed. |
|TimesheetPendingLines = 3210  <br/> |Timesheet lines are pending. |
|TimesheetInvalidDateRange = 3211  <br/> |The timesheet date range is not valid. |
|TimesheetLineClassDisabled = 3212  <br/> |The timesheet line class is disabled. |
|TimesheetLineHasNonExistentItem = 3213  <br/> |The timesheet line includes an item that does not exist. |
|TimesheetLineInvalidStatus = 3214  <br/> |The status for the timesheet line is not valid. |

<a name="pj15_ErrorCodes_UserDelegation"></a>

## Table 29. User delegation 

|User delegation error code|Description|
|:-----|:-----|
|UserDelegationExpired = 43000  <br/> |The user delegation has expired. |
|UserDelegationCannotSelfDelegate = 43001  <br/> |A user cannot delegate to himself or herself. |
|UserDelegationInvalidDelegate = 43002  <br/> |The user delegate is not valid. |
|UserDelegationInvalidUser = 43003  <br/> |The user is not valid for delegation. |
|UserDelegationInvalidDates = 43004  <br/> |The user delegation dates are not valid. |
|UserDelegationCannotDoubleDelegate = 43005  <br/> |Cannot create two delegates. |
|UserDelegationDelegateCannotLogon = 43006  <br/> |The user delegate cannot log on to Project Server. |
|UserDelegationDelegateIsInactive = 43007  <br/> |The user delegate is inactive. |
|UserDelegationInvalidFilter = 43008  <br/> |The user delegate filter is not valid. |
|UserDelegationUserCannotLogon = 43010  <br/> |The user cannot log on to Project Server. |
|UserDelegationUserIsInactive = 43011  <br/> |The user delegate is inactive. |

<a name="pj15_ErrorCodes_Workflow"></a>

## Table 30. Workflow 

|Workflow error code|Description|
|:-----|:-----|
|WorkflowPhasesCannotCreatePhase = 35000  <br/> |Cannot create the workflow phase. |
|WorkflowPhasesCannotUpdatePhase = 35001  <br/> |Cannot update the workflow phase. |
|WorkflowPhasesCannotDeletePhase = 35002  <br/> |Cannot delete the workflow phase. |
|WorkflowPhaseNameIsRequired = 35003  <br/> |The workflow [PHASE_NAME](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.WorkflowPhaseRow.PHASE_NAME.aspx) is required. |
|WorkflowStagesCannotCreateStage = 35004  <br/> |Cannot create the workflow stage. |
|WorkflowStagesCannotUpdateStage = 35005  <br/> |Cannot update the workflow stage. |
|WorkflowStagesCannotDeleteStage = 35006  <br/> |Cannot delete the workflow stage. |
|WorkflowStagesProjectsInStage = 35007  <br/> |There are projects in the workflow stage. |
|WorkflowCannotAccessPDPLibrary = 35008  <br/> |Cannot access the project detail page library. |
|WorkflowInvalidPDPUid = 35009  <br/> |The project detail page GUID is not valid. |
|WorkflowInvalidCustomFieldUid = 35010  <br/> |The custom field GUID is not valid. |
|WorkflowCustomFieldNotWorkflowControlled = 35011  <br/> |The custom field is not controlled by a workflow. |
|WorkflowCustomFieldCannotBeRequiredAndReadOnly = 35012  <br/> |The workflow custom field cannot be both required and read-only. |
|WorkflowInvalidWorkflowPhaseUid = 35013  <br/> |The workflow [PHASE_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.WorkflowPhaseRow.PHASE_UID.aspx) is not valid. |
|WorkflowInsertWorkflowPhaseNotAllowed = 35014  <br/> |Cannot insert a workflow phase. |
|WorkflowInvalidWorkflowStageUid = 35015  <br/> |The workflow [STAGE_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.WorkflowStageRow.STAGE_UID.aspx) is not valid. |
|WorkflowPhaseHasStages = 35016  <br/> |The workflow phase has stages. |
|WorkflowStageNameIsRequired = 35020  <br/> |The workflow [STAGE_NAME](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.WorkflowStageRow.STAGE_NAME.aspx) is required. |
|WorkflowStageAtLeastOnePDPIsRequired = 35021  <br/> |At least one project detail page is required for the workflow stage. |
|WorkflowCannotStartWorkflow = 35100  <br/> |Cannot start the workflow. |
|WorkflowStatusCannotUpdateStatus = 35101  <br/> |Cannot update the workflow status. |
|WorkflowOnlyProjectsHaveWorkflow = 35102  <br/> |Only projects can have a workflow. |
|WorkflowNoWorkflowsDefined = 35103  <br/> |No workflows are defined. |
|WorkflowInvalidStageForProject = 35104  <br/> |The workflow stage for the project is not valid. |
|WorkflowNoWorkflowForProject = 35105  <br/> |The project does not have a workflow. |
|WorkflowCheckinRequiredAndProjectNotCheckedin = 35106  <br/> |The project must be checked in for the workflow to operate. |
|WorkflowWaitingForRequiredData = 35107  <br/> |The workflow is waiting for required data. |
|WorkflowFlagCustomFieldsCannotBeRequired = 35108  <br/> |A flag custom field cannot be required in a workflow. |
|WorkflowCannotChangeWorkflow = 35109  <br/> |Cannot change the workflow. |
|WorkflowWorkflowStatusPDPNotAllowed = 35110  <br/> |A project detail page for workflow status is not allowed. |
|WorkflowInvalidWorkflowStatusPDPUid = 35111  <br/> |The GUID for the workflow status project detail page is not valid. |
|WorkflowInvalidStageStatusValue = 35112  <br/> |The value of the workflow stage status is not valid. When you set the stage status within the workflow, only the values **InProgressRequestSent**, **InProgressRunning**, or **InProgressWaiting** in [Workflow.StageStatus](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Workflow.StageStatus.aspx) are allowed. |
|WorkflowCannotCheckinNotify = 35113  <br/> |Cannot notify the workflow that the project is checked in. |
|WorkflowCannotCommitNotify = 35114  <br/> |Cannot notify the workflow that the project is committed in the Planner or the Optimizer. |
|WorkflowExceptionStartingWorkflow = 35115  <br/> |There is an error when starting the workflow. |
|WorkflowStatusPDPMustBeSupplied = 35116  <br/> |A project detail page for the workflow status is required. |
|WorkflowWorkflowProxyAccountNotFound = 35117  <br/> |The workflow proxy account is not found. |
|WorkflowInvalidCurrentStage = 35118  <br/> |The current stage of the workflow is not valid. |
|WorkflowMultipleStagesInProgress = 35119  <br/> |There are multiple stages in progress in the workflow. |
|WorkflowActivityInvalidArgument = 35120  <br/> |The message that is received if a workflow activity received an invalid. |
|WorkflowMTWConfigurationError = 35121  <br/> |Microsoft Azure Workflow configuration error. |
|EnterpriseProjectTypeInvalidEnterpriseProjectTypeUid = 35200  <br/> |The **ENTERPRISE_PROJECT_TYPE_UID** is not valid. |
|EnterpriseProjectTypeCannotCreateEnterpriseProjectType = 35201  <br/> |Cannot create the enterprise project type. |
|EnterpriseProjectTypeCannotUpdateEnterpriseProjectType = 35202  <br/> |Cannot update the enterprise project type. |
|EnterpriseProjectTypeCannotDeleteEnterpriseProjectType = 35203  <br/> |Cannot delete the enterprise project type. |
|EnterpriseProjectTypeCannotCreateMultipleEnterpriseProjectTypes = 35204  <br/> |Cannot create multiple enterprise project types. |
|EnterpriseProjectTypeCannotUpdateMultipleEnterpriseProjectTypes = 35205  <br/> |Cannot update multiple enterprise project types. |
|EnterpriseProjectTypeInvalidCreatePDPUid = 35206  <br/> |An enterprise project template (EPT) requires an associated project detail page (PDP) to create a project using the EPT. If the EPT is for a workflow, this error occurs during EPT validation when the project detail page (PDP) is not the *Create* type. Other PDP types are *Normal* for editing a project and *Workflow Status* for showing details of a project related to workflow. |
|EnterpriseProjectTypeInvalidProjectPlanTemplateUid = 35207  <br/> |The [ENTERPRISE_PROJECT_PLAN_TEMPLATE_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.EnterpriseProjectTypeRow.ENTERPRISE_PROJECT_PLAN_TEMPLATE_UID.aspx) is not valid. |
|EnterpriseProjectTypeInvalidWorkspaceTemplateName = 35208  <br/> |The [ENTERPRISE_PROJECT_WORKSPACE_TEMPLATE_NAME](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.EnterpriseProjectTypeRow.ENTERPRISE_PROJECT_WORKSPACE_TEMPLATE_NAME.aspx) is not valid. |
|EnterpriseProjectTypeInvalidWorkflowAssociationUid = 35209  <br/> |The [WORKFLOW_ASSOCIATION_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.EnterpriseProjectTypeRow.WORKFLOW_ASSOCIATION_UID.aspx) is not valid. |
|EnterpriseProjectTypeCannotReadWssSettings = 35210  <br/> |Cannot read the SharePoint settings. |
|EnterpriseProjectTypeCannotReadWssLanguagesAndTemplates = 35211  <br/> |Cannot read the SharePoint languages and site templates. |
|EnterpriseProjectTypeInvalidDepartmentUid = 35212  <br/> |The [DEPARTMENT_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.EnterpriseProjectTypeDepartmentsRow.DEPARTMENT_UID.aspx) is not valid. |
|EnterpriseProjectTypeInvalidUri = 35213  <br/> |The [ENTERPRISE_PROJECT_TYPE_UID](https://msdn.microsoft.com/library/WebSvcWorkflow.WorkflowDataSet.EnterpriseProjectTypeDepartmentsRow.ENTERPRISE_PROJECT_TYPE_UID.aspx) is not valid. |
|EnterpriseProjectTypeUriRequiresHttp = 35214  <br/> |The enterprise project type URI requires the HTTP protocol. |
|EnterpriseProjectTypeCannotDeleteDefault = 35215  <br/> |Cannot delete the default enterprise project type. |
|EnterpriseProjectTypeCannotChangeDefault = 35216  <br/> |Cannot change the default enterprise project type. |
|EnterpriseProjectTypeHasProjectsCannotDelete = 35217  <br/> |Cannot delete an enterprise project type that has projects. |
|EnterpriseProjectTypeCreatePDPIsRequired = 35218  <br/> |An enterprise project template (EPT) for a workflow requires an associated *Create* type project detail page (PDP) to create a project using the EPT. This error occurs when the PDP is not included in the EPT definition. Other PDP types are *Normal* for editing a project and  Workflow Status* for showing details of a project related to workflow. |
|EnterpriseProjectTypeOnlyOneCreatePDPAllowed = 35219  <br/> |The EPT definition allows only one *Create* type project detail page. |
|EnterpriseProjectTypeHasWorkflowOnlyCreatePDPAllowed = 35220  <br/> |An enterprise project template (EPT) for a workflow requires an associated *Create* type project detail page (PDP) to create a project using the EPT. This error occurs when the PDP in the workflow EPT definition is of another type. Other PDP types are *Normal* for editing a project and *Workflow Status* for showing details of a project related to workflow. |
|EnterpriseProjectTypeInvalidData = 35221  <br/> |The **WorkflowDataSet** for the enterprise project type has data that is not valid. |
|EnterpriseProjectNoDefaultEnterpriseProjectTypeDefined = 35222  <br/> |No default enterprise project type is defined. |
|EnterpriseProjectTypeAtLeastOnePDPIsRequired = 35223  <br/> |At least one project details page is required for the enterprise project type. |
|EnterpriseProjectTypeWorkflowStatusPDPNotAllowed = 35224  <br/> |A project details page for the workflow status is not allowed for the enterprise project type. |
|EnterpriseProjectTypeCannotChangeWorkflowAssociation = 35225  <br/> |The project already has an enterprise project type (EPT); you cannot change the EPT for the project. |

<a name="pj15_ErrorCodes_WSS"></a>

## Table 31. WssInterop and ObjectLinkProvider (SharePoint integration)

|SharePoint integration error code|Description|
|:-----|:-----|
|WSSCreateSiteFailure = 16400  <br/> |Failed to create SharePoint site for project workspace. |
|WSSCannotCreateWebWithBlankName = 16401  <br/> |Cannot create SharePoint website with a blank name. |
|WSSWebAlreadyExists = 16402  <br/> |The SharePoint website already exists. |
|WSSInvalidProjectUID = 16403  <br/> |The project GUID is not valid for the SharePoint project workspace. |
|WSSProjectAlreadyHasSpWeb = 16404  <br/> |The project already has a SharePoint workspace site. |
|WSSWebDoesNotExist = 16405  <br/> |The SharePoint website does not exist. |
|WSSSpWebAlreadyLinkedToProject = 16406  <br/> |The SharePoint website is already linked to a project. |
|WSSWebHierarchyDoesNotExist = 16407  <br/> |The SharePoint web hierarchy does not exist. |
|WSSSPWebHasChildren = 16408  <br/> |The SharePoint web has child webs. |
|WSSURIInvalidFormat = 16409  <br/> |The format for a SharePoint web URI is not valid. |
|WSSSyncReportingDataFailed = 16410  <br/> |Failed to synchronize reporting data for SharePoint. |
|WSSWorkspaceUrlPathTooLong = 16411  <br/> |SharePoint project workspace URL path too long. |
|WSSWorkspaceNameContainsIllegalChars = 16412  <br/> |One or more characters in a SharePoint project site name are not valid. The following characters are not valid in a project name: / " : \< \> | , . ' ? \* #  <br/> |
|WSSInvalidWssServerUid = 16413  <br/> |The SharePoint server GUID is not valid. |
|WSSSyncUsersFailed = 16414  <br/> |Failed to synchronize Project Server users with SharePoint. |
|WSSWrongWebTemplateLCID = 16415  <br/> |The SharePoint web template locale identifier (language ID) is not valid. |
|WSSWrongWebTemplate = 16416  <br/> |The SharePoint web template is not valid. |
|WSSWebIsNotProjectWorkspace = 16417  <br/> |The SharePoint website is not a project workspace. |
|WSSWebCannotStartOrEndOnPeriod = 16418  <br/> |A SharePoint web name cannot start or end with a period. |
|WSSCannotDeleteSiteCollection = 16419  <br/> |Cannot delete the website collection. |
|WSSListUidInvalid = 16420  <br/> |The SharePoint list GUID is not valid. |
|WSSSyncDataSetListUidMismatch = 16421  <br/> |The SharePoint list GUID does not match the list GUID in the synchronizing **DataSet**. |
|WSSSyncDataSetMissingProjectSettingsRow = 16422  <br/> |The **DataSet** for synchronizing with SharePoint is missing the project settings row. |
|WSSSyncDataSetTaskMappingsNotAllowed = 16423  <br/> |Task mappings are not allowed in the **DataSet** for synchronizing with SharePoint. |
|WSSSyncDataSetWssListUidEmpty = 16424  <br/> |The SharePoint list GUID is empty in the **DataSet** for synchronizing with SharePoint. |
|WSSSyncDataNotFound = 16425  <br/> |There is data missing in the synchronization with SharePoint. |
|WSSSyncCriticalDataValidationError = 16426  <br/> |There is a critical data validation error in the synchronization with SharePoint. |
|WSSSyncSharePointListNotAccessibleError = 16427  <br/> |The SharePoint list is not accessible. |
|WSSSyncInvalidEntityUids = 16428  <br/> |The entity GUIDs are not valid for synchronizing with SharePoint. |
|WSSSyncInvalidSyncData = 16429  <br/> |SharePoint synchronization has data that is not valid. |
|WSSSyncSPSummaryTaskAssignedToResourceError = 16430  <br/> |The SharePoint synchronization has a summary task assigned to a resource. |
|WSSSyncInsufficientPermissionsToCreateWinUser = 16431  <br/> |Permissions are not sufficient to create a Windows user when synchronizing with SharePoint. |
|WSSSyncNoDefaultValueForCustomField = 16432  <br/> |A custom field does not have a default value in the SharePoint synchronization. |
|WSSOLPCreateLinkFailure = 18000  <br/> |Failed to create link for the SharePoint object link provider. |
|WSSOLPDeleteWebObjectLinkError = 18001  <br/> |Error deleting a web object link in the SharePoint object link provider. |
|WSSInvalidPermissionsToWssList = 18002  <br/> |Permissions are not valid for the SharePoint list. |
|WSSWebIsNotUnderDefaultCollection = 18003  <br/> |The SharePoint web is not in the default collection. |
|WSSWorkspaceUrlIsNotUnderPrimaryCollection = 18004  <br/> |The specified workspace url is not in the site collection associated with this instance of project server. This is required by the current permission mode. |
|WSSWorkspacesMustBeRestrictedToDefaultCollection = 18005  <br/> |Workspaces must be restriced to the default site collection in the current permission mode. |

<a name="pj15_ErrorCodes_ASMXExample"> </a>

## Error code example for ASMX

To get a list of errors if you get an exception when you call a PSI method, pass the **SoapException** object to the [Microsoft.Office.Project.Server.Library.PSClientError](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.PSClientError.aspx) class constructor. You can then use [GetAllErrors](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.PSClientError.GetAllErrors.aspx) to store the error information in a **PSErrorInfo** array and enumerate the errors, as in the following example. 
  
> [!NOTE]
> The **PSErrorInfo** object does not include all of the information you might need. For example, if you use **Resource.CheckOutResources** where one of the resources is already checked out, **PSErrorInfo** shows the reason for failure for each resource that cannot be checked out, but does not include the resource name or GUID. For a way to get more information in an ASMX-based application, see [CheckOutResources](https://msdn.microsoft.com/library/WebSvcResource.Resource.CheckOutResources.aspx). 
  
```cs
using System;
using System.Collections.Generic;
using System.Text;
using System.Web.Services.Protocols;
using System.Windows.Forms;
using PSLibrary = Microsoft.Office.Project.Server.Library;
. . .
try
{
    /* Call a PSI method. */
}
catch (SoapException ex)
{
    string errAttributeName;
    string errAttribute;
    string errMess = "".PadRight(30, '=') + "\r\n" + "Error: " + "\r\n";
    PSLibrary.PSClientError error = new PSLibrary.PSClientError(ex);
    PSLibrary.PSErrorInfo[] errors = error.GetAllErrors();
    PSLibrary.PSErrorInfo thisError;
    for (int i = 0; i < errors.Length; i++)
    {
        thisError = errors[i];
        errMess += "\n" + ex.Message.ToString() + "\r\n";
        errMess += "".PadRight(30, '=') + "\r\nPSCLientError Output:\r\n \r\n";
        errMess += thisError.ErrId.ToString() + "\n";
        for (int j = 0; j < thisError.ErrorAttributes.Length; j++)
        {
            errAttributeName = thisError.ErrorAttributeNames()[j];
            errAttribute = thisError.ErrorAttributes[j];
            errMess += "\r\n\t" + errAttributeName +
                       ": " + errAttribute;
        }
        errMess += "\r\n".PadRight(30, '=');
    }
    MessageBox.Show(errMess, "Error", MessageBoxButtons.OK,
        MessageBoxIcon.Error);
}
```

<a name="pj15_ErrorCodes_WCFExample"> </a>

## Error code example for WCF

To get a list of errors if you get a **System.ServiceModel.FaultException** when you call a PSI method in a WCF-based application, you can extract a **PSClientError** object from the **FaultException** object. You can then use [GetAllErrors](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.PSClientError.GetAllErrors.aspx) to store the error information in a **PSErrorInfo** array and enumerate the errors, as in the previous ASMX example. 
  
```cs
using System;
using System.Text;
using System.ServiceModel;
using System.Xml;
using PSLibrary = Microsoft.Office.Project.Server.Library;
. . .
try
{
    /* Call a PSI method. */
}
catch(FaultException fault)
{
    // Use the WCF FaultException, because the ASMX SoapException does not 
    // exist in a WCF-based application.
    WriteFaultOutput(fault);
}
// Get a PSClientError object from the WCF FaultException object, and
// then display the exception details and each error in the PSClientError stack.
private static void WriteFaultOutput(FaultException fault)
{
    string errAttributeName;
    string errAttribute;
    string errOut;
    string errMess = "".PadRight(30, '=') + "\r\n"
        + "Error details: " + "\r\n";
    PSLibrary.PSClientError error = GetPSClientError(fault, out errOut);
    errMess += errOut;
    PSLibrary.PSErrorInfo[] errors = error.GetAllErrors();
    PSLibrary.PSErrorInfo thisError;
    for (int i = 0; i < errors.Length; i++)
    {
        thisError = errors[i];
        errMess += "\r\n".PadRight(30, '=') + "\r\nPSClientError output:\r\n";
        errMess += thisError.ErrId.ToString() + "\n";
        for (int j = 0; j < thisError.ErrorAttributes.Length; j++)
        {
            errAttributeName = thisError.ErrorAttributeNames()[j];
            errAttribute = thisError.ErrorAttributes[j];
            errMess += "\r\n\t" + errAttributeName
                + ": " + errAttribute;
        }
    }
    Console.ForegroundColor = ConsoleColor.Red;
    Console.WriteLine(errMess);
    Console.ResetColor();
}
/// <summary>
/// Extract a PSClientError object from the ServiceModel.FaultException,
/// for use in output of the GetPSClientError stack of errors.
/// </summary>
/// <param name="e"></param>
/// <param name="errOut">Shows that FaultException has more information 
/// about the errors than PSClientError has. FaultException can also contain 
/// other types of errors, such as failure to connect to the server.</param>
/// <returns>PSClientError object, for enumerating errors.</returns>
public static PSLibrary.PSClientError GetPSClientError(FaultException e, 
                                                        out string errOut)
{
    const string PREFIX = "GetPSClientError() returns null: ";
    errOut = string.Empty;
    PSLibrary.PSClientError psClientError = null;
    if (e == null)
    {
        errOut = PREFIX + "Null parameter (FaultException e) passed in.";
        psClientError = null;
    }
    else
    {
        // Get a ServiceModel.MessageFault object.
        var messageFault = e.CreateMessageFault();
        if (messageFault.HasDetail)
        {
            using (var xmlReader = messageFault.GetReaderAtDetailContents())
            {
                var xml = new XmlDocument();
                xml.Load(xmlReader);
                var serverExecutionFault = xml["ServerExecutionFault"];
                if (serverExecutionFault != null)
                {
                    var exceptionDetails = serverExecutionFault["ExceptionDetails"];
                    if (exceptionDetails != null)
                    {
                        try
                        {
                            errOut = exceptionDetails.InnerXml + "\r\n";
                            psClientError = 
                                new PSLibrary.PSClientError(exceptionDetails.InnerXml);
                        }
                        catch (InvalidOperationException ex)
                        {
                            errOut = PREFIX + "Unable to convert fault exception info ";
                            errOut += "a valid Project Server error message. Message: \n\t";
                            errOut += ex.Message;
                            psClientError = null;
                        }
                    }
                    else
                    {
                        errOut = PREFIX + "The FaultException e is a ServerExecutionFault, "
                            + "but does not have ExceptionDetails.";
                    }
                }
                else
                {
                    errOut = PREFIX + "The FaultException e is not a ServerExecutionFault.";
                }
            }
        }
        else // No detail in the MessageFault.
        {
            errOut = PREFIX + "The FaultException e does not have any detail.";
        }
    }
    errOut += "\r\n" + e.ToString() + "\r\n";
    return psClientError;
}

```


In addition to the data in the **PSClientError** object, the **FaultException** object can include other types of errors, such as failure to connect to Project Server. The _errOut_ parameter of the **GetPSClientError** method in the previous example shows additional information. For example, the **CreateProject4Department** code sample in the [QueueCreateProject](https://msdn.microsoft.com/library/WebSvcProject.Project.QueueCreateProject.aspx) method includes comments that show how to create errors when setting properties in the **ProjectCustomFields** table. When the application is run, the _errOut_ parameter includes the **errinfo** element and other data (formatted here from the console output). 
  
```XML
==============================
Error details:
<errinfo xmlns="">
  <dataset name="ProjectDataSet">
    <table name="ProjectCustomFields">
      <row CUSTOM_FIELD_UID="976d3bd9-95ff-40a2-a938-960c410b0341">
        <error id="11704" name="CustomFieldInvalidTypeColumnFilledIn" 
               uid="aa8a2fab-9262-422f-b022-ca1cb12bc75f"></error>
        <error id="11713" name="CustomFieldRequiredValueNotProvided" 
               uid="dc2e2156-86e9-4aac-bede-d07dc44dfedc"></error>
      </row>
    </table>
  </dataset>
</errinfo>
System.ServiceModel.FaultException`1[SvcProject.ServerExecutionFault]: 
ProjectServerError(s) LastError=CustomFieldRequiredValueNotProvided Instructions: 
Pass this into PSClientError constructor to access all error information 
(Fault Detail is equal to SvcProject.ServerExecutionFault).
============================
PSClientError output:
CustomFieldInvalidTypeColumnFilledIn
============================
PSClientError output:
CustomFieldRequiredValueNotProvided
```

<a name="pj15_ErrorCodes_AR"> </a>

## See also

- [Project conceptual and how-to articles](project-conceptual-and-how-to-articles.md)
- [SQL Server Profiler](https://msdn.microsoft.com/library/3ad5f33d-559e-41a4-bde6-bb98792f7f1a.aspx)
- [Project Server 2010: What to Expect when you get the Unexpected](https://blogs.msdn.com/b/brismith/archive/2010/03/24/project-server-2010-what-to-expect-when-you-get-the-unexpected.aspx)
- [ULS Viewer](https://www.codeproject.com/Articles/458052/ULS-Log-Viewer)
    

