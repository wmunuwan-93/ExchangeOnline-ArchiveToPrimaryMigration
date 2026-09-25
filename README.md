# ExchangeOnline-ArchiveToPrimaryMigration
Overview

Invoke-Unarchive is a PowerShell-based migration utility designed to move content from an Exchange Online Personal Archive Mailbox back into the user's Primary Mailbox using Exchange Web Services (EWS) and OAuth App Authentication.

The tool automatically recreates the archive folder structure in the primary mailbox, performs high-performance batch item moves, and generates detailed migration logs and audit reports for verification and compliance purposes.

Key Features
OAuth 2.0 App-Only authentication using Microsoft Entra ID
Exchange Online Personal Archive support
Automatic archive folder discovery
Automatic primary mailbox folder creation
Folder hierarchy preservation
Batch item migration using EWS MoveItems API
Retry handling for transient failures
Detailed execution logging
CSV audit reporting
Progress tracking during migration
Large mailbox support through paged item enumeration
Mailbox impersonation support
Migration Workflow

The script performs the following operations:

Authenticates to Microsoft Entra ID using Client Credentials Flow.
Obtains an Exchange Online OAuth access token.
Connects to Exchange Online EWS.
Validates Primary Mailbox accessibility.
Validates Archive Mailbox accessibility.
Enumerates all archive folders.
Recreates missing folders in the primary mailbox.
Maps archive folders to primary mailbox folders.
Enumerates all archive items.
Migrates items in configurable batches.
Generates migration logs.
Generates a CSV audit report.
Requirements
PowerShell
Windows PowerShell 5.1 or later
PowerShell 7.x supported
Exchange Online
Exchange Online mailbox with Personal Archive enabled
EWS access enabled
Microsoft Entra Application

The application must have:

Exchange.ManageAsApp application permission
Admin consent granted
