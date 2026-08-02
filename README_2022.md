# Xanadu Pro Change Log 2022

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, Refactored, NOTE ]

**Change Log**

2022-08-07-15-03-18
- Moved Examples from Home to Settings Examples.
- Added Examples to Users Menu in the Admin only section.
- Renamed URL_BASE to URL_ROOT for older pages with commented out usages.

2022-08-07-13-15-15
- Tested Backups after the refactoring of Root Web and Root Other.
- Updated Settings Backups to show the percentage free along with teh free space. Both Root Web and Root Other will be shown if the free space differs.

2022-08-06-13-21-23
- Refactored web root to a folder "rootWeb".
- Refactored files and backups from external drive to a folder "rootOther".

2022-08-04-16-02-44
- Updated Settings Backups to only show zip files.

2022-08-04-15-36-52
- Tested APIRequests by running a 'Random Amount' request and 'Process Queue' request but an error occured and the entire queue was not processed. Updated so each request in the queue gets its own response and a summary if responses are returned.

2022-08-02-17-44-17
- Added Constants for FM_USE_FMREST and FM_FIELDS_KEY, used with class \xan\fmResponse.
- Added class \xan\fmResponse, used with class \xan\fmDB. fmResponse normalizes the data from either FileMaker XML Web Publishing convered to JSON or from FileMaker Data API using fmRest.
- Updated class \xan\fmDB to support offset, script, scriptParam, scriptPreRequest, scriptPreRequestParam, scriptPreSort, scriptPreSortParam.
- Updated class \xan\fmDB notes about Portals, Omit, and Sort.

2022-08-02-17-05-28
- Added /init_foo.xanweb.app.php called in init.php as an example.

2022-08-02-16-33-03
- Added /include/pheditor File Manager and implemented in /fileManager.php.

2022-07-22-17-32-56
- Added Settings Tasks Monthly to Router and Crontab to run on the first of the month.
- Added do-tasks-weekly-logDumpSQL to 'Settings Tasks Monthly' to dump records older than 90 days from LogAudit and LogEvent to the Backups folder along with regular backups.
- Added tableName parameter to \xan\recordsExport to bypass the need for the metaMoule.

2022-07-21-15-34-39
- Added sample code to init.php for opcache static + preload.
- Added an Audit Log Viewer to Contacts, Comms, Settings, Users, APIRequests with a shared Modal instantiated on page-resp.php.
- Added a xan.php function to create a Table for the Audit Log Modal.
- Added Settings do-modal-logAudit.php file to populate the Modal with the Audit Log.

2022-07-14-18-23-06
- Updated Aloe Session to only set the Session ID Name if not already set in order to set the session in Router, explained below.
- Updated Router to Init the Session without regenerating the Session ID to be able to Log the Request. Had to update Aloe Session to not re-set teh Session ID Name if it was already set.
- Added Xan phpFileInfo function to create a clean way to see where an event occurred with the File Name, Line Number, Namespace, Class, Function, and Path
- Updated Send SMS and Email to log what was sent but with the exception of the message body HTML and Text.
- Updated Log calls to use the phpFileInfo function.

2022-07-12-18-30-38
- Updated calls to logEventToFile to logEventToSQL. Passed __NAMESPACE__ . '_' . __CLASS__ . '_' . __FUNCTION__ in Desc1 when possible.

2022-07-12-15-37-16
- Added to Setting Tasks Often, Auto Deletion of Users that have not clicked the Registration Link within 3 days.

2022-07-11-18-12-05
- Updated Router Login and Router Logout to terminate the session on load.
- Updated Status Session to show a list of User Session and Path Sessions. Empty Sessions are not shown, but the count is shown.
- Added Settings Tasks Often that purges 'sess_' and 'CURLCOOKIE' files.
- Updated Crontab to run Settings Tasks Often.
- Updated Settings Backup to prefix the file with the APP_NAME.
- Updated to keep 20 backups and must be less than thirty days old.
- Renamed \xan\dateStrFromString to \xan\dateTimeStrFromString.
- Updated Stats Sessions to show sessions with an email address first. Then with a Path, then the remaining sessions.

