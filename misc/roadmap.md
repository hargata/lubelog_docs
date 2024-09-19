# Roadmap

## 1.3.7
Scheduled Release TBD

### Objectives
- Add Vehicle Info endpoint for third party widgets/dashboard
- Fix minor tooltip bug on touchscreen devices in reminders view
- Add default email recipient for reminder emails(Issue: #517)
- Add ability to login via OICD for root user(Issue: #482)
- Add data table view(Issue: #551)
- Add user-configurable vehicle metric chips(Issue: #537)
- Add color-coded icons for Planner Items(Issue: #598)
- Add custom thresholds for Reminders(Issue: #609)
- Add adaptive theme if Dark Mode is not enabled(Issue: #603)

## 1.3.6
Released 08/26/2024

### Objectives
- Fix Postgres table bug for vehicles with zero records(Issue: #576)
- Add PKCE to OICD Auth(Issue: #568)
- Add fuel type dropdown(Issue: #534)
- Add functionality to upload files on paste(Issue: #570)
- Add Cleanup API method to clear out temp files and unlinked documents/thumbnails
- Add functionality to export extra fields in CSV
- Add Due Date and Odometer in API output for Reminders
- Add tooltip to show configured due date and odometer for reminders(Issue: #531)
- Added Extra Fields to API methods(Issue: #588)

## 1.3.5
Released 07/10/2024

### Objectives
- Allow currency values greater than six figures(Issue #515; PR #542 by [kapcake](https://github.com/kapcake))
- Add maskable icons for Android PWA(PR #519 by [NateWright](https://github.com/NateWright))
- Auto-create PostgreSQL schema on init(PR #508 by [snpaul22](https://github.com/snpaul22))
- Functionality to reset password for root user without disabling auth
- Make initial odometer reading readonly by default to prevent unintended edits
- Reminder recurring intervals are now based on reminder metric(Issue #512)
- Map extra fields to records via CSV import(Issue #545)

## 1.3.4
Released 06/04/2024

### Objectives
- Fix bug where zero cost supplies cannot be selected
- Add missing translation keys
- Fix bug with locale where space is used for thousand separator
- Fix bug with SMTP servers with no authentication

## 1.3.3
Released 05/21/2024

### Objectives
- Remove Commercial Restrictions
- Fix SweetAlert2 Restrictions
- Add Sponsorship Tiers

## 1.3.2
Released 04/25/2024

### Objectives
- Replace .NET SMTPClient with MailKit
- Fix bug with persistent metric on Dashboard
- Fix bug where year dropdown does not show Odometer Record year

## 1.3.1
Released 04/23/2024

### Objectives
- Fix donation link colors not being visible in light mode
- Fix alternate fuel units in European locale
- Temporarily persist selected metrics in Dashboard

## 1.3.0
Released 04/08/2024

### Objectives
- Allow users to increment from last reported odometer reading when creating records
- Cache records including unsaved changes to prevent accidental closing of modal
- Global search
- Functionality to edit plan record templates

## 1.2.9
Released 03/29/2024

### Objectives
- Allow users to select multiple reminders to push back when creating new record
- Add tagging feature to Reminders
- Add option to copy Supplies attachments when requisitioned by new Plan/Service/Repair/Upgrade records
- Add chips to vehicle tile in Garage tab for Mileage and Past Due/Very Urgent Reminders
- Reminders renewed via creation of records now use the date/mileage of the record for next interval
- Improve Reminders tab usability on mobile devices

## 1.2.8
Released 03/21/2024

### Objectives
- Fix security vulnerability where unauthorized users can access uploaded files
- Improve LiteDB Implementation to bypass concurrency issue
- Add URL Parser to Extra Field Values

## 1.2.7
Released 03/16/2024

### Objectives
- Add Odometer Adjustments for vehicle where odometer units differ from user settings or vehicles with swapped odometers that no longer reflect actual mileage
- Fix bug where Odometer Records are not deleted when the vehicle is deleted
- Fix bug where translation are not being backed up
- Add functionality to edit multiple fuel records at once
- Add webhooks
- Add logging for backup restoration

## 1.2.6
Released 03/13/2024

### Objectives
- Made columns automatically shrink when extra fields are visible
- Improve file names when exporting attachments
- Fixed bug with black boxes showing up under Vehicle Maintenance Report
- Add Initial Odometer Reading and Distance metric to Odometer Records
- Distance Traveled chart in Reports tab now rely solely on odometer records
- Added functionality to edit multiple odometer records at once

## 1.2.5
Released 03/07/2024

### Objectives
- State persistence for column visibilities
- Flex basis for table columns to take up as much space as needed(no more white spaces)
- Statistics between records (average distance traveled and average days elapsed)
- Allow users to set their own acceptable file extensions for documents upload
- Allow users to inject root user credentials via Environment Variables
- Allow users to hide sold vehicles
- Allow users to configure reminder urgency thresholds
- Column-specific search
- Added a Message of the Day(MOTD) feature.
