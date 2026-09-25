# ExchangeOnline-ArchiveToPrimaryMigration
__Overview__

Invoke-Unarchive is a PowerShell-based migration utility designed to move content from an Exchange Online Personal Archive Mailbox back into the user's Primary Mailbox using Exchange Web Services (EWS) and OAuth App Authentication.

The tool automatically recreates the archive folder structure in the primary mailbox, performs high-performance batch item moves, and generates detailed migration logs and audit reports for verification and compliance purposes.

__Key Features__

- OAuth 2.0 App-Only authentication using Microsoft Entra ID
- Exchange Online Personal Archive support
- Automatic archive folder discovery
- Automatic primary mailbox folder creation
- Folder hierarchy preservation
- Batch item migration using EWS MoveItems API
- Retry handling for transient failures
- Detailed execution logging
- CSV audit reporting
- Progress tracking during migration
- Large mailbox support through paged item enumeration
- Mailbox impersonation support
- Migration Workflow

__The script performs the following operations:__

- Authenticates to Microsoft Entra ID using Client Credentials Flow.
- Obtains an Exchange Online OAuth access token.
- Connects to Exchange Online EWS.
- Validates Primary Mailbox accessibility.
- Validates Archive Mailbox accessibility.
- Enumerates all archive folders.
- Recreates missing folders in the primary mailbox.
- Maps archive folders to primary mailbox folders.
- Enumerates all archive items.
- Migrates items in configurable batches.
- Generates migration logs.
- Generates a CSV audit report.

__Requirements__

__PowerShell__
  - Windows PowerShell 5.1 or later
  - PowerShell 7.x supported

__Exchange Online__
  - Exchange Online mailbox with Personal Archive enabled
  - EWS access enabled

__Microsoft Entra Application__

__The application must have:__
  - Exchange.ManageAsApp application permission
  - Admin consent granted

__EWS Managed API__

The script requires: "Microsoft.Exchange.WebServices.dll"

Default path: "C:\Program Files\PackageManagement\NuGet\Packages\Exchange.WebServices.Managed.Api.2.2.1.2\lib\net35\Microsoft.Exchange.WebServices.dll"

__Usage__

$Secret = ConvertTo-SecureString "ClientSecret" -AsPlainText -Force

.\Invoke-Unarchive.ps1 -Mailbox user@contoso.com -TenantId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -ClientId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -ClientSecret $Secret

__Logging__

Execution logs are automatically written to: ".\Logs\"

__Log entries include:__

- Authentication status
- Folder discovery
- Folder creation
- Batch migration progress
- Errors and warnings
- Migration summary

__Audit Reporting__

The script generates a CSV audit report for every migration.


__Disclaimer__

This tool is provided "as is" without warranty of any kind. Always test in a non-production environment before running against production mailboxes. The author assumes no responsibility for data loss, mailbox corruption, or service interruptions resulting from the use of this script.