2022-07-09-16-52-19
- Updated abstract class module functions 'getListItem' and 'getListItemWImage' to highlight the search term, if passed.
- Added Xan functions for strSubstituteCaseInsensitive and strSubstituteCaseMatching.

2022-07-09-15-05-02
- Updated Settings Backups table padding and changed the zip icon to a new icon.
- Updated Settings Backups to auto delete backups older than 30 days but only the most recent 5 backups.
- Update eleTable, removing right and bottom padding from table but keeping left and top padding.

2022-07-09-13-00-34
- Replaced zip functions with zipfile class. Previous addDir did not work. Now it does!
- Fixed xanDo function timeBegin and timeEnd math to use valueOf instead of getMilliseconds. Was always less than a second but now accurate.
- Updated Settings Backups to zip SQL, Code, and Files into one zip file. Auto deletes after 15 days. Sends text message with time spent, total size of backup, and a link to the backup for easy downloading.
- Updated Moment from 2.29.2 to 2.29.4.

2022-07-05-17-36-31
- Removed use of xan.js date function in favor of Moment. Added a comment: "Use moment.js like in xanEleFlatpickrSetFromSelect function in this file."

2022-07-05-17-23-26
- Updated colValueMassageForGUI to handle Currency from SettingsSchema Table EleFormatAs Column. Works on Contacts Detail and Print.

2022-07-05-16-27-24
- Added Calendar Module. Moved Calendar from Home to the Module.
- Enabled Delete Button.
- Changed Month View to be the default.
- Added Category field in Calendar Edit Dialog.
- Added 2 second delay in refetching events after Save and Delete.

2022-07-04-17-14-50
- Changed ChangeLog location in README.md.

2022-07-04-17-08-48
- Updated Home adding Button for APIs, Calendar, IMAP, Khan, Stripe, and Tests. These were hidden but available as home/apis... Now exposed.

2022-07-04-16-09-14
- Updated Khan module generator to work with the Schema Table.

2022-07-02-17-17-54
- Removed Moment 2.24.0.

2022-07-02-17-12-58
- Updated Moment 2.24.0 to 2.29.2.

2022-07-02-17-02-55
- Removed eleMeta details from Module files. Set Non Table Module files like Table Module files.
- Updated templates/calendar.js.

2022-07-02-16-06-33
- Removed Google Fonts in the PDF-Default Template.
- Removed Bootstrap Icons, removed DayPilot in favor of FullCalendar.
- Updated to DataTables 1.12.1, FontAwesome 6.1.1, FullCalendar 5.10.2/free.
- Removed Dark Mode. For Dark Mode in Browser, consider https://darkreader.org.
- Moved source of eleMeta details from Module files to an SQL Table, populated and updateable using information_schema.columns.
- Renamed ELE_AS_DEFINED to ELE_AS_INPUT.
- Added app/settings/do-certbot-log-email.php called from crontab.

2022-02-15-16-12-41
- Added FontAwesome 6.0.0. Updated PSoS icons to fa-beat-fade.
- Added DayPilot Lite 2022.1.362.

2022-02-15-14-14-51
- Khan can now generate a new project from database tables and some info about the tables. Cleaned code during the creation of Khan.
- Added Modules for Projects and Transactions. Need to customize for FMSB like functionality.
- Added Module property for colNamesToMassageA to set a list of columns to be massaged. If not set, column types date, time, datetime, decimal, and integers are massaged.
- Changed how row massaging works. Now called only when needed for headers, printing to html/pdf, etc.
- Added filenameClean function to clean up filenames for printing to html/pdf.
- Added DATETIME_FORMATS for US Dates.
- Rewrote xan.js xanDateTimeStrToStr. Now uses PHO formats like n/j/Y
- Updated xan.css dividers for less white space.

2022-01-18-17-00-25
- Khan dev began. Khan is a Module Generator. Just add SQL tables and columns, write a little php to describe the module, and generate!
- Khan needs the files for printing, rec delete, rec duplocate, and rec create.
- Moved fm-example-1 module from BRG our of the project and into "z fmRest" folder.

