# Get-MailboxReport.ps1
PowerShell script to generate a report of mailboxes, including information such as item count, total size, and other useful attributes.

## SYNOPSIS
Get-MailboxReport.ps1 - Mailbox report generation script.

## DESCRIPTION

Generates a report of useful information for the specified server, database, mailbox or list of mailboxes. Use only one parameter at a time depending on the scope of your mailbox report.

Single mailbox reports are output to the console, while all other reports are output to a CSV file.

## Parameters
- -All
Generates a report for all mailboxes in the organization.

- -Server
Generates a report for all mailboxes on the specified server.

- -Database
Generates a report for all mailboxes on the specified database.

- -File
Generates a report for mailbox names listed in the specified text file.

- -Mailbox
Generates a report only for the specified mailbox.

- -Filename
(Optional) Specifies the CSV file name to be used for the report.
If no file name specificed then a unique file name is generated by the script.

- -SendEmail
Specifies that an email report with the CSV file attached should be sent.

- -MailFrom
The SMTP address to send the email from.

- -MailTo
The SMTP address to send the email to.

- -MailServer
The SMTP server to send the email through.

- -CSVEncoding
Specifies the encoding for the exported CSV file. Valid values are Unicode, UTF7, UTF8, ASCII, UTF32, BigEndianUnicode, Default, and OEM. The default is ASCII.

- -CSVDelimiter
Specifies a delimiter to separate the property values in the CSV output file. The default is a comma (,). Enter a character, such as a colon (:). To specify a semicolon (;), enclose it in quotation marks.

- -DisplayProgressBar
Set to $true to display progress bar under report generating. Can increase script execution time.

## Usage examples

Example 1
```powershell
> .\Get-MailboxReport.ps1 -Database DB01
```
Returns a report with the mailbox statistics for all mailbox users in database DB01

Example 2
```powershell
> .\Get-MailboxReport.ps1 -All -SendEmail -MailFrom exchangereports@exchangeserverpro.net -MailTo alan.reid@exchangeserverpro.net -MailServer smtp.exchangeserverpro.net
```

Returns a report with the mailbox statistics for all mailbox users and send an email report to the specified recipient.

## More Information
A detailed explanation of this script and a demonstration video are available at:
http://exchangeserverpro.com/powershell-script-create-mailbox-size-report-exchange-server-2010

## Credits
Initially written by Paul Cunningham, updated by community

Website:	http://exchangeserverpro.com

Twitter:	http://twitter.com/exchservpro

##Additional Credits:
Chris Brown, http://www.flamingkeys.com
Boe Prox, http://learn-powershell.net/
Stefan Midjich, http://stefan.midjich.name
Wojciech Sciesinski, https://www.linkedin.com/in/sciesinskiwojciech

## Change Log
- V1.00, 02/02/2012 - Initial version
- V1.01, 27/02/2012 - Improved recipient scope settings, exception handling, and custom file name parameter.
- V1.02, 16/10/2012 - Reordered report fields, added OU, primary SMTP, some specific folder stats, archive mailbox info, and updated to show DAG name for databases when applicable.
- V1.03, 27/05/2014 - Modified behavior of Server parameter. Added UseDatabaseQuotaDefaults, AuditEnabled, HiddenFromAddressListsEnabled, IssueWarningQuota, ProhibitSendQuota, ProhibitSendReceiveQuota. Added email functionality. Added auto-loading of snapin for simpler command lines in Task Scheduler
- V1.04, 31/05/2015 - Fixed bug reported by some Exchange 2010 users
- V1.05, 10/06/2015 - Fixed bug with date in email subject line
- V1.06, 24/04/2106 - Additional fields added: ExchangeGuid,ArchiveGuid. Corrected connecting to Exchange PowerShell if the script running from ordinary PowerShell. Displaying progress bar disabled by default to increase speed. Additional parameters CSVEncoding, CSVDelimiter added to improve a CSV file exporting. Help updated and reformatted
- V1.07, 24/04/2016 - removed unused variables: reporthtml, spacer. Code reformatted