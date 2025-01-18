---
title: "Transport Provider Sample"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ec6eb6c0-bfe3-4989-9071-89a14c0e7bdd
description: "This sample uses files and directories to transmit and receive messages. It implements a simple preprocessor that appends a line of text to each outbound message."
 
 
---

# Transport Provider Sample

**Applies to**: Outlook 2013 | Outlook 2016
  
This sample uses files and directories to transmit and receive messages. It implements and registers a very simple preprocessor that appends a line of text to each outbound message. The sample illustrates how to split message content between Transport Neutral Encapsulation Format (TNEF) and text. It also supports all configuration options (property sheets, wizards, and programmatic configuration) and message options. It does not support the remote transport interfaces.
  
You can download this sample from [Outlook Messaging API (MAPI) Code Samples](https://github.com/microsoft/Outlook2010CodeSamples).
  
|Property |Value |
|:-----|:-----|
|Executable:  <br/> |mrxp32.dll  <br/> |
|Source code directory:  <br/> |SampleTransportProvider\MRXP  <br/> |
|Language:  <br/> |C++  <br/> |
|Platforms:  <br/> |Visual Studio 2008 to compile for Windows Vista, Windows Server 2008, Windows XP SP2, and Windows Server 2003 SP1  <br/> |

## Supported Features

This sample supports the following features:
  
- Basic features such as sending, receiving, and polling for new messages.

- Interactive and programmatic configuration.

- The **IMAPIStatus** interface, except for property setting. For more information, see the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface.

- Thread safety.

- Event logging to a text file. The file is automatically limited to a specified size. All transport sessions use the same file.

## Unsupported Features

This sample does not support asynchronous detection of incoming messages.
  
 **To install the Sample Transport Provider**
  
1. To download the Sample Transport Provider, see [Downloading the Outlook MAPI Samples](downloading-the-outlook-mapi-samples.md).

2. Locate the folder where you saved the Outlook MAPI samples. Right-click the **OutlookMAPISamples-\<version number\>** zip folder and click **Extract All**.

3. Click **Browse**, select the location where you want to save the sample, and click **Extract**.

4. Run Visual Studio 2008.

5. In Visual Studio 2008, click **File**, select **Open**, and then click **Project/Solution**.

6. Browse to the location where you saved the sample, click **mrxp32.vcproj**, and then click **Open**.

7. On the **Build** menu, click **Configuration Manager**.

8. In the **Configuration Manager** dialog box, go to the **mrxp32** row, and in the **Configuration** column select **Release**, and then click **Close**.

9. On the **Build** menu, click **Build Solution**.

10. In the **Save File As** dialog box, click **Save**.

11. In the folder where you saved the sample, right-click the installation batch file and click **Run as administrator**.

12. In the **User Account Control** dialog box, click **Continue**.

    > [!NOTE]
    > **install.bat** copies the .dll to the default Microsoft Office installation folder, C:\Program Files\Microsoft Office\Office12\. If you have installed Office products in a different location, right-click **install.bat** and click **Edit**. The file opens in Notepad. Replace the default installation path with the installation path used on your computer.
  
 **To set up the Transport Provider in Outlook**
  
1. On the **Tools** menu of Outlook, click **Account Settings**.

2. In the **Account Settings** dialog box, on the **Email** tab, click **New**.

3. Under **Choose Email Service** click **Other**, select **MRXP Sample Transport**, and then click **Next**.

4. In the **MRXP Transport Configuration** dialog box type a **User Display Name**.

5. Under **Path to Inbox (UNC Share)** enter a folder path. This can also be a path to a local folder.

    > [!IMPORTANT]
    > This path must exist.
  
6. Click **OK**.

7. In the **Add Email Account** dialog box click **OK**. Click **Finish** and then click **Close**.

8. To start using the MRXP account, exit and restart Outlook.

 **To use the Transport Provider Sample to send a message in Outlook**
  
1. On the **File** menu, click **New**, and then click **Mail Message**.

2. In the **To** box type the name of the recipient using the format **[MRXP:\<ADDRESS\>]**. The address is the UNC share or local folder path to the recipient's inbox.

    > [!NOTE]
    > If there are colons or backslashes in the address, you must insert a backslash before each colon or backslash. For example, to send mail to [MRXP:C:\Mail\myDir] you must type `[MRXP:C\:\\Mail\\myDir]`.
  
    > [!IMPORTANT]
    > The recipient address must exist.
  
3. Click **Account** and then click **MRXP Sample Transport**.

4. Type your message and click **Send**. The message is sent using the MRXP transport provider.

 **To use the Transport Provider Sample to receive a message in Outlook**
  
1. On the **File** menu, click **New**, and then click **Mail Message**.

2. Type your message.

3. Click the **Microsoft Office Button**, click **Save As**, and then click **Save As** to save the file to the inbox folder you specified during setup.

4. In the **Save As** dialog box, browse to the UNC share or local folder that you set as your inbox.

5. In the **Save as type** drop down, click **Outlook Message Format**.

6. Type a name for the file and click **Save**.

7. The file is saved to the shared folder. The MRXP transport provider delivers the message to your Inbox in Outlook.
