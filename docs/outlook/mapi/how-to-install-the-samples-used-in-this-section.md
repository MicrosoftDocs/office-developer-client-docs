---
title: "Install the samples used in this section"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 810f54bf-5b78-46b8-a617-4f61ff816400
---

# Install the samples used in this section

**Applies to**: Outlook 2013 | Outlook 2016 
  
To install the MFCMAPI application and CreateOutlookItemsAddin project to view and run the sample code referenced by the topics in the [Creating Outlook Items by Using MAPI](creating-outlook-items-by-using-mapi.md) section, follow these steps. 

To download and install the examples used in the "Using MAPI to create Outlook items" section, follow these steps.

### To download and install the MFCMAPI application and open CreateOutlookItemsAddin project

1. Download the current version of the [MFCMAPI](https://aka.ms/mfcmapi) executable to a folder on your system. 
    
2. Extract the MFCMapi.exe file in MFCMapi.exe. _version_.zip to an empty folder on your hard drive.
    
3. Download the current version of the [CreateOutlookItemsAddin](https://go.microsoft.com/fwlink/?LinkID=127828) project. 
    
4. Extract all the files in the CreateOutlookItemsAddin.zip file to the folder where you extracted the MFCMapi.exe file in Step 2.
    
5. Copy MFCMapi.exe from the folder used in Step 2 to the build directory for the CreateOutlookItemsAddin project (\CreateOutlookItemsAddin\Debug).
    
6. Open the CreateOutlookItemsAddin project (\CreateOutlookItemsAddin\CreateOutlookItemsAddin.vcproj) in Visual Studio to examine the source code. Refer to the topics from the [Creating Outlook Items by Using MAPI](creating-outlook-items-by-using-mapi.md) section to determine which source files to open. 
    
## Run MFCMAPI and the CreateOutlookItemsAddin project

The following steps assume that you have downloaded and installed the current version of the MFCMAPI executable and the CreateOutlookItemsAddin project as described in the preceding procedure. These steps will guide you to the **Addins** menu items that enable you to create Outlook items using the MFCMAPI application and the CreateOutlookItemsAddin project. 
  
> [!NOTE]
> The folder you select in step 8, and the command you select in step 9, depends on the item type discussed in one of the topics from the [Creating Outlook Items by Using MAPI](creating-outlook-items-by-using-mapi.md) section. 

### To run the MFCMAPI application and Addins menu commands

1. Start Mfcmapi.exe in the CreateOutlookItemsAddin\Debug folder that is created when you follow the installation instructions.
    
2. Click **OK** to dismiss the MFCMAPI splash screen. 
    
3. On the **Session** menu, click **Logon and Display Store Table**.
    
4. In the **Choose Profile** dialog box, select the correct profile, and then click **OK**. 
    
5. Double-click **Mailbox -  _[User Name]_** in the store table list view. 
    
6. In the folder tree view, expand the root node. The name displayed for the root node varies depending on the type of profile selected. Typically this node is displayed as **Root - Mailbox**.
    
7. In the folder tree view, expand the node that contains the information store. The name displayed for this node varies depending on the type of profile selected. Typically this node is displayed as **IPM_SUBTREE** or **Top of Information Store**.
    
8. Double-click the folder for the item type to create. For example, to create an appointment, click the **Appointments** folder. 
    
9. On the **Addins** menu, click the appropriate command for the item to create. 
    
## Download and view code from the MFCMAPI application

Some topics refer to source code from the MFCMAPI application itself. The following steps describe how to download the MFCMAPI source code and view it in Visual Studio. 

### To download and view the MFCMAPI application source code

1. Download the source code for the current version of the [MFCMAPI](https://go.microsoft.com/fwlink/?LinkID=124154) application to a folder on your system. 
    
2. Extract the files in MFCMAPI- _changeset_.zip to an empty folder on your hard drive.
    
3. Open the MFCMapi project (\ _foldername_\ MFCMapi.vcproj) in Visual Studio to examine the source code.
    
## See also

- [Create a Simple Mail Item](how-to-create-a-simple-mail-item.md)
- [Create a Simple Recurrent Task Item](how-to-create-a-simple-recurrent-task-item.md)
- [Create a Complex Recurrent Appointment Item](how-to-create-a-complex-recurrent-appointment-item.md)
- [Read and Parse a Recurrence Pattern](how-to-read-and-parse-a-recurrence-pattern.md)

