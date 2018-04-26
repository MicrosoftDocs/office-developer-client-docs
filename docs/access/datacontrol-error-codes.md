---
title: "DataControl Error Codes"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d81446e2-aae6-b460-08a3-eae9920dc767
description: "The following table lists the RDS.DataControl object error codes. The positive decimal translation of the low two bytes, the negative decimal translation of the full error code, and the hexadecimal values are shown."
---

# DataControl Error Codes

The following table lists the [RDS.DataControl](datacontrol-object-rds.md) object error codes. The positive decimal translation of the low two bytes, the negative decimal translation of the full error code, and the hexadecimal values are shown. 
  
|**RDS.DataControl error codes**|**Number**|**Description**|
|:-----|:-----|:-----|
|**IDS_AsyncPending** <br/> |4107          -2146824175          0x800A1011  <br/> |Operation cannot be performed while async operation is pending.  <br/> |
|**IDS_BadInlineTablegram** <br/> |4105          -2146824183          0x800A1009  <br/> |Bad inline tablegram.  <br/> |
|**IDS_CantConnect** <br/> |4099          -2146824189          0x800A1003  <br/> |Cannot connect to server.  <br/> |
|**IDS_CantCreateObject** <br/> |4100          -2146824188          0x800A1004  <br/> |Business object cannot be created.  <br/> |
|**IDS_CantFindDataspace** <br/> |4102          -2146824186          0x800A1006  <br/> |Dataspace property is not valid.  <br/> |
|**IDS_CantInvokeMethod** <br/> |4101          -2146824187          0x800A1005  <br/> |Method cannot be invoked on business object.  <br/> |
|**IDS_CrossDomainWarning** <br/> |4112          -2146824170          0x800A1016  <br/> |This page accesses data on another domain. Do you want to allow this? To avoid this message in Internet Explorer, you can add a secure Web site to your Trusted Sites zone on the **Security** tab of the **Internet Options** dialog box.  <br/> |
|**IDS_InvalidADCClientVersion** <br/> |4106          -2146824176          0x800A1010  <br/> |Invalid RDS Client Version — Client is newer than server.  <br/> |
|**IDS_INVALIDARG** <br/> |5376          -2147019520          0x80071500  <br/> |One or more arguments are invalid.  <br/> |
|**IDS_InvalidBindings** <br/> |4097          -2146824191          0x800A1001  <br/> |Error in bindings property.  <br/> |
|**IDS_InvalidParam** <br/> |4110          -2146824172          0x800A1014  <br/> |One or more arguments are invalid.  <br/> |
|**IDS_NOINTERFACE** <br/> |5377          -2147019519          0x80071501  <br/> |No such interface is supported.  <br/> |
|**IDS_NotReentrant** <br/> |4111          -2146824171          0x800A1015  <br/> |Request cannot be executed while the event handler is still processing.  <br/> |
|**IDS_ObjectNotSafe** <br/> |4103          -2146824185          0x800A1007  <br/> |Safety settings on this computer prohibit creation of business object.  <br/> |
|**IDS_RecordsetNotOpen** <br/> |4109          -2146824173          0x800A1013  <br/> |**Recordset** is not open.  <br/> |
|**IDS_ResetInvalidField** <br/> |4108          -2146824174          0x800A1012  <br/> |Column specified in **SortColumn** or **FilterColumn** does not exist.  <br/> |
|**IDS_RowsetNotUpdateable** <br/> |4104          -2146824184          0x800A1008  <br/> |Rowset not updateable.  <br/> |
|**IDS_UnexpectedError** <br/> |4351          -2146823937          0x800A10FF  <br/> |Unexpected error.  <br/> |
|**IDS_UpdatesFailed** <br/> |4098          -2146824190          0x800A1002  <br/> |Unable to update database.  <br/> |
|**IDS_URLMONNotFound** <br/> |4119          -2146824169          0x800A1017  <br/> |DataControl **URL** property requires the system file Urlmon.dll, which cannot be found.  <br/> |
   

