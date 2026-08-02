# Xanadu Pro Change Log 2021

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, Refactored, NOTE ]

**Change Log**

2021-12-21-14-54-20
- Added fm-example-1 module from BRG.
- Renamed date, dateTime, and time functions.
- Updated xan.css.

2021-12-21-13-23-43
- Added BingMapsKey to Settings.
- Added DATETIME_FORMAT_USDATE.
- Remvoed BRG Test

2021-12-07-14-42-13
- Added ID and Name attributes to Cards, Card Header, and Card Body. Header and Body will be the Card ID or Name with an underscore suffix.
- Upated Settings > Backups buttons to return the Card Content via Ajax.

2021-12-07-12-56-24
- Removed 'content-cards.php' and moved code to 'content-page.php'.
- Added PATH_ROOT_ALT for Backups and Files.
- Added Font Icons for Database, Code, Files, and Download.
- Added Settings > Backup Card with ability to backup SQL, Files, and Code with Delete All and individual Delete buttons.

2021-11-28-17-25-22
- Updated Buttons from Secondary to Primary
- Updated content-cards.php to use $mmTable.
- Updated all do.php files to use a switch statement instead of a series of if statements.
- Updated router.php to use a switch statement instead of a series of if statements.
- Set the Card min-height to CARD_HEIGHT_0100.

2021-11-28-15-06-58
- Added Access Keys for Print, Search, and Records First, Last, Previous, and Next.
- Added Gravatars in Comms Email with button to "Set Photo".
- Added a Photo button to Clear the Photo.
- Added Address County, Country, Latitude, Longitude with Labels.
- Added Address Buttons for Zip Lookup, Street Standardization, and Address Correction.
- Cleaned Contacts Comms code.
- Updated Nginx and page-resp.php Content-Security-Policy to allow Gravatar.
- Renamed recsSquerySimple to recsGet.
- Renamed STR_BR to HTML_BR. Added STR_DIV_DIVIDER.
- Added Comms do.php.
- Cleaned do.php to use a case statement.
- Added a Tiny Button: ELE_CLASS_BUTTON_SET . STR_SP . TEXTSM and SECONDARY.
- Renamed \xan\ 'dir' funtions to 'path' functions.
- Renamed \xan\urlContent to \xan\urlTextContent.
- Added \xan\urlDownloadToPath to download a url file to a path.

2021-11-20-16-15-05
- Updated CSS Vars to be based on bootstrap grays.
- Moved CSS from page-resp.php to /xan/xan.css.

2021-11-16-15-45-14
- Added Optional Bootstrap Tooltips to Buttons.
- Removed ContactsNameUpdate and UsersNameUpdate from the Contacts and Users content-pages.php files and deleted the Contacts and Users do-*-nameUpdate.php.
- Renamed setColCalcs to onSaveColCalcs in metaModules.
- Added onSaveJSActions in metaModules.
- Updated onSaveColCalcs and onSaveJSFunctions in mmAPIRequestsT.php, mmContactsT.php.

2021-11-12-18-04-35
- Moved js function xanDoJS from page-resp.php to /xan/xan.js to use it in xanDo and xanSave.
- Updated xan-save.php to reply with rowsD and jsActionsA.
- Added mm abstract function setColCalcs.
- Updated /contacts/content-cards.php content header to have a specific ID for the selected contact so xanSave can update via jsActionsA.

2021-11-09-21-04-29
- Renamed mm->getDisplayName to mm->getDisplayTitle.
- Removed NameUpdate of Header and List Item from Contacts and Users. Working to replace with Calulations.
- Reworked /xan/xan-save.php.

2021-11-05-11-38-00
- Removed an extra space in the page header before the colon.
- Added a Tooltip to the Image Upload button.

2021-11-04-15-01-27
- Added class and instance for $xan->get( '123' ) to make adding PHP to JS via {}.
- Renamed Tags to make more sense.

2021-10-19-19-06-35
- Added Functions \xan\strChr.
- Changed User Menu Items Order.
- Added Stats Process Pools Count.
- Renamed and rearanged constants for Heights and Widths. Removed some unused contants. Changed size number to be based on percentages starting with 100% = 0100.

