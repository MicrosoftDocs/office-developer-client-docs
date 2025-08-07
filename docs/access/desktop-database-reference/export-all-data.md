---
title: Export all data from a Microsoft Access Database
TOCTitle: Export all data
ms:assetid: 79a1f793-7154-1c13-7dfe-a1b8cd64e1ea
ms.date: 08/06/2024
ms.localizationpriority: medium
---

# Export all data from a Microsoft Access database

**Applies to**: Access 2024, Access 2021 

This topic explains how an IT administrator can export all data and objects from a Microsoft Access database to text files, enabling use with other tools and supporting data portability.

For data stored in Tables, data can be exported to a variety of other formats using Access Wizards, such as Excel, see [Export data to Excel](https://support.microsoft.com/office/export-data-to-excel-64e974e6-ae43-4301-a53e-20463655b1a9), or text, see [Export data to a text file](https://support.microsoft.com/office/export-data-to-a-text-file-f72dfc38-a8a0-4c5b-8c2c-bf2950814140).

The following instructions demonstrate how to export objects using VBA code, using the [DoCmd.TransferText method](https://learn.microsoft.com/office/vba/api/Access.DoCmd.TransferText) command to export table data, and the [Application.SaveAsText](/application-save-as-text) command for other objects. 

The code provided will create a function that can be called with the full path to a database and a destination folder. It will then create a text file for each object in the database, which will contain the data from tables, and the definitions of all user created objects such as forms or reports.

Since this process uses OLE automation, the code could also be written using PowerShell or using a .NET language such as C#. For this example, we use VBA.

1.	Create a new database.
2.	Create a new module.
3.	Copy and paste the following export database code into the module.
4.	For each database that you wish to export, enter the following command in the immediate window:<br>ExportAccessDatabase "_Full path to database_", "*Folder to contain exported objects*".
  a.	Note that a new folder will be created in the target folder with the name of the exported database. This is to allow exporting multiple databases to the same target folder while keeping the contents of each exported database in a separate folder.
  b.	If the database to be exported contains a startup form, or an AutoExec macro, startup actions may interfere with the export process, so you should reset the Startup Form property for the database, and remove or rename the AutoExec macro before attempting to call ExportAccessDatabase.
5.	If you wish to further automate this process, you could write a function that, given the path to a folder, enumerates all the databases in the folder, and calls teh ExportAccessDatabase function to export each Microsoft Access database to a target folder.

## Export database code (VBA)

```vba

Option Compare Database
Option Explicit
 \
' Pass in the location of the database to export, and the folder to export to
Sub ExportAccessDatabase(strDBPath As String, exportFolder As String)
    Dim objAccess As Object
    Dim db As Database
    Dim td As TableDef
    Dim qd As QueryDef
    Dim doc As Document
    Dim cont As Container

    On Error GoTo Err_ExportDatabase
    
    ' Create a new instance of Access
    Set objAccess = CreateObject("Access.Application")

    ' Open the database
    objAccess.OpenCurrentDatabase strDBPath
    
    ' Create a new folder using the name of the database to hold all the exported objects if it does not already exist
    exportFolder = exportFolder & Mid(strDBPath, InStrRev(strDBPath, "\"), InStr(strDBPath, ".") - InStrRev(strDBPath, "\")) & "\"
    
    If Dir(exportFolder, vbDirectory) = "" Then
        MkDir exportFolder
    End If

    Set db = objAccess.CurrentDb()

    ' Export all objects to export location with a name based on the type and name of the object

    ' Export Tables
    For Each td In db.TableDefs
        If Left(td.Name, 4) <> "MSys" Then ' Skip Microsoft Access system tables
            objAccess.DoCmd.TransferText acExportDelim, , td.Name, exportFolder & "Table_" & td.Name & ".txt", True
        End If
    Next td

    ' Export Forms
    For Each doc In db.Containers("Forms").Documents
        objAccess.SaveAsText acForm, doc.Name, exportFolder & "Form_" & doc.Name & ".txt"
    Next doc

    ' Export Reports
    For Each doc In db.Containers("Reports").Documents
        objAccess.SaveAsText acReport, doc.Name, exportFolder & "Report_" & doc.Name & ".txt"
    Next doc

    ' Export Macros
    For Each doc In db.Containers("Scripts").Documents
        objAccess.SaveAsText acMacro, doc.Name, exportFolder & "Macro_" & doc.Name & ".txt"
    Next doc

    ' Export Modules
    For Each doc In db.Containers("Modules").Documents
        objAccess.SaveAsText acModule, doc.Name, exportFolder & "Module_" & doc.Name & ".txt"
    Next doc

    ' Export Queries
    For Each qd In db.QueryDefs
        ' Skip Microsoft Access temporary queries
        If Left(qd.Name, 3) <> "~sq" Then
            objAccess.SaveAsText acQuery, qd.Name, exportFolder & "Query_" & qd.Name & ".txt"
        End If
    Next

    objAccess.Quit

    Set db = Nothing
    Set cont = Nothing
    Set objAccess = Nothing

    MsgBox "Export complete to " & exportFolder, vbInformation
    
GoTo Exit_Sub

Err_ExportDatabase:
    MsgBox Err.Number & ": " & Err.Description
 
Exit_Sub:
End Sub

```
