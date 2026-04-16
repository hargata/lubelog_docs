# Roadmap

## 1.6.4
Released 04/16/2026

### Objectives
- Features
    - Allow users to add multiple reminders to new and existing plans(Issue: #1333, #427)
    - Updated email templates for password reset and registration
    - Refactored code to no longer require app restart when making SMTP-related changes
    - API enhancements for creating backups
    - Add option for users to revert to grid view in mobile
    - Add Automated Events
    - Add validation on CSV imports(Issue: #1343)
- Misc
    - Add warning when user selects locale with mismatched currency and number decimal separator
    - Add additional translation keys
    - Minor code refactor related to SMTP methods

## 1.6.3
Released 03/31/2026

### Objectives
- Bug Fixes
    - Fixed bug with Fuel Economy Units not updating in mobile view
    - Fixed bug with leftover views unoptimized for mobile(Issue: #1315)
    - Fixed Path Traversal on Link Attachments
- Features
    - Add OIDC Registration Options(Issue: #1324)
    - Login-related views now disabled when OIDC-only login is enforced(PR: #1329)
    - Add wrap-around for Description fields in Vehicle History(PR: #1009 by [trevordavies095](https://github.com/trevordavies095))
- Misc
    - Minor code refactor
    - Update dependencies

## 1.6.2
Released 03/16/2026

### Objectives
- Bug Fixes
    - Fixed bug with really long inspection template fields(Issue: #1308)
- Features
    - Display records in cards instead of table rows for mobile view(Issue: #934)
    - Made Add Record button more visible(Issue: #1313)
- Misc
    - Update dependencies

## 1.6.1
Released 02/26/2026

### Objectives
- Bug Fixes
    - Fixed bug with vehicleId in vehicleinfo endpoint(PR: #1269 by [iamdabe](https://github.com/iamdabe))
    - Fixed back/forward buttons in browser not updating selected tabs
    - Fixed bug with costs not displayed in Kiosk Planner
- Features
    - Add query params to URL for adding and editing records
    - Add QR Codes for adding and editing records(Discussion #1275)
    - Failing criterias in Inspection Records are now highlighted
    - Add retry policy(exponential backoff and jitter) to webhooks
    - Add Web Socket to facilitate realtime-sync for dashboards 
- Misc
    - Minor UI and code cleanup. 

## 1.6.0
Released 02/10/2026

### Objectives
- Bug Fixes
    - Fixed minor UI bugs from 1.5.9
- Features
    - Add API endpoints for Notes(PR: #1257 by [iamdabe](https://github.com/iamdabe))
- Misc
    - .NET 10 Migration(update with caution and be prepared to rollback if needed)
    - Resolved some tech debt

## 1.5.9
Released 02/09/2026

### Objectives
- Bug Fixes
    - Fixed bug with decimals in supplies(Issue: #1239)
    - Fixed bug with mobile nav menu on iOS browsers(Issue: #1213)
- Features
    - Add `autoIncludeEquipment` parameter to Odometer Add API endpoint(Issue: #1233, PR: #1234 by [iamdabe](https://github.com/iamdabe))
    - Add supplies to Fuel Records(Issue: #914)
    - Allow API users to append vehicleId in json body(Issue: #1237)
    - Improve support for mobile browsers 
    - Re-designed Supply Usage modal(Issue: #934)
    - Re-designed Planner(Issue: #923)
    - Re-designed Kiosk, now only accepts API Keys for persistent auth
    - Add option to disable zoom on mobile devices
    - Add VehicleId in API response(PR: #1255 by [iamdabe](https://github.com/iamdabe))
- Misc
    - Minor code cleanup(PR: #1256)

## 1.5.8
Released 01/26/2026

### Objectives
- Bug Fixes
    - Fixed Attachment Name bug(Issue: #1217)
    - Fixed line breaks on markdown(Issue: #1219)
    - Fixed bug with moving records
    - Fixed bug with redirect URL post login
- Features
    - Add setting to auto fill Odometer when adding records(Issue: #1212, PR #851 by [Forceu](https://github.com/Forceu))
    - Add API Keys as authentication method(Issue: #855)
- Misc
    - Code Cleanup and bump dependencies
    - Cleaned up Postgres Docker Compose(Issue: #1104)

## 1.5.7
Released 01/11/2026

### Objectives
- Bug Fixes
    - Fixed Global Search with non-English characters(Issue: #1185)
    - Fixed Distance Traveled on Report Header(Issue: #1168)
    - Fixed navbar bug on certain browsers(Issue: #1194)
- Features
    - Add distance export to increment odometer of towed vehicles(Issue: #644)
    - Add Equipment tab to track distance accumulated on tire sets(Issue: #413)
    - Cleaned up the API page
    - Add API endpoint to recalculate odometer record distance(Issue: #1204)

## 1.5.6
Released 12/27/2025

### Objectives
- Bug Fixes
    - Fixed Socket Exhaustion Exception using IHttpClientFactory
    - Force SweetAlerts to comply with dark theme(Issue: #952)
    - Fixed missing validation for purchase and sold date(PR: #1177)
- Features
    - Reminder API Send endpoint now takes an optional reminder id(Issue: #865)
    - Log failed login attempts(Issue: #1145)
    - Add Optional Filters for CSV Exports(Issue: #921)
    - Add API endpoint to retrieve all files in Temp folder
    - Add simplified API endpoints for vehicles(Issue: #1033)
- Misc
    - Minor styling cleanup

## 1.5.5
Released 11/30/2025

### Objectives
- Bug Fixes
    - Fixed bug with exporting records with image in notes(Issue: #1133)
    - Fixed bug with Visible Tabs not allowing for less than 6 visible tabs(Issue: #1147)
- Features
    - Add a confirm password field when setting up credentials for root user(Prevents: #1136)
    - Add User Households to inherit vehicles from a user(Issue: #136, #538, #565, #577)
    - Garage context menu now displays tabs in order based on user config(PR: #1156)
    - Add API endpoints for supply records(PR: #1166)
    - Add API endpoints to retrieve all records for all vehicles(PR: #1167)
- Misc
    - Add logging for JWT validation error for OIDC

## 1.5.4
Released 11/08/2025

### Objectives
- Bug Fixes
    - Fixed bug with Cost Table pagination when there is exactly 5 years of data
    - Fixed bug with Reminder Records when it's created from another record
- Features
    - Custom Widgets are now loaded async with Dashboard tab
    - Add Tags Filter for Reminder API's
    - Add Inspection Tab(Issue: #513, #979)
    - Add functionality to link records via attachments
    - Add functionality to copy link for attachments
    - Add API endpoint for retrieving configured extra fields(Issue: #1119)
- Misc
    - Bump Npgsql and MailKit versions

## 1.5.3
Released 10/13/2025

### Objectives
- Bug Fixes
    - Fixed bug with translation editor when translation content exceeds certain size
    - Fixed bug with cost data table having too many year columns(Issue: #1098)
- Features
    - Allow URLs to individual tabs to be bookmarked
    - Custom Widgets now persists acknowledgement in the session
    - Add bulk collaborator management
    - Add Kestrel Configuration in Server Settings Configurator
    - Add Jwks Endpoint for OIDC to validate issuer signature
    - Add ability to populate certain OIDC settings from well-known url
    - Add Fixed Intervals option for Reminders
- Misc
    - Removed `.env` file and updated docker-compose files
    - Stopgap measure for handling PDF attachments(Issue: #1075)

## 1.5.2
Released 09/19/2025

### Objectives
- Features
    - Add search function in garage(Issue: #1059)
    - Add Attachment Preview for Images(Issue: #1047)
    - Add circle as a shape for vehicle map(PR: #1068) by [Zeromark30](https://github.com/Zeromark30)
    - Add user-configurable auth cookie lifespan, max 90 days(Issue: #951)
- Misc
    - Fixed traefik docker compose(PR: #1067) by [Jekotia](https://github.com/Jekotia)

## 1.5.1
Released 09/09/2025

### Objectives
- Bug Fixes
    - Fix Vehicle Map Opacity for EU locales(Issue: #1039)
    - Fix URL Attachments breaking Attachment Exports(Issue: #1050)
- Features
    - Global Search settings now persist client side(Issue: #1035)

## 1.5.0
Released 08/21/2025

### Objectives
- Bug Fixes
    - Fixed bug with UK MPG conversion applied on EV's(Issue: #1012)
    - Fixed bug with columns disappearing if Enable CSV Import is disabled(Issue: #1005)
- Features
    - Add option to upload a Vehicle Map(Issue: #38)
    - Allow users to select locale different from their system(Issue: #929)
    - Add urgencies param to Reminder GET API(PR: #1026)
- Misc. Tech Debt
    - Updated Npgsql and CsvHelper
    - Migrated from System.IdentityModel.Tokens.Jwt to Microsoft.IdentityModel.JsonWebTokens

## 1.4.9
Released 07/09/2025

### Objectives
- Bug Fixes
    - Fixed bug where non-root users cannot access vehicles(PR: #998)

## 1.4.8
Released 07/02/2025

### Objectives
- Bug Fixes
    - Fixed bug where tag is cleared off after editing a record(Issue: #945)
- Features
    - Update layout
    - Add option to display vehicle image on nav(PR: #950) by [iamdabe](https://github.com/iamdabe)
    - Add UserMetric attribute in Reminder GET methods(Issue: #964)
    - Add Extra Fields for Notes(Issue: #957)
    - Add Parameters for API GET Methods
    - Add Case Insensitive Global Search
    - Updated Document Uploader to also allow link attachments.
    - Add Server Settings Configurator
    - Hides irrelevant Metrics in Report Dropdown(Issue: #867)
    - Add Due Days and Due Distance columns to Reminders
- Misc. Tech Debt
    - Fixed label target in Notes(PR: #949) by [iamdabe](https://github.com/iamdabe)

## 1.4.7
Released 04/29/2025

### Objectives
- Bug Fixes
    - Fixed bug with Extra Field Types not working for Fuel Records(Issue: #931)
- Features
    - Add `userinfo` endpoint parameter for OpenIDConfig to future-proof claims retrieval(PR: #916)
    - Hardened API to accept null for list object types in payload(prevents Issue: #918)
    - Add tooltip for attachment file names(Issue: #926)
    - Add POST/PUT/DELETE API endpoints for Reminders(Issue: #877)
    - Add clickable links in Registration and Reset Password emails

## 1.4.6
Released: 04/02/2025

### Objectives
- Bug Fixes
    - Fixed bug with incorrect average MPG label when toggling consumption units(Issue: #889)
    - Fixed bug with vehicle sold and purchase date not returning in locale-invariant format(Issue: #895)
- Features
    - Add functionality for root users to review server settings and test SMTP config(Issue: #884)
    - Add reminder urgency and due metrics for reminder selection when creating new records(Issue: #893)
    - Add toggle for users to hide Calendar tab(Issue: #879)
    - Add extra field types(Issue: #612)
    - Reworded OIDC error message if auth response does not contain email claim(PR: #901)
    - OIDC scope now defaults to `openid email` if not provided(PR: #903)
    - Added Remote Auth Debug endpoint for advanced OIDC Troubleshooting(PR: #905)

## 1.4.5
Released: 03/06/2025

### Objectives
- Bug Fixes
    - Fixed bug with incorrect MPG labels from tagged partial fuel ups(Issue: #848)
- Features
    - Add API Endpoints for Plans(Issue: #840)
    - Add functionality to re-order table columns(Issue: #780)
    - Dynamically generate locale-sensitive CSV import samples
    - Add check to print individual records when generating vehicle history report(Issue: #857)
    - Add markdown rendering to Kiosk notes(Issue: #856)
    - Minor Quality of Life Improvements(PR: #866)

## 1.4.4
Released: 02/03/2025

### Objectives
- Bug Fixes
    - Fixed bug with duplicating shop supplies to vehicle
    - Fixed bug with replenishing supplies
    - Fixed bug with sorting and filtering
    - Fixed bug with Odometer and Reminder count label
    - Fixed bug with Cost Per Distance traveled(Issue: #825)
    - Fixed bug with Cost Per Day metric when Year is selected(Issue: #824)
- Features
    - Add Basic Auth to the Reminders Calendar Endpoint(Issue: #697)
    - Add functionality to print records(Issue: #801, #800)
    - Add functionality to enable Open Registration(Issue: #805)
    - Add Days interval to Recurring Reminder and Tax Records(Issue: #755)
    - Made parameters optional for Send Reminder API endpoint(defaults to all urgencies)
    - Add Attachments Column(Issue: #823)

## 1.4.3
Released 01/10/2025

### Objectives
- Bug Fixes
    - Fixed bug with fuel mileage for empty odometers(Issue: #796)
- Features
    - Added new endpoint to retrieve Reminders Calendar in ICS format(Issue: #697)
    - Added new endpoint to upload documents and attach documents to records(Issue: #769)
- Misc. Tech Debt
    - Moved user uploaded files out from `wwwroot` to `data` folder(Issue: #785, #260)
    - Moved userConfig.json out from `config` to `data/config`

## 1.4.2
Released 01/02/2025

### Objectives
- Bug Fixes
    - Fixed bug with creating past records for recurring tax records(Issue: #745)
    - Security Fixes
    - Fixed bug where tags are returned as null in API(Issue: #763)
    - Fixed bug on MacOS devices with context menu
- Features
    - Add PUT/DELETE API requests to modify records(Issue: #541)
    - Allow API requests in JSON format.
    - Add Total Distance Traveled label in Gas Records(Issue: #751)
    - Add setting to default to Fuel Unit Cost input(Issue: #744)
    - Reformatted Webhook payloads(Issue: #574)
    - Allow users to filter records by tags on the consolidated report(Issue: #572)
    - Allow users to filter records by date range on consolidated report(Issues: #761, #689)
    - Allow users to insert odometer records from existing records(Issue: #758)
    - Improved tile sizes in garage on mobile devices

## 1.4.1
Released: 11/25/2024

### Objectives
- Bug Fixes
    - Fixed bug with drag and drop for plan items 
    - Fixed bug where plan type does not display correctly in Kiosk mode
    - Fixed bug with sorting in tables.
    - Fixed aggregate label bug when search returns empty results
    - Fixed bug with changes in appsettings.json(Issue: #739)
- Features
    - Cached Report Metrics are now vehicle specific
    - Added option to toggle between 2 and 3 decimal places for fuel consumption(Issue: #723)
    - Deleting records will now replenish requisitioned supplies(Issue: #429)
    - Users can now add supplies to existing records(Issue: #454)
    - Add cost table for multi-year trends(Issue: #716)
    - Sort notes in ascending order by description(Issue: #523)
    - Added Select Mode
    - Remastered the Context Menu
    - Remastered Reminder Record tab.
    - Added SimplyAuto column mapping for imports(Issue: #60)
- Misc. Tech Debt
    - Additional Code Cleanup(PR: #721, #722) with ideas from [Scorpoon](https://github.com/Scorpoon) 

## 1.4.0
Released: 11/14/2024

### Objectives
- Bug Fixes
    - Fix Translation Editor Bug(Issue: #681)
- Features
    - Add Custom Dashboard functionality(Issue: #660, #678)
    - Add Kiosk View for Vehicles, Reminders, and Planners
    - Add functionality to duplicate records across vehicles(Issue: #526)
    - Add Tags to POST API methods(Issue: #684)
    - Add functionality to automatically format decimal inputs(Issue: #611)
    - Allow Custom Logos and Extra Fields in Vehicle Maintenace Report(Issue: #702)
- Misc Tech Debt
    - [Code Cleanup](https://github.com/hargata/lubelog/pull/704) by [Scorpoon](https://github.com/Scorpoon)

## 1.3.9
Released: 10/31/2024

### Objectives
- Bug Fixes
    - Fix AdjustedOdometer endpoint with decimal odometer multiplier 
    - Fix bug with inverted bar chart colors with metric calculations(Issue: #649)
    - Fix bug with average/min/max fuel mileage labels
    - Fix Page Titles
    - Fix misaligned columns when viewed on small screens
    - Fix mobile nav closing on iOS devices when scrolling
- Features
    - Enter key to submit on Forms(Issue: #639)
    - Add functionality to edit extra fields for multiple records(Issue: #483)
    - Add Attachment Exports for Notes
    - Add emphasis lines for API methods in documentation
    - Add support for smaller tabs in smaller screens
    - Add thumbnail resizing(Issue: #616)
    - Add Experimental GPS Integration(Issue: #511)
    - Allow ExtraFields to be displayed in place of LicensePlate(Issue: #485)
    - Add Built-In Translation Downloader and Editor
    - Add functionality to re-order tabs(Issue: #518)
    - Add funtionality to reveal password on password fields
- Misc Tech Debt and Changes
    - Move Delete Vehicle button into Edit Vehicle modal(Issue: #637)
    - Automatically create app schema in existing Postgres container
    - Remastered Admin Panel
    - Improve Code Maintainability(Split VehicleController out)
    - Load sponsors asynchronously for users with slower internet connection

## 1.3.8
Released 09/24/2024

### Objectives
- Add Vehicle Info endpoint documentation
- Add endpoint to get adjusted odometer for vehicle
- Fix Light mode issue on PC with dark mode preference(Issue: #630)
- Add vehicle flag to indicate odometer entry is optional(Issue: #619, #563, #312)
- Updated demo default file

## 1.3.7
Released 09/23/2024

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
- Add ability to disable Registration(Issue: #618)

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