2021-10-02-18-11-41
- Added xan-mysqlTools.php for MySQL Backup and Restore.
- Added Home Examples for MySQL Backup and Restore.
- Added Home Examples for FileWrite, Gzip, UnGzip, Read, Delete.
- Added \xan\ functions for fileGzip, fileUngzip, fileDelete.

2021-09-21-22-50-15
- Updated Bootstrap 4.5.0 to 5.1.1. Need to update Buttons that use FontIcons.
- Fixed Contacts Picker Clear Button which was adding WHERE when finding all records.
- Added function \xan\eleTable->generateDemoData.
- Added Colors for Heat Map to xan.php constants from https://www.schemecolor.com/hot-and-cold.php
- Added a param in \xan\eleTable->generateDemoData to display as a Heatmap.
- Added functions \xan\arrayValuesUnique, \xan\arrayValuesRemove.
- Separated Array and Dict functions to be named like arrayImplode or arrayDImplode. Both ar arrays, but these names help to separate how they work.

2021-09-21-15-38-55
- Renamed $tableEle->dataTableScriptOnLoad to $tableEle->dataTableInit
- Updated calls of strtolower to \xan\strCaseLower.
- Update DataTable CSS.
- Added DataTable FI_ORDER for row reordering.
- Added DataTable params so Buttons and Filter can be placed at the top/bottom let/right.

2021-09-09-14-21-51
- Removed the function strTagsRemoveScript and all calls to it.
- Removed most uses of ob_start to HEREDOC JS/HTML. Keeping ob_start when PHP looping is needed.
- Fixed Contacts Comms 'go' buttons showing and hiding. Renamed CallPhoneLink to PhoneCallLink to match PhoneSMSLink.
- Renamed \xan\strFilterKeep functions to remove the 'Keep'.
- Fixed \xan\eleTable->render loop that gets the rowMax and colMax. Was using the last row's col count rather than the using the largest colMax.

2021-09-07-11-45-02
- Fixed APIRequest Printing.
- Removed one use of ob_start to HEREDOC JS/HTML.
- Added Card Widths 4x to 9x.
- Updated each page to Load Content Immediately rather than optionally via AJAX after page load.
- Added functions for numRound, cssSizeFactor.
- Updated functions strFilterKeepNumbers and strFilterKeepAlphanumeric to also include decimal point and dash.
- Updated Cards to be Resizeable by default.

2021-09-06-14-20-21
- Removed page-resp.php head meta logout. Using setTimeout redirect instead.
- Added page-resp.php XSS Headers was missing.

2021-09-05-17-08-25
- Updated Contacts to no longer have a content load now or later making now be the only choice.
- Updated Table Constructor to only add an ID if the ID is not empty.
- Updated page-resp.php JS to be in functions. Reordered too.

2021-09-05-15-10-04
- Updated DataTables example on Home.

2021-09-02-15-59-10
- Added DataTables.net 1.11.0 to Includes and an example on Home in the Table Card.
- Changed colors in datatables.min.css from Green: #31b131 to gray and Red: #d33333 to gray.
- Added 4 Font Icons: Filter, Excel, PDF, and Clipboard. Already had Print.

2021-08-26-16-24-56
- Removed Stacktable.js as it was not used.

2021-08-26-14-19-38
- Added Note in init.php regarding MySQL Sort Buffer Size for version > 8.0.17
- Verified that all SQL calls use binding when using WHERE. Updated one SQL call.

2021-08-24-18-46-07
- Fixed SearchBar. Was missing the D in public $resp->reqPostD.
- Updated Home URL check for 'more', 'more2', 'morepurge' for demo purposes.
- Updated GPS to be 10 seconds.
- Added an IP Geolocation to Home via xanDo.

2021-08-19-13-35-55
- Updated Readme.
- Added IP Geocode function \xan\ipGeocode using https://ipstack.com/.

2021-08-19-12-51-36
- Updated \xan\urlContent.

2021-08-17-17-16-27
- Fixed backticks in Contacts List Images to show, Contact Picker, and Select 'Other...'.
- Updated Comms Portal to use \xan\get::TAGS_ELE_BUTTON_ONCLICK and added mr-1.
- Updated page-resp.php so the navbar, header, and content align.

2021-08-17-13-37-14
- Added ddeboer-imap to includes along with xan/imap class.
- Added IMAP Example to Home.
- Updated Home to put each Example in a Card.

