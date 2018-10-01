---
title: 'Create a Helper Class to Access Common Outlook Item Members'
TOCTitle: 'Create a Helper Class to Access Common Outlook Item Members'
ms:assetid: 344ff07d-e448-4418-910d-930e60f7381f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn292518(v=office.15)
ms:contentKeyID: 55119845
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create a Helper Class to Access Common Outlook Item Members

This example shows how to implement an OutlookItem helper class that accesses common properties and methods of Outlook item objects, saving the overhead of testing for and casting to a specific item object before accessing these common item members.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>The following code example is an excerpt from <em>Programming Applications for Microsoft Office Outlook 2007</em>, from <a href="http://www.microsoft.com/learning/books/default.mspx">Microsoft Press</a> (ISBN 9780735622494, copyright Microsoft Press 2007, all rights reserved).</p>
<p><a href="http://www.amazon.com/gp/product/0735622493?ie=utf8%26tag=msmsdn-20%26linkcode=as2%26camp=1789%26creative=9325%26creativeasin=0735622493">Buy this book</a></p>
<p><a href="https://msdn.microsoft.com/en-us/library/cc513844(v=office.15)">Sample chapters</a></p></td>
</tr>
</tbody>
</table>


Many Outlook items have similar properties and methods. For example, the Application, Attachments, Body, Categories, and Class properties, and Close, Copy, and Display methods are common to all Outlook item object. The COM-based Outlook object model returns the generic Visual Basic Object instead of the exact item type for many members. For example, the [CurrentItem](https://msdn.microsoft.com/en-us/library/bb611743\(v=office.15\)) property returns a generic Object. On the other hand, the strongly typed managed code environment requires you to cast the Object representing an Outlook item to the exact Outlook type such as MailItem. The OutlookItem helper class uses reflection to expose properties and methods that are common to all items. The class helps you cast the object to the exact type and provides the convenience of directly using common item properties or methods on the OutlookItem object. This is a very useful technique and several other how-to topics listed in the See Also section below take advantage of this helper class.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

```vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```vb
Option Strict On

Imports System
Imports System.Reflection
Imports System.Runtime.InteropServices
Imports System.Diagnostics

Namespace SampleCodeAddinVB
    Friend Class OutlookItem

        Private m_Item As Object 'the wrapped Outlook item
        Private m_Type As Type 'type for the Outlook item
        Private m_Args As Object() 'dummy argument array
        Private m_TypeOlObjectClass As System.Type


#Region "OutlookItem Constants"
        Private Const OlActions As String = "Actions"
        Private Const OlApplication As String = "Application"
        Private Const OlAttachments As String = "Attachments"
        Private Const OlBillingInformation As String = "BillingInformation"
        Private Const OlBody As String = "Body"
        Private Const OlCategories As String = "Categories"
        Private Const OlClass As String = "Class"
        Private Const OlClose As String = "Close"
        Private Const OlCompanies As String = "Companies"
        Private Const OlConversationIndex As String = "ConversationIndex"
        Private Const OlConversationTopic As String = "ConversationTopic"
        Private Const OlCopy As String = "Copy"
        Private Const OlCreationTime As String = "CreationTime"
        Private Const OlDelete As String = "Delete"
        Private Const olDisplay As String = "Display"
        Private Const OlDownloadState As String = "DownloadState"
        Private Const OlEntryID As String = "EntryID"
        Private Const OlFormDescription As String = "FormDescription"
        Private Const OlGetInspector As String = "GetInspector"
        Private Const OlImportance As String = "Importance"
        Private Const OlIsConflict As String = "IsConflict"
        Private Const OlItemProperties As String = "ItemProperties"
        Private Const OlLastModificationTime As String = "LastModificationTime"
        Private Const OlLinks As String = "Links"
        Private Const OlMarkForDownload As String = "MarkForDownload"
        Private Const OlMessageClass As String = "MessageClass"
        Private Const OlMileage As String = "Mileage"
        Private Const OlMove As String = "Move"
        Private Const OlNoAging As String = "NoAging"
        Private Const OlOutlookInternalVersion As String = "OutlookInternalVersion"
        Private Const OlOutlookVersion As String = "OutlookVersion"
        Private Const OlParent As String = "Parent"
        Private Const OlPrintOut As String = "PrintOut"
        Private Const OlPropertyAccessor As String = "PropertyAccessor"
        Private Const OlSave As String = "Save"
        Private Const OlSaveAs As String = "SaveAs"
        Private Const OlSaved As String = "Saved"
        Private Const OlSensitivity As String = "Sensitivity"
        Private Const OlSession As String = "Session"
        Private Const OlShowCategoriesDialog As String = "ShowCategoriesDialog"
        Private Const OlSize As String = "Size"
        Private Const OlSubject As String = "Subject"
        Private Const OlUnRead As String = "UnRead"
        Private Const OlUserProperties As String = "UserProperties"
#End Region

#Region "Constructor"
        Public Sub New(ByVal Item As Object)
            m_Item = Item
            m_Type = m_Item.GetType()
            m_Args = New Object() {}
        End Sub
#End Region

#Region "Public Methods and Properties"
        Public ReadOnly Property Actions() As Outlook.Actions
            Get
                Return CType(GetPropertyValue(OlActions), Outlook.Actions)
            End Get
        End Property

        Public ReadOnly Property Application() As Outlook.Application
            Get
                Return CType(GetPropertyValue(OlApplication), Outlook.Application)
            End Get
        End Property

        Public ReadOnly Property Attachments() As Outlook.Attachments
            Get
                Return CType(GetPropertyValue(OlAttachments), Outlook.Attachments)
            End Get
        End Property

        Public Property BillingInformation() As String
            Get
                Return CType(GetPropertyValue(OlBillingInformation), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlBillingInformation, value)
            End Set
        End Property

        Public Property Body() As String
            Get
                Return CType(GetPropertyValue(OlBody), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlBody, value)
            End Set
        End Property

        Public Property Categories() As String
            Get
                Return CType(GetPropertyValue(OlCategories), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlCategories, value)
            End Set
        End Property

        Sub Close(ByVal SaveMode As Outlook.OlInspectorClose)
            Dim myArgs() As Object = {SaveMode}
            Me.CallMethod(OlClose, myArgs)
        End Sub

        Public Property Companies() As String
            Get
                Return CType(GetPropertyValue(OlCompanies), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlCompanies, value)
            End Set
        End Property

        Public ReadOnly Property ConversationIndex() As String
            Get
                Return CType(GetPropertyValue(OlConversationIndex), String)
            End Get
        End Property

        Public ReadOnly Property ConversationTopic() As String
            Get
                Return CType(GetPropertyValue(OlConversationTopic), String)
            End Get
        End Property

        Function Copy() As Object
            Copy = Me.CallMethod(OlCopy)
        End Function

        Public ReadOnly Property CreationTime() As System.DateTime
            Get
                Return CType(GetPropertyValue(OlCreationTime), System.DateTime)
            End Get
        End Property

        Sub Display()
            Me.CallMethod(olDisplay)
        End Sub

        Public ReadOnly Property DownloadState() As Outlook.OlDownloadState
            Get
                Return CType(GetPropertyValue(OlDownloadState), Outlook.OlDownloadState)
            End Get
        End Property

        Public ReadOnly Property EntryID() As String
            Get
                Return CType(GetPropertyValue(OlEntryID), String)
            End Get
        End Property

        Public ReadOnly Property FormDescription() As Outlook.FormDescription
            Get
                Return CType(GetPropertyValue(OlFormDescription), Outlook.FormDescription)
            End Get
        End Property

        Public ReadOnly Property GetInspector() As Outlook.Inspector
            Get
                Return CType(GetPropertyValue(OlGetInspector), Outlook.Inspector)
            End Get
        End Property

        Public Property Importance() As Outlook.OlImportance
            Get
                Return CType(GetPropertyValue(OlImportance), Outlook.OlImportance)
            End Get
            Set(ByVal value As Outlook.OlImportance)
                SetPropertyValue(OlImportance, value)
            End Set
        End Property

        Public ReadOnly Property InnerObject() As Object
            Get
                Return m_Item
            End Get
        End Property

        Public ReadOnly Property IsConflict() As Boolean
            Get
                Return CType(GetPropertyValue(OlIsConflict), Boolean)
            End Get
        End Property

        Public ReadOnly Property ItemProperties() As Outlook.ItemProperties
            Get
                Return CType(GetPropertyValue(OlItemProperties), Outlook.ItemProperties)
            End Get
        End Property

        Public ReadOnly Property LastModificationTime() As System.DateTime
            Get
                Return CType(GetPropertyValue(OlLastModificationTime), System.DateTime)
            End Get
        End Property

        Public ReadOnly Property Links() As Outlook.Links
            Get
                Return CType(GetPropertyValue(OlLinks), Outlook.Links)
            End Get
        End Property

        Public Property MarkForDownload() As Outlook.OlRemoteStatus
            Get
                Return CType(GetPropertyValue(OlMarkForDownload), Outlook.OlRemoteStatus)
            End Get
            Set(ByVal value As Outlook.OlRemoteStatus)
                SetPropertyValue(OlMarkForDownload, value)
            End Set
        End Property

        Public Property MessageClass() As String
            Get
                Return CType(GetPropertyValue(OlMessageClass), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlMessageClass, value)
            End Set
        End Property

        Public Property Mileage() As String
            Get
                Return CType(GetPropertyValue(OlMileage), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlMileage, value)
            End Set
        End Property

        Function Move(ByVal DestinationFolder As Outlook.Folder) As Object
            Dim myArgs() As Object = {DestinationFolder}
            Move = Me.CallMethod(OlMove, myArgs)
        End Function

        Public Property NoAging() As Boolean
            Get
                Return CType(GetPropertyValue(OlNoAging), Boolean)
            End Get
            Set(ByVal value As Boolean)
                SetPropertyValue(OlNoAging, value)
            End Set
        End Property

        Public ReadOnly Property [Class]() As Outlook.OlObjectClass
            Get
                Return CType(GetPropertyValue(OlClass), Outlook.OlObjectClass)
            End Get
        End Property

        Public ReadOnly Property OutlookInternalVersion() As Long
            Get
                Return CType(GetPropertyValue(OlOutlookInternalVersion), Long)
            End Get
        End Property

        Public ReadOnly Property OutlookVersion() As String
            Get
                Return CType(GetPropertyValue(OlOutlookVersion), String)
            End Get
        End Property

        Public ReadOnly Property Parent() As Outlook.Folder
            Get
                Return CType(GetPropertyValue(OlParent), Outlook.Folder)
            End Get
        End Property

        Sub PrintOut()
            Me.CallMethod(OlPrintOut)
        End Sub

        Public ReadOnly Property PropertyAccessor() As Outlook.PropertyAccessor
            Get
                Return CType(GetPropertyValue(OlPropertyAccessor), Outlook.PropertyAccessor)
            End Get
        End Property

        Sub Save()
            Me.CallMethod(OlSave)
        End Sub

        Sub SaveAs(ByVal Path As String, ByVal Type As Outlook.OlSaveAsType)
            If Path.Length = 0 Then
                Exit Sub
            Else
                Dim myArgs() As Object = {Path, Type}
                Me.CallMethod(OlSaveAs, myArgs)
            End If
        End Sub

        Public ReadOnly Property Saved() As Boolean
            Get
                Return CType(GetPropertyValue(OlSaved), Boolean)
            End Get
        End Property

        Public Property Sensitivity() As Outlook.OlSensitivity
            Get
                Return CType(GetPropertyValue(OlSensitivity), Outlook.OlSensitivity)
            End Get
            Set(ByVal value As Outlook.OlSensitivity)
                SetPropertyValue(OlSensitivity, value)
            End Set
        End Property

        Public ReadOnly Property Session() As Outlook.NameSpace
            Get
                Return CType(GetPropertyValue(OlSession), Outlook.NameSpace)
            End Get
        End Property

        Sub ShowCategoriesDialog()
            Me.CallMethod(OlShowCategoriesDialog)
        End Sub

        Public ReadOnly Property Size() As Long
            Get
                Return CType(GetPropertyValue(OlSize), Long)
            End Get
        End Property

        Public Property Subject() As String
            Get
                Return CType(GetPropertyValue(OlSubject), String)
            End Get
            Set(ByVal value As String)
                SetPropertyValue(OlSubject, value)
            End Set
        End Property

        Public Property UnRead() As Boolean
            Get
                Return CType(GetPropertyValue(OlUnRead), Boolean)
            End Get
            Set(ByVal value As Boolean)
                SetPropertyValue(OlUnRead, value)
            End Set
        End Property

        Public ReadOnly Property UserProperties() As Outlook.UserProperties
            Get
                Return CType(GetPropertyValue(OlUserProperties), Outlook.UserProperties)
            End Get
        End Property
#End Region

#Region "Private Helper Functions"

        Private Sub SetPropertyValue(ByVal PropertyName As String, ByVal Value As Object)
            Try
                m_Type.InvokeMember(PropertyName, _
                 BindingFlags.Public Or BindingFlags.SetField Or BindingFlags.SetProperty, _
                 Nothing, _
                 m_Item, _
                 New Object() {Value})
            Catch ex As Exception
                Debug.Write(String.Format("OutlookItem: SetPropertyValue for {0} Exception: {1}", _
                 PropertyName, ex.Message))
            End Try
        End Sub

        Private Function GetPropertyValue(ByVal PropertyName As String) As Object
            Try
                Return m_Type.InvokeMember(PropertyName, _
                 BindingFlags.Public Or BindingFlags.GetField Or BindingFlags.GetProperty, _
                 Nothing, _
                 m_Item, _
                 m_Args)
            Catch ex As SystemException
                Debug.Write(String.Format("OutlookItem: GetPropertyValue for {0} Exception: {1} ", _
                 PropertyName, ex.Message))
                Return Nothing
            End Try
        End Function

        Private Overloads Function CallMethod(ByVal MethodName As String) As Object
            Try
                Return m_Type.InvokeMember(MethodName, _
                BindingFlags.Public Or BindingFlags.InvokeMethod, _
                Nothing, _
                m_Item, _
                m_Args)
            Catch ex As SystemException
                Debug.Write(String.Format("OutlookItem: CallMethod for {0} Exception: {1} ", _
                 MethodName, ex.Message))
                Return Nothing
            End Try
        End Function

        Private Overloads Function CallMethod(ByVal MethodName As String, ByVal Args() As Object) As Object
            Try
                Return m_Type.InvokeMember(MethodName, _
                BindingFlags.Public Or BindingFlags.InvokeMethod, _
                Nothing, _
                m_Item, _
                Args)
            Catch ex As SystemException
                Debug.Write(String.Format("OutlookItem: CallMethod for {0} Exception: {1} ", _
                 MethodName, ex.Message))
                Return Nothing
            End Try
        End Function
#End Region
    End Class
End Namespace
```

```csharp
using System;
using System.Reflection;
using System.Runtime.InteropServices;
using System.Diagnostics;

namespace SampleCodeAddinCS
{
    class OutlookItem
    {
        private object m_item;  // the wrapped Outlook item
        private Type m_type;  // type for the Outlook item 
        private object[] m_args;  // dummy argument array
        private System.Type m_typeOlObjectClass;

        #region OutlookItem Constants

        private const string OlActions = "Actions";
        private const string OlApplication = "Application";
        private const string OlAttachments = "Attachments";
        private const string OlBillingInformation = "BillingInformation";
        private const string OlBody = "Body";
        private const string OlCategories = "Categories";
        private const string OlClass = "Class";
        private const string OlClose = "Close";
        private const string OlCompanies = "Companies";
        private const string OlConversationIndex = "ConversationIndex";
        private const string OlConversationTopic = "ConversationTopic";
        private const string OlCopy = "Copy";
        private const string OlCreationTime = "CreationTime";
        private const string OlDisplay = "Display";
        private const string OlDownloadState = "DownloadState";
        private const string OlEntryID = "EntryID";
        private const string OlFormDescription = "FormDescription";
        private const string OlGetInspector = "GetInspector";
        private const string OlImportance = "Importance";
        private const string OlIsConflict = "IsConflict";
        private const string OlItemProperties = "ItemProperties";
        private const string OlLastModificationTime = "LastModificationTime";
        private const string OlLinks = "Links";
        private const string OlMarkForDownload = "MarkForDownload";
        private const string OlMessageClass = "MessageClass";
        private const string OlMileage = "Mileage";
        private const string OlMove = "Move";
        private const string OlNoAging = "NoAging";
        private const string OlOutlookInternalVersion = "OutlookInternalVersion";
        private const string OlOutlookVersion = "OutlookVersion";
        private const string OlParent = "Parent";
        private const string OlPrintOut = "PrintOut";
        private const string OlPropertyAccessor = "PropertyAccessor";
        private const string OlSave = "Save";
        private const string OlSaveAs = "SaveAs";
        private const string OlSaved = "Saved";
        private const string OlSensitivity = "Sensitivity";
        private const string OlSession = "Session";
        private const string OlShowCategoriesDialog = "ShowCategoriesDialog";
        private const string OlSize = "Size";
        private const string OlSubject = "Subject";
        private const string OlUnRead = "UnRead";
        private const string OlUserProperties = "UserProperties";
        #endregion

        #region Constructor
        public OutlookItem(object item)
        {
            m_item = item;
            m_type = m_item.GetType();
            m_args = new Object[] { };
        }
        #endregion

        #region Public Methods and Properties
        public Outlook.Actions Actions
        {
            get
            {
                return this.GetPropertyValue(OlActions) as Outlook.Actions;
            }
        }

        public Outlook.Application Application
        {
            get
            {
                return this.GetPropertyValue(OlApplication) as Outlook.Application;
            }
        }

        public Outlook.Attachments Attachments
        {
            get
            {
                return this.GetPropertyValue(OlAttachments) as Outlook.Attachments;
            }
        }

        public string BillingInformation
        {
            get
            {
                return this.GetPropertyValue(OlBillingInformation).ToString();
            }
            set
            {
                SetPropertyValue(OlBillingInformation, value);
            }
        }

        public string Body
        {
            get
            {
                return this.GetPropertyValue(OlBody).ToString();
            }
            set
            {
                SetPropertyValue(OlBody, value);
            }
        }

        public string Categories
        {
            get
            {
                return this.GetPropertyValue(OlCategories).ToString();
            }
            set
            {
                SetPropertyValue(OlCategories, value);
            }
        }


        public void Close(Outlook.OlInspectorClose SaveMode)
        {
            object[] MyArgs = { SaveMode };
            this.CallMethod(OlClose);
        }

        public string Companies
        {
            get
            {
                return this.GetPropertyValue(OlCompanies).ToString();
            }
            set
            {
                SetPropertyValue(OlCompanies, value);
            }
        }

        public Outlook.OlObjectClass Class
        {
            get
            {
                if (m_typeOlObjectClass == null)
                {
                    // Note: instantiate dummy ObjectClass enumeration to get type.
                    //       type = System.Type.GetType("Outlook.OlObjectClass") doesn't seem to work
                    Outlook.OlObjectClass objClass = Outlook.OlObjectClass.olAction;
                    m_typeOlObjectClass = objClass.GetType();
                }
                return (Outlook.OlObjectClass)System.Enum.ToObject(m_typeOlObjectClass, this.GetPropertyValue(OlClass));
            }
        }

        public string ConversationIndex
        {
            get
            {
                return this.GetPropertyValue(OlConversationIndex).ToString();
            }
        }

        public string ConversationTopic
        {
            get
            {
                return this.GetPropertyValue(OlConversationTopic).ToString();
            }
        }

        public object Copy()
        {
            return (this.CallMethod(OlCopy));
        }

        public System.DateTime CreationTime
        {
            get
            {
                return (System.DateTime)this.GetPropertyValue(OlCreationTime);
            }
        }

        public void Display()
        {
            this.CallMethod(OlDisplay);
        }

        public Outlook.OlDownloadState DownloadState
        {
            get
            {
                return (Outlook.OlDownloadState)this.GetPropertyValue(OlDownloadState);
            }
        }

        public string EntryID
        {
            get
            {
                return this.GetPropertyValue(OlEntryID).ToString();
            }
        }

        public Outlook.FormDescription FormDescription
        {
            get
            {
                return (Outlook.FormDescription)this.GetPropertyValue(OlFormDescription);
            }
        }


        public Object InnerObject
        {
            get
            {
                return this.m_item;
            }
        }

        public Outlook.Inspector GetInspector
        {
            get
            {
                return this.GetPropertyValue(OlGetInspector) as Outlook.Inspector;
            }
        }

        public Outlook.OlImportance Importance
        {
            get
            {
                return (Outlook.OlImportance)this.GetPropertyValue(OlImportance);
            }
            set
            {
                SetPropertyValue(OlImportance, value);
            }
        }

        public bool IsConflict
        {
            get
            {
                return (bool)this.GetPropertyValue(OlIsConflict);
            }
        }

        public Outlook.ItemProperties ItemProperties
        {
            get
            {
                return (Outlook.ItemProperties)this.GetPropertyValue(OlItemProperties);
            }
        }

        public System.DateTime LastModificationTime
        {
            get
            {
                return (System.DateTime)this.GetPropertyValue(OlLastModificationTime);
            }
        }

        public Outlook.Links Links
        {
            get
            {
                return this.GetPropertyValue(OlLinks) as Outlook.Links;
            }
        }

        public Outlook.OlRemoteStatus MarkForDownload
        {
            get
            {
                return (Outlook.OlRemoteStatus)this.GetPropertyValue(OlMarkForDownload);
            }
            set
            {
                SetPropertyValue(OlMarkForDownload, value);
            }
        }

        public string MessageClass
        {
            get
            {
                return this.GetPropertyValue(OlMessageClass).ToString();
            }
            set
            {
                SetPropertyValue(OlMessageClass, value);
            }
        }

        public string Mileage
        {
            get
            {
                return this.GetPropertyValue(OlMileage).ToString();
            }
            set
            {
                SetPropertyValue(OlMileage, value);
            }
        }

        public object Move(Outlook.Folder DestinationFolder)
        {
            object[] myArgs = { DestinationFolder };
            return this.CallMethod(OlMove, myArgs);
        }

        public bool NoAging
        {
            get
            {
                return (bool)this.GetPropertyValue(OlNoAging);
            }
            set
            {
                SetPropertyValue(OlNoAging, value);
            }
        }

        public long OutlookInternalVersion
        {
            get
            {
                return (long)this.GetPropertyValue(OlOutlookInternalVersion);
            }
        }

        public string OutlookVersion
        {
            get
            {
                return this.GetPropertyValue(OlOutlookVersion).ToString();
            }
        }

        public Outlook.Folder Parent
        {
            get
            {
                return this.GetPropertyValue(OlParent) as Outlook.Folder;
            }
        }

        public Outlook.PropertyAccessor PropertyAccessor
        {
            get
            {
                return this.GetPropertyValue(OlPropertyAccessor) as Outlook.PropertyAccessor;
            }
        }

        public void PrintOut()
        {
            this.CallMethod(OlPrintOut);
        }

        public void Save()
        {
            this.CallMethod(OlSave);
        }

        public void SaveAs(string path, Outlook.OlSaveAsType type)
        {
            object[] myArgs = { path, type };
            this.CallMethod(OlSaveAs, myArgs);
        }

        public bool Saved
        {
            get
            {
                return (bool)this.GetPropertyValue(OlSaved);
            }
        }

        public Outlook.OlSensitivity Sensitivity
        {
            get
            {
                return (Outlook.OlSensitivity)this.GetPropertyValue(OlSensitivity);
            }
            set
            {
                SetPropertyValue(OlSensitivity, value);
            }
        }

        public Outlook.NameSpace Session
        {
            get
            {
                return this.GetPropertyValue(OlSession) as Outlook.NameSpace;
            }
        }

        public void ShowCategoriesDialog()
        {
            this.CallMethod(OlShowCategoriesDialog);
        }

        public long Size
        {
            get
            {
                return (long)this.GetPropertyValue(OlSize);
            }
        }

        public string Subject
        {
            get
            {
                return this.GetPropertyValue(OlSubject).ToString();
            }
            set
            {
                SetPropertyValue(OlSubject, value);
            }
        }

        public bool UnRead
        {
            get
            {
                return (bool)this.GetPropertyValue(OlUnRead);
            }
            set
            {
                SetPropertyValue(OlUnRead, value);
            }
        }

        public Outlook.UserProperties UserProperties
        {
            get
            {
                return this.GetPropertyValue(OlUserProperties) as Outlook.UserProperties;
            }
        }

        #endregion

        #region Private Helper Functions
        private object GetPropertyValue(string propertyName)
        {
            try
            {
                // An invalid property name exception is propagated to client
                return m_type.InvokeMember(
                    propertyName,
                    BindingFlags.Public | BindingFlags.GetField | BindingFlags.GetProperty,
                    null,
                    m_item,
                    m_args);
            }
            catch (SystemException ex)
            {
                Debug.WriteLine(
                    string.Format(
                    "OutlookItem: GetPropertyValue for {0} Exception: {1} ",
                    propertyName, ex.Message));
                throw;
            }
        }

        private void SetPropertyValue(string propertyName, object propertyValue)
        {
            try
            {
                m_type.InvokeMember(
                    propertyName,
                    BindingFlags.Public | BindingFlags.SetField | BindingFlags.SetProperty,
                    null,
                    m_item,
                    new object[] { propertyValue });
            }
            catch (SystemException ex)
            {
                Debug.WriteLine(
                   string.Format(
                   "OutlookItem: SetPropertyValue for {0} Exception: {1} ",
                   propertyName, ex.Message));
                throw;
            }
        }

        private object CallMethod(string methodName)
        {
            try
            {
                // An invalid property name exception is propagated to client
                return m_type.InvokeMember(
                    methodName,
                    BindingFlags.Public | BindingFlags.InvokeMethod,
                    null,
                    m_item,
                    m_args);
            }
            catch (SystemException ex)
            {
                Debug.WriteLine(
                    string.Format(
                    "OutlookItem: CallMethod for {0} Exception: {1} ",
                    methodName, ex.Message));
                throw;
            }
        }

        private object CallMethod(string methodName, object[] args)
        {
            try
            {
                // An invalid property name exception is propagated to client
                return m_type.InvokeMember(
                    methodName,
                    BindingFlags.Public | BindingFlags.InvokeMethod,
                    null,
                    m_item,
                    args);
            }
            catch (SystemException ex)
            {
                Debug.WriteLine(
                    string.Format(
                    "OutlookItem: CallMethod for {0} Exception: {1} ",
                    methodName, ex.Message));
                throw;
            }
        }
        #endregion

    }
}
```

## See also

#### Tasks

[Display Selected Items in the Active Explorer](how-to-display-selected-items-in-the-active-explorer.md)

[Open and Display the Contents of an iCalendar File](how-to-open-and-display-the-contents-of-an-icalendar-file.md)

[Open and Display the Contents of an iCalendar File](how-to-open-and-display-the-contents-of-an-icalendar-file.md)

[Assign Categories to an Item](how-to-assign-categories-to-an-item.md)

[Implement a Wrapper for Inspectors and Track Item-Level Events in Each Inspector](how-to-implement-a-wrapper-for-inspectors-and-track-item-level-events-in-each-inspector.md)



[General Outlook Items](general-outlook-items.md)

