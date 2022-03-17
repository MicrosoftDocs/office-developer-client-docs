---
title: "Declaring Form Interfaces"
manager: lindalu
ms.date: 03/16/2022
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 79283301-e544-4a4d-96c2-3f81dc5b3731
  
---

# Declaring Form Interfaces

**Applies to**: Outlook 2013 | Outlook 2016
  
You can simplify the declarations of your implementations of MAPI form interfaces by using the MAPI_interface_METHOD macros, where _interface_ is a form interface defined in the Mapiform.h header file. You are not required to use these macros, but if you do not, you should take particular care that your declarations conform to the declarations in the Mapiform.h header file. For example, you could declare your form server's form object class like the following:
  
```cppclass CMyForm : public IPersistMessage, public IMAPIForm,
                public IMAPIFormAdviseSink
{
public:
    CMyForm(CClassFactory *);    // constructor takes a class factory object
    ~CMyForm(void);
// MAPI methods that need to be implemented.
    MAPI_IUNKNOWN_METHODS(IMPL);
    MAPI_GETLASTERROR_METHOD(IMPL);
    MAPI_IPERSISTMESSAGE_METHODS(IMPL);
    MAPI_IMAPIFORM_METHODS(IMPL);
    MAPI_IMAPIFORMADVISESINK_METHODS(IMPL);
// Add other implementation specific items.
};

```

## See also

[Writing Form Server Code](writing-form-server-code.md)