2021-08-17-12-10-33
- Replaced \recs\recsDumpSQL with \recs\recordsExport

2021-07-18-17-02-13
- Merged xan-utility.php into xan.php. Removed xan-utility.php.
- Replaced all calls to \xan\tags to use \xan\get.

2021-07-15-17-34-47
- Added \xan\recs $idSelected to store the selected ID on the recs object.
- Added \xan\get TAG functions. Need to replace individual $tag calls.
- Renamed \xan\response $reqPathComponentsD back to $reqPathComponentsA since it's an array not dictionary.
- Renamed \xan\response functions so the suffix is Get or Set. NounVerb is the goal.
- Added \xan\tags property for $otherD for 'other' values. Used to pass file upload JS on Success or Problem.
- Added xan-utility.php function require_once_recursive.
- Updated \xan\filenameClean to work on filenames and no longer considers the path.

2021-07-05-13-26-29
- Renamed 'moduleMeta' to 'module'. Removed 'meta' from each subclass. Enclosing folder moved to root and named 'modules'.
- Renamed \xan\response $reqPostD, $reqPathComponentsD to append a D.
- Added \xan\response $reqIDsD to replace individual $reqIDs.

2021-07-01-17-28-45
- Organized the Loading Scripts including renaming files in /xan.
- Removed Setting Headers and a Metatag as it's now handled in NGINX.

2021-06-27-16-35-58
- Added functions for pathGetFileNameFull, pathGetFileNameNoExtension, pathGetExtension, pathGetPath, and filenameClean.

2021-06-26-15-43-01
- Added CURL timeout options in the API calls.
- Removed APIRequests Name Update.
- Removed APIRequests ContactPicker and New Button.
- Removed APIRequests Actions options Duplicate and Delete.
- Updated \xan\fileWrite to separate the Path and Filename. Path is created if it doesn't exist. File is written if Path exists.
- Updated calls to \xan\fileWrite to separate the Path and Filename.

2021-06-24-17-22-01
- Rolled back and reappied these changes.
- Changed Constants order in class-xan.php.
- Added \xan\get class for getting a class instance liek: \xan\get::TAGS_CELL_LEFT_MIDDLE().
- Replaced $tagsCell... variables with a new \xan\get class with static functions.

2021-06-22-14-55-13
- Added a meta tag for theme-color and set to the same color as the Nav Bar.
- Added a border-top to the Nav Bar.

2021-06-22-14-40-24
- Added /postit.php which lets GET requests be POSTed.
- Deprecated metaModule->getListRow to refactor a replacement. Started on the replacement on /app/apirequests/content-cards.php.
- Updated eleTable->cellset to add params for $rowGroup (thead|tbody|tfoot) and $isSticky.
- Updated eleTable->render to use cellset params $rowGroup and $isSticky.
- Updated eleTable->__construct to remove the $tagCellsEmpty param. Now sets in constuct and can still be overridden.
- Renamed eleMeta->widthForTable to eleMeta->eleWidthTable.
- Added eleMeta properties $valueHeader, $valueRow, $valueFooter for setting table values temporarily.
- Updated eleMeta->eleAlign to now accepts TEXT_ALIGN_LEFT, TEXT_ALIGN_RIGHT, TEXT_ALIGN_CENTER, TEXT_ALIGN_JUSTIFY.
- Added and Renamed CARD_HEIGHT_x Constants for easier access to quarters and thirds.
- Using Microsoft Edge for Mac, started fixing its suggestions.
    - Added a header for 'X-Content-Type-Options', "nosniff"
    - Added a title tag to the nav Dropdown.

2021-06-14-17-42-18
- Moved Files to another different dir than the app. This allows for putting files on another disk.
    - Moved upload.php to the app root. Need to refactor.
    - Updated PATH_ROOT and URL_ROOT var names to be consistent.
    - Moved upload to the root.
    - Fixed Contacts List Card Image ID.
- Fixed a bug with getListItemWImage and getListItem where on row x, x-1 extra html tr tags were added.

2021-06-12-18-02-11
- XanPro Commit Test

2021-06-12-15-47-52
- Added \xan\microsecsTracker class for millisecond level time tracking of code and loops.

