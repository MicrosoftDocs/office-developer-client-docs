---
title: 'How to: Send an E-Mail Given the SMTP Address of an Account'
TOCTitle: 'How to: Send an E-Mail Given the SMTP Address of an Account'
ms:assetid: 4ff4aaac-54ba-45c7-8b2e-aeba35af1e56
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff462095(v=office.15)
ms:contentKeyID: 55119865
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# How to: Send an E-Mail Given the SMTP Address of an Account

This topic shows how to create an e-mail and send it from a Microsoft Outlook account, given the Simple Mail Transfer Protocol (SMTP) address of that account.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Helmut Obertanner provided the following code examples. Helmut's expertise is in Office Developer Tools for Visual Studio and Outlook. Helmut maintains a professional site at <a href="http://www.outlooksharp.de/">X4Uelectronix</a>.</p></td>
</tr>
</tbody>
</table>


The following code examples contain the SendEmailFromAccount and GetAccountForEmailAddress methods of the Sample class, implemented as part of an Outlook add-in project. Each project adds a reference to the Outlook Primary Interop Assembly, which is based on the [Microsoft.Office.Interop.Outlook](https://msdn.microsoft.com/en-us/library/bb610835\(v=office.15\)) namespace. The SendEmailFromAccount method accepts as input arguments a trusted [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) object, and strings that represent the subject, body, a semicolon-delimited list of recipients, and the SMTP address of an e-mail account. SendEmailFromAccount creates a [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object and initializes the [To](https://msdn.microsoft.com/en-us/library/bb624372\(v=office.15\)), [Subject](https://msdn.microsoft.com/en-us/library/bb611353\(v=office.15\)), and [Body](https://msdn.microsoft.com/en-us/library/bb646600\(v=office.15\)) properties with the given arguments. To find the [Account](https://msdn.microsoft.com/en-us/library/bb645103\(v=office.15\)) object from which to send the e-mail, SendEmailFromAccount calls the GetAccountForEmailAddress method, which matches the given SMTP address with the [SmtpAddress](https://msdn.microsoft.com/en-us/library/bb623516\(v=office.15\)) property of each account for the current profile. The matching Account object is returned to SendEmailFromAccount, which then initializes the [SendUsingAccount](https://msdn.microsoft.com/en-us/library/bb623679\(v=office.15\)) property of the MailItem with this Account object, and sends the MailItem.

The following is the Visual Basic code example, followed by the C\# code example.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook

Namespace OutlookAddIn2
    Class Sample
        
        Shared Sub SendEmailFromAccount(ByVal application As Outlook.Application, _
            ByVal subject As String, ByVal body As String, ByVal recipients As String, ByVal smtpAddress As String)

            ' Create a new MailItem and set the To, Subject, and Body properties.
            Dim newMail As Outlook.MailItem = DirectCast(application.CreateItem(Outlook.OlItemType.olMailItem), Outlook.MailItem)
            newMail.To = recipients
            newMail.Subject = subject
            newMail.Body = body

            ' Retrieve the account that has the specific SMTP address.
            Dim account As Outlook.Account = GetAccountForEmailAddress(application, smtpAddress)
            ' Use this account to send the e-mail.
            newMail.SendUsingAccount = account
            newMail.Send()
        End Sub

        Shared Function GetAccountForEmailAddress(ByVal application As Outlook.Application, ByVal smtpAddress As String) As Outlook.Account

            ' Loop over the Accounts collection of the current Outlook session.
            Dim accounts As Outlook.Accounts = application.Session.Accounts
            Dim account As Outlook.Account
            For Each account In accounts
                ' When the e-mail address matches, return the account.
                If account.SmtpAddress = smtpAddress Then
                    Return account
                End If
            Next
            Throw New System.Exception(String.Format("No Account with SmtpAddress: {0} exists!", smtpAddress))
        End Function

    End Class
End Namespace
```

``` csharp
using System;
using System.Text;
using Outlook = Microsoft.Office.Interop.Outlook;

namespace OutlookAddIn1
{
    class Sample
    {
        public static void SendEmailFromAccount(Outlook.Application application, string subject, string body, string to, string smtpAddress)
        {

            // Create a new MailItem and set the To, Subject, and Body properties.
            Outlook.MailItem newMail = (Outlook.MailItem)application.CreateItem(Outlook.OlItemType.olMailItem);
            newMail.To = to;
            newMail.Subject = subject;
            newMail.Body = body;

            // Retrieve the account that has the specific SMTP address.
            Outlook.Account account = GetAccountForEmailAddress(application, smtpAddress);
            // Use this account to send the e-mail.
            newMail.SendUsingAccount = account;
            newMail.Send();
        }


        public static Outlook.Account GetAccountForEmailAddress(Outlook.Application application, string smtpAddress)
        {

            // Loop over the Accounts collection of the current Outlook session.
            Outlook.Accounts accounts = application.Session.Accounts;
            foreach (Outlook.Account account in accounts)
            {
                // When the e-mail address matches, return the account.
                if (account.SmtpAddress == smtpAddress)
                {
                    return account;
                }
            }
            throw new System.Exception(string.Format("No Account with SmtpAddress: {0} exists!", smtpAddress));
        }

    }
}
```

## See also

#### Other resources

[Mail](mail.md)

