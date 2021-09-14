---
title: "Launching a Form Server"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a439e75a-92b3-4830-9dfc-e723d046be7b
description: "Last modified: July 23, 2011"
 
 
---

# Launching a Form Server

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The series of interactions that occurs when a form is loaded from persistent storage (that is, from a form library) to display a message is as follows:
  
1. The messaging client gets the message's message class, message flags, and message status. This step is optional; if these pieces of data are not provided in step 2, the form manager will retrieve them.
    
2. The messaging client calls [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md) with the target message. 
    
3. The form manager loads the form server from the appropriate form library. If the form server for the target message is not installed, the form manager installs the form's executable files, as well.
    
4. The form manager calls [IUnknown::QueryInterface](https://msdn.microsoft.com/library/54d5ff80-18db-43f2-b636-f93ac053146d%28Office.15%29.aspx) on the form object to obtain the form object's [IMAPIForm : IUnknown](imapiformiunknown.md) and [IPersistMessage : IUnknown](ipersistmessageiunknown.md) interfaces. 
    
5. The form manager calls [IPersistMessage::Load](ipersistmessage-load.md) with the message site and message interfaces from the viewer object. 
    
6. The form object calls back to the messaging client's [IMAPIMessageSite::GetSiteStatus](imapimessagesite-getsitestatus.md) method. 
    
7. The form manager calls the form object's [IMAPIForm::SetViewContext](imapiform-setviewcontext.md) method with the view context interface from the messaging client. 
    
8. The form object calls back to the messaging client's [IMAPIViewContext::SetAdviseSink](imapiviewcontext-setadvisesink.md) method. 
    
9. The form object calls back to the messaging client's [IMAPIViewContext::GetViewStatus](imapiviewcontext-getviewstatus.md) method. 
    
10. The messaging client calls the form object's [IMAPIForm::Advise](imapiform-advise.md) method with the view context interfaces from the viewer object and the message site object. 
    
11. The messaging client calls the form object's [IMAPIForm::DoVerb](imapiform-doverb.md) method. 
    
12. The form object creates its user interface, if necessary, and interacts with the user.
    
## See also



[Form Server Interactions](form-server-interactions.md)

