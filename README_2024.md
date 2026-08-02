# Xanadu Pro Change Log 2024

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, Refactored, NOTE ]

**Change Log**

2024-11-23-17-59-58
- Updated ALM Pages. Still more to do.

2024-11-23-15-58-15
- Removed Fields for Gallons and R12.

2024-11-23-15-39-54
- Updated ALM Cards and Portals.
- Updated ALM Import to Delete Addresses From Comms and Blank Addresses aka Non Addresses from Addresses.

2024-11-21-15-21-52
- Cleaned more Cards and Portals.
- Updated eleCard->renderCardWithDiv to support passing the Paged Records Buttons.

2024-11-17-17-04-13
- Updated functions-importALM.php function fmValuesToJoinTables to be easier to understand and validate the join table.

2024-11-17-13-17-24
- Added Users field EmailSendMethod with Select values SMTP, MailTo.
- Moved Constants for Selects to /xan/constants-arrays.php for once place to define the Arrays including query based.
- Addex Settings Companies back to the Admin menu.

2024-11-16-15-47-34
- Added Payments content-page.php.
- Fixed \xan\recs->query by looking for "SELECT" from "Word 1" to "Left 6".
- Removed \xan\module->dbTriggersSQL to spell out the Triggers instead.
- Cleaned up the \xan\module->dbTriggersInstall function.

2024-11-08-18-25-39
- Updated xanDo and xanSave reverted to regular AJAX. Removed Workers, but kept xan.js.worderSafe.js.
- Updated xanDoProgress for Schema Update, Triggers Update, and Massage Update.

2024-11-04-11-37-15
- Removed CalendarTagsJoinMT. Also removed from functions-importALM.php.
- Updated CalendarM and CalendarEvents to use UUIDCalendarTags. Deleted Category column.
- Updated Calendar Edit Event replacing the Category and All Day Text inputs to Drop Downs.

2024-11-03-11-35-37
- Removed qodana.yam from git.

2024-11-02-17-42-36
- Updated functions-importALM.php from functions to a class.
- Renamed Xan_LabsM preventTimeout to preventTimeoutProgressBar.
- Updated Xan_LabsM preventTimeoutProgressBar to no longer add each progress percentage to the console.log.
- Added a constant ELE_WIDTH_DROPDOWN_YES_NO = '2.7rem'.
- Updated ALM FMValues for Comms and Addresses. Used ELE_WIDTH_DROPDOWN_YES_NO. Added Addresses fields for TypeIsBill, TypeIsMail, TypeIsShip.

2024-10-31-14-11-29
- Added a Prevent Timeout example in Xan-LabsM.
- Added a .monospace class to xan.css for a text based progress bar in PRevent Timeout.
- Fixed HomeM and Xan_LabsM Validation.
- Added a function to calculate Pi, for fun.
- Fixed a bug in functions-importALM.php by converting displaying progress in a $table to $resultA.

2024-10-24-18-17-58
- Added functions-importALM.php function fmValuesToJoinTables which creates Xan Join Tables from FM Multi Keys.
- Updated formatting on HomeM->class function cardHome.

2024-10-23-17-58-27
- Replaced calls to \xan\recsGetPDO with \xan\recsGetSQL for most usages with existing Modules so the results use \xan\recs instead of \xan\recsPDO.

2024-10-22-18-10-55
- Renamed recsGet to recsGetPDO.
- Renamed recsGetRelated to recsGetModule. Updated to use \xan\recs instead of \xan\resPDO and to optionally pass $queryColName.
- Updated each \xan\module->getContentImage to accept an optional UUID instead of \xan\recs.
- Updated ContactsMT and ALM_ArtistsMT to share the same getContentTextBrief and getContentImage.

2024-10-18-09-19-42
- Fixed the Photos Uploading in Contacts and Users.
- Fixed the Upload Alert by commenting it out.
- Updated recsGet Function to require BindValues.

2024-10-17-16-26-45
- Updated to have Join Tables for ArtTags, ContactTags, and CalendarTags.
- Updated a few Cards and Portals.
- Moved and Renamed Module Class Files. Example: /xanApp/app/ContactsMT.php is now /xanApp/app/ContactsMT/class.php. This reduces the items in /xanApp/app/ by half.