2021-06-10-16-22-27
- Added a Constant TWOFACTORAUTH_ENABLED to enable or disable 2FA.
- Added getEleMetaRender ELE_AS_STRING.
- Added User table columns for '2FA via Phone' and '2FA via Email' to allow options for receiving the code.
- Updated the Password Meter to check for Password Length and spread out the Levels ( Weak, Moderate, Strong ).
- Register and Change Passwords now require a Strong password based on the Password Meter.

2021-06-08-16-21-56
- Removed setting $_SESSION[ SESS_USER ] from init.php Session was not started yet. It's set in mmUsersT->doLogin.
- Moved setting $_SESSION[ SESS_URL ] to aloe/framework/session.php.
- Added a mb-1 to the button classes, ELE_CLASS_BUTTON_BLUE, ELE_CLASS_BUTTON_BLUE, ELE_CLASS_BUTTON_GRAY, and ELE_CLASS_BUTTON_GRAY to add bit of vertical space.

2021-06-08-15-26-13
- Fixed eleTable->render to correctly set table thead and tbody.
- Renamed FontAwesome properties to FontIcon since we're using FontAwesome and Boostrap Icons.
- $_SESSION[ 'urlCurrent' ] is now $_SESSION[ SESS_URL ] to replace the string with a constant.

2021-06-06-16-20-23
- Updated Init, mmSettingsT, and Settings Card values to appear in similar order.
- Added Settings for Phone Number, Email Address, and Postal Address.

2021-06-05-16-30-10
- Added eleMeta->eleAlign that accepts left, right, center, justify which defaults to left.
- Added Utility Function arrayContainsString for searching arrays for a value.
- Added additional reqID properties 2, 3, 4, 5
- Added getListRow params $rowHaButton and $rowColNamesA for tables in List Cards.
- Added eleCard IDs to make Showing and Hiding Cards simple.
- Added eleSearchBarListDB->render optional properties for $inclColA, $inclColMod, and $inclColKeys.

2021-05-15-14-37-21
- Removed an unneeded call to fmREST.

2021-05-13-17-45-29
- Added Contacts Comms create SMS to go with call.

2021-05-13-17-12-47
- Fixed \xan\response->metaSet(). Removed an extra quote and closing bracket.

2021-05-13-17-01-49
- Updated Home to add more examples. Added a use of php date_default_timezone_get.

2021-05-13-16-39-14
- Added a clickable link to the 2FA SMS and Email messages that will open a new tab to complete the Login. Works similar to the Registration One Time Code.

2021-05-13-15-34-17
- Added setting the default timezone to UTC in init.php.
- Added a function for arrayValuesWrapWith and arrayValuesWrapWithBackticks. Using to wrapping Column Names with backticks. Moved array functions higher within functions_utility.php.
- Updated sqlUpsert to use arrayValuesWrapWithBackticks. Goal is to wrap all SQL Statement Column Names with backticks everywhere possible.

2021-05-13-14-38-07
- Renamed /sql/ files from sequential numbers to dates.
- Added /sql/xan-2021-05-13.sql to add columns for constants: APP_COUNTRY_CODE, TWITTER_SITE, TWITTER_AUTHOR.
- Changed ALTER TABLE commands to use AFTER to keep table column order.
- Changed init.php to use the database values for APP_COUNTRY_CODE, TWITTER_SITE, TWITTER_AUTHOR.

2021-05-13-12-57-31
- Added constants: APP_COUNTRY_CODE, APP_LOCALE, TWITTER_SITE, TWITTER_AUTHOR. Need to add to the Settings Database Record.
- Added properties to \xan\response to support optionally adding html meta tags via \xan\respone->metaSet();
- Added \xan\respone->metaSet(); to several pages.

2021-05-11-15-09-05
- Updated Register Password Rating as a function in xan.js xanPasswordRating.
- Added User Change Password Rating using xan.js xanPasswordRating.

2021-05-11-14-10-04
- Added a simple Password Rating of Weak in red, Moderate in yellow, Strong in green.

2021-05-11-12-51-44
- Added a function sqlUpsert that creates a sql statement that will INSERT / ON DUPLICATE KEY UPDATE that will either Insert a record or Update a record if it already exists.
- Renamed a few functions to: sqlInsertQuestions, sqlLikeWhere, sqlLikeBindNames, sqlLikeBindValues, dbQueryBuilder_DataType, dbQueryBuilder_FindFilter, and dbQueryOrderBy_DropdownItem.

