---
title: Specifying Threads Per Processor on IIS
TOCTitle: Specifying Threads Per Processor on IIS
ms:assetid: 12889d7b-5415-8077-2ca0-1c3a96fb89ec
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248898(v=office.15)
ms:contentKeyID: 48543344
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Specifying Threads Per Processor on IIS


**Applies to**: Access 2013 | Office 2013

When using RDS with Internet Information Services 4.0 or later, the number of threads created per processor can be controlled by manipulating the registry on the Web server. The number of threads per processor can affect performance in a high traffic situation, or in low traffic situations with large query sizes. The user should experiment for best results.

The method used to determine and change the default value for this setting depends upon the configuration of the IIS 4.0 server.

With MDAC 2.1.2.4202.3 (GA) or later installed on the IIS server, RDS uses the same Component Services (or Microsoft Transaction Services, if you are using Windows NT) thread pool as ASP scripts use. The default value for the number of threads per processor is 10. To change the default, you must add the following key to the server registry:

``` 
 
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\InetInfo\Parameters\MaxPoolThreads
```

where *MaxPoolThreads* is a REG\_DWORD. *MaxPoolThreads* does not appear in the Registry unless it is specifically added. Valid values range from 5 to a recommended maximum of 20. If the value specified by the registry key is greater than the value of the *PoolThreadLimit* key (located under the same path), then *PoolThreadLimit* value is used.

Alternatively, if MDAC 2.1 2.1.1.3711.11 (GA) or earlier is installed on the IIS server, the default value for the number of threads per processor is 6. To change the default, you must add the following key to the registry on the IIS server:

``` 
 
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCThreads
```

where *ADCThreads* is a REG\_DWORD. *ADCThreads* does not appear in the Registry unless it is specifically added. The range of valid values is 1 to 50. If the value specified by the registry key is greater than 50, then the maximum value is used (50).

