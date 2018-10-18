---
title: Configuring RDS on Windows 2000
TOCTitle: Configuring RDS on Windows 2000
ms:assetid: eb2d4c1d-8b3b-07ac-258f-edb0b1a3daba
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250193(v=office.15)
ms:contentKeyID: 48548482
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Configuring RDS on Windows 2000


**Applies to**: Access 2013 | Office 2013

If you experience difficulties getting RDS to function properly after upgrading to Windows 2000, follow the steps below to troubleshoot the issue.

1.  Make sure that the World Wide Web Publishing Service is running first by navigating to https://*server* using Internet Explorer. If you are unable to access the web server this way, go to a command prompt and enter the following command, "NET START W3SVC".

2.  From the Start menu, select Run. Type msdfmap.ini and click OK to open the msdfmap.ini file in Notepad. Check the \[CONNECT DEFAULT\] section, and if the ACCESS parameter is set to NOACCESS, change it to READONLY.

3.  Using the RegEdit utility, navigate to "HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DataFactory\\HandlerInfo" and make sure **HandlerRequired** is set to 0 and **DefaultHandler** is "" (Null string).
    

    > [!NOTE]
    > <P>If you make any changes to this section of the registry, you must stop and restart the World Wide Web Publishing Service by entering the following commands at a command prompt: "NET STOP W3SVC" and "NET START W3SVC".</P>



4.  Using the RegEdit utility, navigate in the registry to "HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\W3SVC\\Parameters\\ADCLaunch" and verify that there is a key called **RDSServer.Datafactory**. If not, create it.

5.  Using Internet Services Manager, go to the Default Web Site and view the properties of the MSADC virtual root. Inspect the Directory Security/IP Address and Domain Name Restrictions. If the "Access is Denied" is checked then select "Granted".

Be sure to try rebooting the server if the changes to do not appear to solve the problem at first.