2021-05-10-12-18-05
- Fixed an issue with quotes when displaying font icons during ajax calls.

2021-05-06-17-52-02
- Added Bootstrap Icons.
- Replaced iconFA function with fontIcon. Adds a tags parameter. Works with both Bootstrap Icons and FontAwesome.
- Planning to remove FontAwesome when to Bootstrap Icons collection is larger.
- Replaced all FontAwesome html with the equivalent fontIcon function.
- Ranamed all "FA_" icon constant names to "FI_".
- Removed eleCard->renderListItemLink as it's now redundant.

2021-05-04-16-46-46
- Commented out XanDo javascript alert.
- Touched images and index.php.

2021-05-04-15-48-16
- Summary: Simplifying List Cards while adding options: Items Text, Items Image + Text, or a Table Row.
- Removed three functions from moduleMeta class and each subclass. Replaced with sharable moduleMeta functions.
- Added eleMeta property eleWidthTable that defaults to empty string but can be overridden per Table Column Name.
- Added two new moduleMeta getList functions: getListItem is for text, getListItemWImage is for an image + text, and getListRow is for html tables at full page width with a default column width.
- Updated content-cards.php Lists for Contacts, Contact Picker ( image + text ), Settings-Users ( text ), and APIRequests ( html table ). It's now easy to change how Lists are displayed.

2021-05-01-18-08-00
- Added a link to the ChangeLog in the ReadMe.

2021-05-01-17-58-33
- Updated APIRequests getListItemRowHeader and getListItemRow functions to a single function getListRow as an option to getListItem.
- Updated APIRequests List Card Styles from mini/wide to items/rows.
- Updated APIRequests List Card Styles to also set the Card Width.

2021-05-01-17-06-03
- Updated APIRequests to have an option to have Mini or Wide List.

2021-05-01-16-58-12
- Updated APIRequests 100% Wide List Table to use Column Labels rather than Column Names.

2021-05-01-16-29-11
- Fixed usages of NameModule, NamePlural, and NameSingular.

2021-05-01-16-04-10
- Added, for Admins, a APIRequests Module with a 100% Wide List Table and Sticky Header Row. Left most Column has a Button with the Row Index to view Details in Cards below the list.

2021-05-01-15-06-37
- Removed AutoLogout HTML Meta Refresh tag and replaced with a Javascript function that can push the Logout time out after AJAX calls.

2021-04-29-16-33-46
- Updated Stats Sessions to first look in ini_get( 'session.save_path' ) and then /tmp/. If no sessions found, now shows "$sessionsPath: /var/lib/php/sessions/ does not seem to be accessible."
- Changed the Stats Card order to show Sessions above Process Pools.

2021-04-29-15-31-29
- Added Stats Versions for OS, PHP, and wkHTMLtoPDF. Added section dividers.
- Fixed Processes values that were off by one row.

2021-04-29-14-36-51
- Updated references to GET and POST parameters for ID within comments.
- Fixed the missing $ for 'mmUsersT->nameSingular'.

2021-04-29-13-54-22
- Updated references to GET and POST parameters for ID to use metaModule property NameTable.
- Fixed case on api-process-queued Semaphore Error Messages.

2021-04-28-20-11-42
- Added functions-utility.php function paramDecodeQuotes to decode just quotes.
- Update eleSearchBarListDB to remove an extra parameter.
- Fixed eleSearchBarListDB Simple Query and Query Builder as both stopped working.
- Fixed eleSearchBarListDB so Table Keys and Mod Columns would not appear in Query Builder.
- Added metaModule property NameTable used for GET and POST params.
- Updated mmCheckout.php as it was missed.

2021-04-27-13-01-06
- Updated page-resp.php to make UTF-8 be capitalized.
- Update API calls to follow redirects.

2021-04-25-16-16-44
- Added API Handling. Can process immediately or queue!

2021-04-22-17-08-26
- Added a xanDo javascript alert function.
- Touched images, index.php, loading.php, and router.php for OCD reasons.

2021-04-22-17-02-04
- Updated Home Location button to use backticks for Javascript quotes. Will be using backticks more!