2024-10-14-13-41-19
- Updated Stripe from v7 to v16.
- Reverted adding Bucket and Pickers within Render. Update Schema will set the Element Types to ELE_TYPE_FILE_BUCKET_DB and ELE_TYPE_PICKER_DB and Generator will use the expected code.

2024-10-12-17-41-23
- Renamed 'Examples' to Xan_Labs.

2024-10-12-17-41-23
- Renamed SettingsExamples to Xan_Labs.
- Renamed Server-404 to Server_404.

2024-10-12-15-56-49
- Updated Khan Class genModule function to automatically use Pickers for 'UUID*' cols and Buckets for '*FN' cols.
- Updated Khan Card with an option for "DeleteKhanBU" to delete older versions of the Module.

2024-10-12-14-00-58
- Misc Cleaning

2024-10-11-15-26-05
- Replaced ALM to use ALM_Artists and ALM_Licensees instead of Contacts just like ALM FM. ALM Modules and Tables now prefixed with "ALM_". Import Tables are now prefixed with "zzImport_ALM_".

2024-09-29-16-29-18
- Added ArtMT's Photo to be the First Related Documents Image.
- Added init.php function appIsActive to check if a App is active.
- Added ArtMT and CollectionsMT Pickers to Documents Related Card. Will show if the App ALM is Active.

2024-09-29-15-44-37
- Added DocumentsMT Image Preview.
- Updated Module Search Term CSS Font Color to go with the Background from color-bg-Yellow to color-bg-text-Yellow.

2024-09-29-15-14-39
- Fixed \xan\eleTimeDB Time Selector.

