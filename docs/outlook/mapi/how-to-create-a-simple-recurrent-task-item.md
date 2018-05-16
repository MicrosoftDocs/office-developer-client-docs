---
title: "How to Create a Simple Recurrent Task Item"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e9ee8865-0983-439e-8405-7946c5ec8762
description: "Last modified: July 23, 2011"
 
 
---

# How to: Create a Simple Recurrent Task Item

  
  
**Applies to**: Outlook 
  
MAPI can be used to create to create task items. This topic describes how to create a simple recurrent task item.
  
For information about how to download, view, and run the code from the MFCMAPI application and CreateOutlookItemsAddin project referenced in this topic, see [How to: Install the Samples Used in This Section](how-to-install-the-samples-used-in-this-section.md).
  
### 

### To create a task item

1. Open a message store. For information on how to open a message store, see [Opening a Message Store](opening-a-message-store.md).
    
2. Open the Tasks folder in the message store. For more information, see **PR_IPM_TASK_ENTRYID** ( [PidTagIpmTaskEntryId](pidtagipmtaskentryid-canonical-property.md)).
    
3. Call the [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method on the Tasks folder to create the new task item. 
    
4. Set the **dispidTaskRecur** ( [PidLidTaskRecurrence](pidlidtaskrecurrence-canonical-property.md)) property and other task-related properties required to create a recurrent task.
    
5. Save the new task item.
    
The  `AddTask` function in the Tasks.cpp source file of the CreateOutlookItemsAddin project demonstrates these steps. The  `AddTask` function takes parameters from the **Add Task** dialog box that is displayed when you click **Add Task** on the **Addins** menu in the MFCMAPI sample application. The  `DisplayAddTaskDialog` function in Tasks.cpp displays the dialog box and passes values from the dialog box to the  `AddTask` function. The  `DisplayAddTaskDialog` function does not relate directly to creating a task item using MAPI, so it is not listed here. 
  
> [!IMPORTANT]
> The code in the MFCMAPI application does not ensure that the **Tasks** folder has been selected when you click the **Add Task** command on the **Addins** menu. Creating task items in a folder other than the **Tasks** folder can cause undefined behavior. Make sure that you have selected the **Tasks** folder before using the **Add Task** command in the MFCMAPI application. 
  
The  `AddTask` function is listed below. Note that the  _lpFolder_ parameter passed to the  `AddTask` function is a pointer to an [IMAPIFolder](imapifolderimapicontainer.md) interface that represents the folder where the new task is created. Given the  _lpFolder_ that represents an **IMAPIFolder** interface, the code calls the [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method. The **CreateMessage** method returns a success code and a pointer to a pointer to an **IMessage** interface. Most of the  `AddTask` function code handles the work of specifying properties in preparation for calling the [IMAPIProp::SetProps](imapiprop-setprops.md) method. If the call to the **SetProps** method succeeds, the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method is called to commit the changes to the store and create a new task item. 
  
The  `AddTask` function sets a number of named properties. For information about named properties and how they are created, see [Using MAPI to Create Outlook 2007 Items](http://msdn.microsoft.com/en-us/library/cc678348%28office.12%29.aspx). Because the named properties used for task items occupy multiple property sets, care must be taken when building parameters to pass to the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method. 
  
The  `AddTask` function uses the  `BuildWeeklyTaskRecurrencePattern` helper function to build a structure representing a task recurrence for setting the **dispidTaskRecur** property. For information on the task recurrence structure the  `BuildWeeklyTaskRecurrencePattern` function builds, see [PidLidTaskRecurrence Canonical Property](pidlidtaskrecurrence-canonical-property.md) and [PidLidRecurrencePattern Canonical Property](pidlidrecurrencepattern-canonical-property.md). Note that while a large variety of recurrence patterns are possible, the  `BuildWeeklyTaskRecurrencePattern` function only builds a weekly recurrence pattern. It is also hard coded for a number of assumptions, such as the calendar type (Gregorian), the first day of the week (Sunday), and the number of modified or deleted instances (none). A more general purpose recurrence pattern creation function would need to accept these sorts of variables as parameters. 
  
The following is the complete listing of the  `AddTask` function. 
  
```
HRESULT AddTask(LPMAPIFOLDER lpFolder,
            SYSTEMTIME* lpstStart, // PidLidCommonEnd, PidLidTaskDueDate, PidLidTaskRecurrence
            SYSTEMTIME* lpstEnd, // PidLidTaskRecurrence
            SYSTEMTIME* lpstFirstDOW, // PidLidTaskRecurrence
            DWORD dwPeriod, // PidLidTaskRecurrence
            DWORD dwOccurrenceCount, // PidLidTaskRecurrence
            DWORD dwPatternTypeSpecific, // PidLidTaskRecurrence
            LPWSTR szSubject, // PR_SUBJECT_W
            LPWSTR szBody) // PR_BODY_W
{
   if (!lpFolder) return MAPI_E_INVALID_PARAMETER;
   HRESULT hRes = S_OK;
   LPMESSAGE lpMessage = 0;
   // create a message and set its properties
   hRes = lpFolder->CreateMessage(0,
      0,
      &amp;lpMessage);
   if (SUCCEEDED(hRes))
   {
      MAPINAMEID  rgnmid[ulTaskProps];
      LPMAPINAMEID rgpnmid[ulTaskProps];
      LPSPropTagArray lpNamedPropTags = NULL;
      ULONG i = 0;
      for (i = 0 ; i < ulTaskProps ; i++)
      {
         if (i < ulFirstTaskProp)
            rgnmid[i].lpguid = (LPGUID)&amp;PSETID_Common;
         else
            rgnmid[i].lpguid = (LPGUID)&amp;PSETID_Task;
         rgnmid[i].ulKind = MNID_ID;
         rgnmid[i].Kind.lID = aulTaskProps[i];
         rgpnmid[i] = &amp;rgnmid[i];
      }
      hRes = lpFolder->GetIDsFromNames(
         ulTaskProps,
         (LPMAPINAMEID*) &amp;rgpnmid,
         NULL,
         &amp;lpNamedPropTags);
      if (SUCCEEDED(hRes) &amp;&amp; lpNamedPropTags)
      {
      // Because the properties to be set are known in advance, 
      // most of the structures involved can be statically declared 
      // to minimize expensive MAPIAllocateBuffer calls.
         SPropValue spvProps[NUM_PROPS] = {0};
         spvProps[p_PidLidTaskMode].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskMode],PT_LONG);
         spvProps[p_PidLidCommonEnd].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidCommonEnd],PT_SYSTIME);
         spvProps[p_PidLidTaskStatus].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskStatus],PT_LONG);
         spvProps[p_PidLidPercentComplete].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidPercentComplete],PT_DOUBLE);
         spvProps[p_PidLidTaskState].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskState],PT_LONG);
         spvProps[p_PidLidTaskRecurrence].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskRecurrence],PT_BINARY);
         spvProps[p_PidLidTaskDeadOccurrence].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskDeadOccurrence],PT_BOOLEAN);
         spvProps[p_PidLidTaskOwner].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskOwner],PT_UNICODE);
         spvProps[p_PidLidTaskFRecurring].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskFRecurring],PT_BOOLEAN);
         spvProps[p_PidLidTaskOwnership].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskOwnership],PT_LONG);
         spvProps[p_PidLidTaskAcceptanceState].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskAcceptanceState],PT_LONG);
         spvProps[p_PidLidTaskFFixOffline].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskFFixOffline],PT_BOOLEAN);
         spvProps[p_PidLidTaskDueDate].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskDueDate],PT_SYSTIME);
         spvProps[p_PidLidTaskComplete].ulPropTag
            = CHANGE_PROP_TYPE(lpNamedPropTags->aulPropTag[p_PidLidTaskComplete],PT_SYSTIME);
         spvProps[p_PR_MESSAGE_CLASS_W].ulPropTag   = PR_MESSAGE_CLASS_W;
         spvProps[p_PR_ICON_INDEX].ulPropTag        = PR_ICON_INDEX;
         spvProps[p_PR_SUBJECT_W].ulPropTag         = PR_SUBJECT_W;
         spvProps[p_PR_MESSAGE_FLAGS].ulPropTag     = PR_MESSAGE_FLAGS;
         spvProps[p_PR_BODY_W].ulPropTag            = PR_BODY_W;
         spvProps[p_PidLidTaskMode].Value.l = tdmtNothing;
         SYSTEMTIME stStartUTC = {0};
         TzSpecificLocalTimeToSystemTime(NULL,lpstStart,&amp;stStartUTC);
         SystemTimeToFileTime(&amp;stStartUTC,&amp;spvProps[p_PidLidCommonEnd].Value.ft);
         spvProps[p_PidLidTaskStatus].Value.l = tsvNotStarted;
         spvProps[p_PidLidPercentComplete].Value.dbl = 0.0;
         spvProps[p_PidLidTaskState].Value.l = tdsOWNNEW;
         spvProps[p_PidLidTaskDeadOccurrence].Value.b = false;
         spvProps[p_PidLidTaskOwner].Value.lpszW = L"Unknown";
         spvProps[p_PidLidTaskFRecurring].Value.b = true;
         spvProps[p_PidLidTaskOwnership].Value.l = tovNew;
         spvProps[p_PidLidTaskAcceptanceState].Value.l = tdvNone;
         spvProps[p_PidLidTaskFFixOffline].Value.b = true;
         SystemTimeToFileTime(lpstStart,&amp;spvProps[p_PidLidTaskDueDate].Value.ft);
         spvProps[p_PidLidTaskComplete].Value.b = false;
         spvProps[p_PR_MESSAGE_CLASS_W].Value.lpszW = L"IPM.Task";
         spvProps[p_PR_ICON_INDEX].Value.l = 0x501; // Unassigned Recurring Task
         spvProps[p_PR_SUBJECT_W].Value.lpszW = szSubject;
         spvProps[p_PR_MESSAGE_FLAGS].Value.l = MSGFLAG_READ;
         spvProps[p_PR_BODY_W].Value.lpszW = szBody;
         hRes = BuildWeeklyTaskRecurrencePattern(
            lpstStart,
            lpstEnd,
            lpstFirstDOW,
            dwPeriod,
            dwOccurrenceCount,
            dwPatternTypeSpecific,
            &amp;spvProps[p_PidLidTaskRecurrence].Value.bin.cb,
            &amp;spvProps[p_PidLidTaskRecurrence].Value.bin.lpb);
         if (SUCCEEDED(hRes))
         {
            hRes = lpMessage->SetProps(NUM_PROPS, spvProps, NULL);
            if (SUCCEEDED(hRes))
            {
               hRes = lpMessage->SaveChanges(FORCE_SAVE);
            }
         }
         if (spvProps[p_PidLidTaskRecurrence].Value.bin.lpb)
            delete[] spvProps[p_PidLidTaskRecurrence].Value.bin.lpb;
      }
      MAPIFreeBuffer(lpNamedPropTags);
   }
   if (lpMessage) lpMessage->Release();
   return hRes;
}

```

## See also

#### Other resources

[Using MAPI to Create Outlook 2007 Items](http://msdn.microsoft.com/en-us/library/cc678348%28office.12%29.aspx)