2021-04-22-15-42-07
- Added example code for hourofDay function.
- Added /sql/xan-2021-03-02.sql which creates the starting tables and sample data.
- Added /sql/xan-2021-04-21.sql which adds Settings columns AppLangCode = 'en' and AppTimezoneID = 'America/New_York'.
- Added in init.php constants for AppLangCode and AppTimezoneID to be loaded from Settings.

2021-04-22-14-21-34
- Added hourOfDayFunction( $timezoneID ) function. Used to prevent or permit running code at specified hours.

2021-04-20-18-52-51
- Renamed Array Variable to fix naming standard.

2021-04-20-18-44-47
- Removed all references to Tenant Table, Primary Keys, and SQL Statements.

2021-04-20-15-29-03
- Added function strAsciiSum used for PHP Semaphores.

2021-04-13-12-07-24
- Fixed the Stripe include after inserting the incorrect script.
- Fixed formatting of PHP Auto Logout Meta tag, PHP XSS Header, and PHP Stripe script include.

2021-04-12-18-20-41
- Updated Stripe to include its javascript on request rather than all the time.

2021-04-12-15-08-40
- Updated the init file loader to use HTTP_HOST instead of SERVER_NAME to load 'init_DOMAIN.php'.
- Updated the init file loader to use __DIR__ instead of dirname( __FILE__ ). Both are equivalant.
- Updated upload.php to use permissions 775 instead of 777 when creating directories.

2021-04-11-16-41-05
- Moved the directories logs|brief|bucket to files/DOMAIN/logs|brief|bucket to separate between instances.
- Updated Bucket Upload to use the new folder structure.

2021-04-10-17-15-30
- Updated XSS to use a Header rather than a Meta tag as Headers work with 'frame-ancestors'.
- Updated the database settings from a hardcoded 'init_private.php' to look for a file based on the domain name like 'init_xanadu.xanweb.app.php'. A basic text 404 message is shown if the domain doesn't match an existing file.

2021-04-07-10-24-21
- Updated Darkly css to comment out Google Font 'Lato' to prevent XSS notfications when Google Fonts is not approved. Darkly is for Dark Mode and from https://bootswatch.com

2021-04-06-17-35-18
- Update Reload and XSS formatting.

2021-04-06-13-08-08
- Disabled Google Fonts from XSS after news from the EFF: https://twitter.com/EFF/status/1378813625960427521
- Updated the Session Updated and Expires timestamps comment.

2021-04-06-12-40-26
- Disabled Google Fonts after news from the EFF: https://twitter.com/EFF/status/1378813625960427521

2021-04-01-16-45-40
- Updated XSS Content-Security-Policy frame-ancestors to none.
- Updated the mobile / narrow window hamburger menu to appear correctly appear in light and dark mode.
- Updated xanLocationGet err.code = 2 message to help Mac Safari users enable Locations Services permissions.

2021-03-31-16-50-10
- Updated xanDo and xanDoSave so xanMessage to show an icon immediately and when done, a success or error messages is shown. On success, the icon and message fades out. Now uses a table for formatting.
- Added sendSMSDebug function and constant for APP_SMS_TO_DEBUG. Moved the debug constants to init_private.php. Needed this to find a pesky error.
- Added Logging PHP errors to a file in the logs folder.
- Error fixed. Icon constants FA_SORT_ASC and FA_SORT_DESC were missing.
- Added Session values for Path and Info in router.php.

2021-03-29-18-23-26
- Contacts: Fixed Table Row incrementer.
- Contacts: Fixed missing ": " in NameUpdate.
- Encoded the $aloe_request->path_get() and $aloe_request->path_components_get().
- Updated xanMessage for xanDo and xanDoSave with larger icons and fix spacing in the javascript console.
- Updated Users nameUpdate to use NameFull.

2021-03-29-17-14-52
- Replaced $rowIndex++ with ++$rowIndex to increment inline.

2021-03-29-16-58-56
- Added a preceding backslash before all usages of xan.

2021-03-29-16-51-17
- Moved xan.js from /include to /xan.

2021-03-29-16-28-15
- Replaced usages of $_POST with $aloe_request->post.
- Replaced usages of \xan\valuePOST with \xan\paramEncode.
- Removed the functions \xan\valuePOST and \xan\valueGET.

2021-03-29-12-40-45
- Updated paramEncode to accept a value or an array.
- Fixed XSS Error regarding frame-ancestors by adding the site url.