2024-09-29-14-47-26
- Replaced \xan\module->getEleMeta with new \xan\eleMeta() and removed \xan\module->getEleMeta.
- Renamed \xan\module->getEleMetaRender` to \xan\module->getEleRender.

2024-09-27-17-16-48
- Added $resp->jsAlert to alert when trying to run \xan\PaymentsMT::inst()->recSaveAfter. Will fix during testing.

2024-09-26-17-18-49
- Added $resp->jsAlert to alert when trying to run paymentApprove or paymentDisuburse. Will fix during testing.

2024-09-26-16-05-32
- Looked over the SalesMT and SalesItemsMT do files. Uncommented to test with the rest of the Modules.

2024-09-26-15-33-08
- Fixed router.php path.
- Moved code from SalesItemsMT.php recSaveBefore to recMassage. Removed the now optional recSaveBefore.

2024-09-21-16-41-25
- Updated \xan\module to make record event functions optional rather than just deleting them. Converted recSaveBefore, recNewBefore, recNewAfter, recDuplicateBefore, recDuplicateAfter, recDeleteBefore, recDeleteAfter to be PHP Traits. Those are generally covered by the existing function dbTriggersInstall and recMassage.
- Fixed a bug in /xan/router.php to not load routs where URL Component 1 does not exist.

2024-09-17-15-37-39
- Updated Modules functions dbTriggersInstall and recMassage to be able to ato massage column values on the fly.
- Moved code from onRecsInsertBefore to recMassage.
- Added calls to recMassage into doSave, module->dbMassageAll, recs->recordInsert, and recs->recordUpdate.
- Renamed arrayContainsValue to arrayValueFound and added arrayValueNotFound.
- In do-triggers-update.php, updated to auto loop thru each Module instance to run module->dbTriggersInstall and module->dbMassageAll.

2024-09-05-15-44-38
- Renamed Module StatsMT to StatsM.
- Updated Nav and User Menu to use ModulesD using added function modulesAppWhere.
- Updated all Portals to only be included if included in APP_ACTIVE array.
- Added function moduleIsActive to optionally include non-portal elements based on ModulesD.

2024-09-03-12-04-46
- Added \xan\xan.php functions to cache Modules like Schema.
- Updated functions-misc.php function recsGet to not use the \xan\recs, but similar to make SQL calls before the class is loaded.
- Updated app/SettingsMT/do-backup email to add returns after semicolons to make it easier to read.

2024-09-01-15-39-44
- Added Tables and Modules for ALM.
- Updated Modules cardPortal Function to use If Else. Was using an If for each related table, now uses the Default.
- Updated /router.php to use the First Component as the basis for the sub router.php path. Currently works for the page and do like /contacts/ and /contacts-do/.
- Lots of other bug fixes.

2024-07-27-17-28-55
- Updated eleFileBuckets to allow for one file or many files to be uploaded. Both files upload to the Bucket but only the first file is represented in the database.

2024-07-25-17-45-18
- Updated eleFileBuckets to finish cleaning up.

2024-07-25-16-53-16
- Updated eleFileBuckets to used shared common functions to reduce code duplication on the page.

2024-07-25-15-02-55
- Updated eleFileBuckets to prep for common functions.

2024-07-25-14-48-31
- Updated eleFileBuckets to prep for common functions.

2024-07-24-17-29-12
- Updated Documents List to not show an Image.
- Moved \xan\eleFileBucket javascript function in renderButtonView() to page-resp.php.
- Updated \xan\eleFileBucket to see if a BucketType was already set and checked for URL_ROOT_IMAGES_PLACEHOLDER path first.
- Updated \xan\response jsCallFunction function and xan.js to work with 0 to 9 parameters.
- Updated \xan\module->recCol_BucketEle to remove php styling so js can style. Moved from $code var to a HEREDOC.

2024-07-21-11-34-34
- Updated \xan\module->recCol_ functions to pass \xan\response to make adding scripts easier.
- Updated \xan\recs->queryModule function to no longer need passing \xan\response.
- Updated \xan\dateTimeStrFromString to optionally pass a time offset.
- Added \xan\eleGetID function to replace \xan\module->getEleID.
- Updated page-resp.php to strip html tags from the Page Title.

2024-07-07-17-52-29
- NEED TO FINISH eleFileBucketDB.php to make resizing not hard coded.
- Updated \xan\module organizaion and renamed a few functions.

2024-07-06-17-57-54
- Updated Documents Bucket to show Images, PDFs, and other files. If in a Card, it can be rsized.

2024-06-29-16-31-53
- Updated xanDoSave to use Javascript Workers for the Save Process.
- Updated each Modules \xan\module->recSaveAfter to strip BRs from the header. Uses \xan\module->getContentTextBrief_Header.

2024-06-29-13-21-50
- Updated /login, /passwordreset, /register to not check to see if it's a call from a Worker.

2024-06-27-17-23-41
2024-06-27-17-23-41
- Updated xanDo New Window code to Alert to allow Popup Windows.
- Updated and Renamed some xanDo params.var names. It's a mix of first letter uppercase and lowercase. Goal is camelCase.
- Updated \aloe\response so the header 'Peak' is now 'peak';

2024-06-27-15-42-42
- xanDo now passes the xanID as doID hashed and then validated.
- Updated \xan\peakMemoryUsageGet() to no longer pass a label.
- Updated \aloe\response to set a Response Header for "Peak" the Peak Memory Usage.
- Updated \aloe\session to set a Session SESS_XANID.

2024-06-27-12-15-37
- Updated xanDo to use JS Workers.
- Updated Stats to use a JS Worker to load the Access Log Stats.

2024-06-24-17-55-03
- Updated Stats to not show the Access Log Stats by default with an ugly Show / Hide Button.
- Updated Notes in Khan for clarity.

2024-06-23-16-12-22
- Updated all Portals and Cards with Notes to use a \xan\module->cardExpandButton function for the Expand Button.
- Updated \xan\module->recCol_Note, removing the Card Height Parameter. Now set to 100% Height.
- Updated Khan to generate a Documents Module.
- Updated xan.js to now be two files ( xan.js and xan.js.workerSafe.js ) to separate functions that can be used in Workers.
- Updated AutoLogout to use a JS Worker to watch the Current Time for lapses in Time which indicates the Connection was Lost.

2024-06-18-15-07-23
- Updated FontAwesome from 6.5.1 to 6.5.2.

2024-06-18-14-55-48
- Fixed Modules with missing functions.
- Updated Routers to no longer change the Session ID on each reload except for login and change password.
- Added jsConsoleLog function in \xan\response.
- Separated Stats from Settings as loading Stats is slow.
- Renamed ELE_TYPE_FILE_BUCKET_IMAGE_DB to ELE_TYPE_FILE_BUCKET_DB.
- Updated the eleFileBucketDB to load files using the embed tag for files that can be displayed, otherwise a file icon.

2024-05-04-15-41-36
- Decided to reenable right click prevention.
- Fixed the \xan\module\getListCard class name for the selected records.

2024-04-30-17-52-35
- Fixed the Password Strength Meter on /register, User Menu Change Password, and /users Replace Password Button.

2024-04-30-16-23-52
- Disabled the User Registration page and do.

2024-04-30-16-08-51
- Fixed Picker constant Parameter PICKER_SHOW_GO_BUTTON postion and added PICKER_DATA_AS_GO_BUTTON.

2024-04-30-14-18-44
- Updated modules->cardActionsDetail and modules->cardActionsList to return a string rather than as a value in $resp->extrasD.
- Updated \xan\respAToString to include \n instead of \n\r to remove the double "returns".

2024-04-25-16-03-54
- Moved the functions cardActionsList and cardActionsDetail from individual modules to module.php.
- Added in AccessPermissionsMT.php a cardActionsModal that adds itself using module->cardActionsList.
- Added in functions-dataMassage.php functions arrayCount( array $arrayA ): int and arrayInsert( array $arrayA, int $index, mixed $value ): array.
- Replaced in xan.js the functions xanActionInitList and xanActionInitDetail with xanActionsModalShow.

2024-04-16-16-39-37
- Updated \xan\UsersMT::inst()->pathLastSet to redirect to the last path set.

2024-04-13-17-42-38
- Moved /include/ to https://xanweb.app/xanApp/include/ to be shared between Xanadu Web Apps.
- Deleted /include/. Will need to create another GitHub Project.

2024-04-11-16-23-30
- Added Access Roles and Permissions. Users can be included in many Roles.
- Update eleCard to pass $cardHeaderContentRight for buttons so that the Left side wraps around the buttons.
- Updated Settings and Users Cards to consolidate.
- Updated User Menu to now have User related items and moved Dev items to a Dev Menu.
- Added xan.php function hasAccess( $permName, $UUIDUsers = '' ):bool.
- Updated module.php function getPicker to pass $whereFilterD = [] to be able to pick related records like Dependents.

2024-04-02-18-00-19
- Added Notes from last update.
- Updated QueryBuilder from 2.5.2 to 3.0.0.
- Updated SQL-Parser from 1.3.0 to 1.2.3. Yes, but it was the latest.
- Updated eleSearchBarListDB.php to convert US Dates, Times, and DateTimes to SQL Formats. Allows for user searches in US formats.

2024-03-31-14-13-58
- Added Users Replace Passwords require_once includes for the missing modal.
- Added require_once to UsersMT/do.php: UsersPasswordChange, UsersPasswordReplace, UsersSetPhoneSMSEmail, UsersTBOTPSecretReplace.
- Added Settings Card for Access Log Stats.

2024-03-26-15-33-58
- Updated Home cardHome to use a table.
- Disabled page-resp.php xanDo passing of PHPSTORM debug parameter.

2024-03-23-15-24-50
- Updated xanApp/templates/pdf-default footer files and footers defined in do-print.php files to pass what is in the footer instead of defaults for Printed Date and Page Number.

2024-03-23-14-30-22
- Renamed \xan\recs->massageColForGUI to massageColForEcho
- Removed Constant HTM_BR2.
- Updated Constant HTM_HR to have a height of 1px.
- Added Constant HTM_HR with a height of 2px.
- Updated SettingsMT/do-backup.php to keep 10 backups instead of 20 for disk space savings. Backups should be backed up to another location.
- Updated SettingsMT/do-tasksmonthly_logDumpSQL/php to now save to PATH_ROOT_LOGS instead of PATH_ROOT_BACKUPS as Backups now only keeps the newest 10 files.
- Updated xanApp/templates/pdf-default header and footer files. Using hr height of 2px to separate the header and footer clearly.
- Added functions-dataMassage.php function function strEncodeHTMLEntities so header special char are safe.
- Changed ini_set for error_log so logs filename dates are YYYYMM instead of YYYYMMDD. Daily was create a lot of log files.

2024-03-14-14-31-16
- Updated Khan so only the first detail Card has the Actions Detail.
- Updated Khan to only include the first three columns in QueryOrderBy.
- Updated Contacts getContentTextBrief to use HTML BR to make Lists easier to read.

2024-03-14-13-55-45
- Updated \xan\recs->recordSelect to optionally pass $tableKeyName.
- Removed Nav link to SettingsCompanies since there is portal in Settings.
- Fixed functions-misc.php function dbQueryOrderBy_DropdownItem so dropdown-item text can wrap.
- Removed Settings Phone, Email, Address, Twitter Site/Author.
- Updated constants-and-settings.php to get the Phone, Email, Address, Twitter from the SelectedSettingsCompanies.

2024-03-10-16-44-57
- Updated \xan\Modules getContentText functions to add an options to pass a UUID instead of a \xan\recs.

2024-03-10-14-24-26
- Renamed recsSimple to recsGet.
- Fixed a xan.js so xanScrollToElementInDiv che

2024-03-03-13-54-25
- Changed Portals to use GTRR instead of a Picker.
- Added Logging of PHP Peak Memory Usage in index.php.
- Added Display of PHP Peak Memory Usage to Page Load Time

2024-02-29-15-00-52
- Added Pagination in Portals.

2024-02-17-17-57-20
- Fixed Expand Card for Contacts > Comms.
- Updated Expand Card so the card expands by 50% in width and height in the center of the window.
- Added a Modules > getCardID and ModulesMini > getCardID function to get a consistent name.
- Updated Modules to use the getCardID function.

2024-02-17-14-39-30
- Updated most cards to now have a calculated $cardID with a random at the end.
- Removed the extra New Buttons from Addresses Portal and Comms Portal.
- Removed the extra Modals for New, Dup, Del.

2024-02-16-10-54-35
- Fixed Nav Bar Icons by changing from a Button to just an Icon.
- Updated .btn .fas to 20px.
- Updated Button Gray from WhiteSmoke to Gainsboro to stand out a bit more.
- Updated Button FI size from 2.5rem to 2.0rem.
- Renamed PORTAL_INDEX_WIDTH to INDEX_WIDTH.

2024-02-15-19-10-18
- Updated eleDate, eleDateTime, eleTime.

2024-02-15-17-34-30
- Updated xanDoSave javascript with a semaphore to not save the same table::column and same value rapidly when there are duplicates of the same table::column on the page.
- Updated eleDateDB.php to include the Selector ID as a Class to make resetting when more than one for the same table::column are on the same page.

2024-02-15-12-39-18
- Removed TAGS_ELE_BUTTON_ICON_PORTAL and replaced with TAGS_ELE_BUTTON_ICON to simplify as the size diff was negligable.
- Updated eleDateDB.php to pair the Input and Selector instead of separate. Need to update Time and DateTime.
- Updated element.php to apply the ID also as a Class to make updating an Input with multiple instances.
- Updated xan.js xanEleFlatpickrSetFromString and xanEleFlatpickrSetFromSelect functions to set the value for updating an Input with multiple instances.

2024-02-13-13-22-11
- Refactored Buttons and Colors. No longer using Bootstrap Sizes (SM, RG) and Colors (Primary and Secondary). Now using HTML Named Colors. Goal it to use the same size everywhere with the exception of font size.
- Updated Detail Card Alignment to use TAGS_CELL_RTB and TAGS_CELL_LT.
- Updated z-index for several elements.

2024-02-04-18-37-39
- Updated Portal Cards to no longer have Buttons for Duplicate or Delete. Now part of the Selector Checkboxes and Dropdown Action Button.
- Added a Portal Cards Expand Button that changes the Card from Float Left to Absolute floating above.
- Updated Button Classes to be rounded.
- Updated Modules Content Pages to now have separate Actions for List and Detail. Detail Actions show on the Main Card.
- Moved Modules Content Pages Actions to the Modules Class.
- Moved Modules Content Pages Modals for Duplicate and Delete to the Modules Class.
- Updated eleCard to have a Margin Bottom of 2 to provide more space for the Card Resizer.
- Added Jquery UI to Includes to support Draggable Cards.

2024-01-25-16-23-42
- Updated Modules recNew, recDup, and recDel with an option to Go To the Page on Portals for tables like Contact, but not for tables like SalesItems.
- Updated ELE_CLASS_BUTTON's to remove 'border' as 'border-2' was already added.
- Added User Link Portal on Home.
- Renamed Links UseCount to Visits.
- Updated eleModal to fix the alignment of the Action and Cancel buttons.
- Updated function colValueMassageForGUI to not evaluate a date, time, or datetime if empty. Empty dates were displaying as 1/1/1970.
- Added functions-internet.php function urlHref to make creating links easier.
- Updated module functions getButtonGTRR, getPicker and getPickerContent to fix confusion with the Picker Key ( For the Picker Element ) and Selected Key ( For the Key Selected in the Column.
- Added router.php routes for PlansItems and PurchasesItems.

2024-01-21-15-35-23
- Renamed $elementRendered and $labelRendered to $colCode for cleaner code. Goal is to make Cards and Portals code similar.
- Added /xan/cmdCheck.sh and cmdDo.sh as a way to run shell script. Just create a file in /xan/cmdDoPermissions.do. The script will run when the file is seen, auto delete the do file, update permissions, then log the action.
- Added in Settings a cmdDo Log Card. Shows the current PID, the command to stop, and the most recent 50 log rows.
- Added function fileReadReverse( $path, $rowCount ). Reads a file returning the last $rowCount in reverse order with the last line first.
- Updated Khan and recreated Plans and Purchases to test. Also updated Disbursements, SettingsCompanies, and Users. Removed old Card and Portal files after moving to their respective Module files.
- Updated Auto Logout to write to the console showing the Event and document.visibilityState.
- Added Contants: CARD_WIDTH_0125, FI_CMD, and FI_FILE_TEXT.
- Updated eleTable cellSet so $colSpan is before $rowSpan since col span is used more.
- Added Modules function setURLs() to set the four URL values using the Module Name: "Contacts" becomes "/contacts/".
- Updated page-resp.php by wrapping the Resizeable Observer javascript in a PHP if instead of a JS if. It now does not appear on the Browser Source.

2024-01-15-16-10-19
- Updated Modules recNew to check for $relatedNameKey and $relatedKey.
- Replaced $xanDoNew, $xanDoDup, $xanDoDel with inline strings.
- Replaced JS var names "window.RecDup_UUID" and "window.RecDel_UUID" with "window.recID".
- Updated xan.js to now use the Hand Cursor on the Action Menu Items.

2024-01-15-14-24-07
- Renamed Modules NameTableKey to NameKey.
- Replaced Modules NameTableParam with NameTable.
- Replaced Modules URL setting with a Function.
- Replaced Disbursements module with Khan Generated version.
- Renamed STR_NBSP to HTM_NBSP.
- Added Xdebug Info page.
- Added PHPStorm Xdebug content.
- Changed URL for SettingsCompaniesMT.php from settings-companies to settingscompanies.
- Updated Router to Redirect to /logout/ if not logged in during xanDoSave.
- Updated each Module instance to set the Related Key if set rather than checking for a Related Module name.
- Updated ProjectsTasks to set the ProjectsItems Related Key instead of the Project Key.

2024-01-07-17-51-09
- More cleanup.
- Renamed app folders and classes from "ContactsMT" to "ContactsMT".

2024-01-02-15-29-18
- Fixed Address Zip Lookup, Address Standardize, and Address Correct filenames as they did not match the router.
- Fixed Contacts Print to Word. Was missing some table tags.

2024-01-02-14-12-47
- UPDATING PORTALS is now considered complete. There are a few exceptions for now like Xan_Labs and users.
- Updated jQuery to 3.7.1.
- Updated by renaming from "mmContactsT" to "ContactsMT". Moved all Modules from "modules" to "app". Non Table Modules like "mmHome" is now "homeM".
- Renamed the folders to the same as the Modules.
- Updated Router to use the correct folders. Did not change the URL Component 1 like "contacts" which now routes to ContactsMT.php.

