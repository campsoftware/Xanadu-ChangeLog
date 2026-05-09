# Xanadu 

**Xanadu is a framework for developing Database Driven Web Apps.** 

Xanadu uses PHP, MySQL, HTML, Bootstrap, CSS, and Javascript with several amazing includes.

We've been developing Database Apps for decades with FileMaker and Xojo. FileMaker rocks but licensing became too expensive. Xojo has fantastic pricing, but is perpetually buggy. We had to find an alternative platform. PHP kept coming up in our searches. Long story short, we decided PHP is the best option just to get back to an affordable and solid platform.

Read more about Xanadu: https://campsoftware.com/products/xanadu.php

# Xanadu Pro Change Log

**In Progress**
- Sales add ProjectsTasks to SalesItems.
- Convert from PHP 8.3 to PHP 8.5:
  - **Find**: \Pdo::MYSQL_ATTR_FOUND_ROWS **Replace**: \Pdo\Mysql::ATTR_FOUND_ROWS

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, NOTE ]

**Change Log**

2026-05-09-15-17-47
- Fixed MEDIUM-002: String Concatenation in Loops in mysqlTools.php
- Rewrote tablesBackup() function to use streaming file writes instead of accumulating $sql string
- Open file handle once at start, write directly for constant memory usage regardless of table size
- Replace inner-loop $sql .= concatenation with array-based value collection + implode per batch
- Key changes:
    * fwrite($fp, ...) instead of $sql .= ... + fileAppend()
    * $values[] = ... then implode(',', $values) per row
    * $rowLines[] = ... then write batch with proper terminators
    * fclose($fp) on success or exception
- Maintains: table filtering, batching, gzip support, error handling, all existing functionality
- Eliminates O(n²) string reallocations that degraded performance under memory pressure
- All 76 tests passing (74 PHPUnit + 2 E2E)

2026-05-09-15-00-52
- Fixed Synchronous Logging to Database on Every Request
- Changed router.php to use logEventToFile instead of logEventToSQL for zero DB latency on requests
- Added logMemoryToFile and logMemoryToSQL functions to functions-files-paths.php for flexible memory logging
- Updated peakMemoryUsageLog in functions-environment.php to use logMemoryToFile instead of direct SQL INSERT
- Both Event and Memory logs now write to daily files (YYYYMMD_Event.txt, YYYYMMD_Memory.txt) for batch processing
- SQL alternatives available (logEventToSQL, logMemoryToSQL) for future switching if needed
- All 76 tests passing (74 PHPUnit + 2 E2E)

2026-05-09-14-44-37
- Fixed HIGH-002: File Operations Without Caching on Every Request
- Added RouterFileExists to modulesD in xan.php modulesLoad() to pre-check router file existence once during module loading
- Updated router.php to use \xan\xan::$modulesD[ $component1Base ][ 'RouterFileExists' ] for zero disk hits on every request
- Removed unused fileExistsCacheD property and fileExistsCached method from xan.php
- All 76 tests passing (74 PHPUnit + 2 E2E)

2026-05-09-14-18-12
- Fixed JS minification escaping: Added str_replace() in init.php to escape double quotes in PHP constant values before minification, preventing syntax errors in minified xan.js.
- Fixed duplicate source.onmessage: Removed duplicate EventSource listener in xan.js.js xanDoProgressContinue function.
- Fixed HIGH-001 N+1 Query: Replaced SELECT-check-loop with INSERT-first collision retry (50 attempts) in linkShortener.php.
- Fixed PHP 8.4 deprecation: Changed implicit nullable params to explicit nullable (?array) in requestSanitize() function.
- Fixed functions-helpers.php: Replaced undefined isEqual() and strContains() with native PHP equivalents (===, str_contains).
- Renamed doGit.sh to doCommit.sh for clarity; updated to manage timestamped commit message files.
- Moved doTestsLog files and doCommitMessage files to new timestamps for history tracking.

2026-05-06-15-09-43
- Updated README.md with project documentation changes.
- Moved PWA test files from xanApp/pwa/ to xanApp/tools/pwa/ for better organization.
- Moved siteAddRedirect.php from xanApp/ to xanApp/tools/ to consolidate utility scripts.
- Created doGitCommitMessage-2026-05-06-13-31-32.txt with previous commit messages for archival.
- Updated doGitCommitMessage-next.txt with current pending changes.

2026-05-06-13-28-37
- Moved tests/ directory from xanApp/tests/ to project root for security (outside web public root).
- Relocated Playwright config and node_modules to tests/ directory with isolated package.json.
- Updated .gitignore with tests/node_modules/, tests/test-results/, tests/playwright-report/, tests/playwright/.cache/ exclusions.
- Added Playwright E2E tests: tests/e2e/contacts-print.spec.js with login and PDF generation flows.
- Added Playwright documentation: tests/docs/PLAYWRIGHT_TESTING.md with setup and troubleshooting guide.
- Fixed isEmpty() in xanApp/xan/functions-dataMassage.php to properly return true for empty arrays.
- Reformatted xanApp/xan/xan.js.js with consistent code style (double quotes, arrow functions, spacing).
- Changed session.cookie_samesite from 'Strict' to 'Lax' in xanApp/init.php for OAuth compatibility.
- Removed package.xml (Xdebug PECL metadata - not part of project).
- Removed old test-results/ from project root.
- Updated doTests.sh to run from tests/ directory and generate comprehensive markdown logs.
- Updated doGit.sh to manage timestamped commit message files with 3-file retention policy.
- Created timestamped commit message files: doGitCommitMessage-2026-05-05-14-42-30.txt and doGitCommitMessage-2026-05-05-15-21-00.txt.
- Renamed doTestsLog files with new timestamps for test run history tracking.

2026-05-05-14-35-00
- Fixed CRITICAL-001: Removed phpinfo.php, phpinfo_xan.php, phpinfo_xdebug.php, phpstorm_debug.php, phpstorm_debug_validator.phar, phpstorm_index.php from production to prevent information disclosure.
- Fixed CRITICAL-002: Applied htmlspecialchars() escaping to url output in xanApp/app/LinksMT/router-api.php line 11 to prevent reflected XSS in link shortener router.
- Fixed CRITICAL-003: XSS in Link Shortener JavaScript already secured via DOM construction with jQuery text() method in xan/linkShortener.php renderModal().
- Fixed HIGH-002: SQL Injection in dbCompare already fixed with prepared statements and identifier sanitization via sanitizeIdentifier closure in xanApp/app/Xan_LabsM/contentCard-dbCompare.php.
- Fixed HIGH-003: Added ini_set('session.cookie_samesite', 'Strict') to xanApp/init.php line 129 to prevent CSRF via cross-site cookie requests.
- Fixed HIGH-004: API Key Logging Exposure - requestSanitize() function exists in xanApp/xan/functions-helpers.php to redact sensitive keys before logging.
- Fixed MEDIUM-001: Created jsonDecodeSafe() helper function in xanApp/xan/functions-helpers.php with JSON error handling and safe defaults.
- Fixed MEDIUM-001: Applied jsonDecodeSafe() to xanApp/app/UsersMT/do.php, xanApp/app/UsersMT/logins/login/do.php, xanApp/app/UsersMT/logins/register/do.php, xanApp/app/UsersMT/logins/passwordreset/do.php to prevent JSON decode errors from crashing authentication.
- Fixed LOW-001: Changed ini_set('html_errors', 1) to ini_set('html_errors', 0) in xanApp/init.php line 138 for defense-in-depth error handling.
- Fixed LOW-002: Added regex-based API key extraction and validation against CRON_API_KEY constant in xanApp/xan/constants-index.php requestReject() function to prevent substring matching attacks.
- Updated xanApp/doTests.sh to automatically delete old doTestsLog files keeping only most recent for cleaner file management.

2026-05-05-11-43-54
- Added @see and @covers annotations to enable IDE test navigation and code coverage tracking.
- Updated xanApp/xan/functions-dataMassage.php with test annotations for isEmpty, isNotEmpty, strExplode, arrayImplode, arrayValuesWrapWithBackticks, arrayCount, arrayKeyExists, arrayInsert, strSubstitute, strLength, strFilter functions, strCaseUpper, cssSizeFactor, arrayValueFound, arrayFilterInteger, paramEncode, paramDecode, and paramDecodeQuotes.
- Updated xanApp/xan/functions-files-paths.php with test annotations for pathExists, pathGetFileNameFull, pathGetFileNameNoExtension, pathGetExtension, pathGetPath, and fileMimeTypeFromFileName.
- Updated xanApp/xan/inflector.php with test annotations for pluralize, singularize, camelize, underscore, dasherize, humanize, delimit, tableize, classify, and variable methods.
- Updated xanApp/xan/constants-index.php with test annotation for requestReject function.
- Updated xanApp/tests/Unit/Xan/FunctionsDataMassageTest.php with adjusted test configuration.
- Updated xanApp/tests/phpunit.xml for PHPUnit coverage settings.
- Updated xanApp/xan/constants-arrays.php with related adjustments.
- Added doTestsLog files for test run history tracking.
- Updated doTests.sh with test runner improvements.

2026-05-04-16-14-55
- Added more unit tests. Can call doTests.sh to run them.

2026-05-04-13-47-48
- Added xanApp/tests/ with basic test structure.

2026-05-04-12-13-21
- Updated doGit.sh to create a backup zip of the project after pushing to main.

2026-05-04-12-07-51
- Updated doGit.sh to create a backup zip of the project after pushing to main.

2026-05-04-12-04-38
- Updated doGit.sh to create a backup zip of the project after pushing to main.

2026-05-03-10-12-46
- Fixed print.php printing to a Word file.
- Fixed some security issues.

2026-04-28-12-39-41
- Massive number of updateds since last. Been working to clean code and fix security issues. Added Contacts 5160 Label printing.

2026-03-16-11-27-58
- Zipped and Removed Modules Tickets and TicketsMessages that were generated with Khan to begin work on Khan AI.
- Updated xan.php function modulesUpdate to set the Modules RelatedTables column.

2026-03-15-15-36-27
- Updated ProjectsTasks cardPortal Card Width.
- Disabled Settings cardRecordOther NumPurchaseNext for now.
- Disabled Stats wkHTMLtoPDF current version number as we now use mPDF.
- Added two Xan gifs.

2026-03-07-15-17-35
- Updated GitHub commit shell script doDevGit.sh.

2026-03-07-14-46-54
- Reformatting Changes

2026-03-05-14-18-03
- Added functionality for PDF form handling, including retrieving and setting PDF form fields in `pdfMan.php`.  
- Integrated new PDF form field feature into the Xan Labs module with a UI button and sample implementation.  
- Refactored and renamed PDF-related methods for clarity: `pagesTextFind` → `getTextFindPageNums`, `pagesTextExtract` → `getPageText`, and `cardRecordApplication` → `cardRecordForm`.  
- Minor cleanup in `ContactsMT` and `HomeM` modules for better maintainability.  
- Added test files `pdfTestForm.pdf` and `pdfTestFormSet.pdf` to validate PDF form functionality.

2026-03-04-12-59-18
- Fixed xan.js.js xanMessageDisplay issue where the completed message was not being removed.

2026-03-03-15-21-09
- Fixed CommsMT->cardPortal function buttons for Email, Text, Call, View Web Page.
- Fixed ContactsMT, ProductsMT, SettingsCompaniesMT, UsersMT Image Buckets.
- Update get.php to add TAGS_CELL_RTBUCKET for displaying the Label and Buttons with the correct padding.
- Fixed All the do-print.php files to use xanDoProgress.
- Fixed AuditLog Modal issue showing the HTML Table.
- Updated eleModal.php to resize to see the AuditLog Progress and also addded a Progress Mirror.
- Added xan.js.js function xanMessageMirrorInit.
- Updated page-resp.php to add xanMessageMirrorInit function.
- Updated codeContentAndScripts function to clear the code arrays.
- Fixed module.php recCol_BucketButtons function setting $eleIDSelector.

2026-02-19-15-03-52
- Added dev-hal_merge.sh to automate merging dev-hal into main.

2025-12-28-17-16-30
- Added xanConsole_GoApp and xanDesktop_GoApp.
- Added watch.php for the xanConsole and xanDesktop Watch Folder apps.
- Added XanLabs contactCard-SQLitePostal.php to Query https://xanweb.app/xanAddresses.php.
- Updated init.php flow and added PATH_ROOT_WATCH and URL_ROOT_WATCH.
- Updated recsPDO.php to use its own property vs a global.
- Updated function pathCreateRecursive to use PERMISSIONS_ constants and to apply chown and chgrp.

2025-12-14-19-23-22
- Updated xan.php Schema Update to create indexes for Columns beginning with UUID. Automatically changes to varchar(50) if not already varchar.
- Added recs.php comment: TODO Add if it makes sense: PDO::ATTR_PERSISTENT => true
- Added openAIAPI.php function estimateCostUsd.
- Refactored XanLabs display and organization to not repeat titles, icons, etc.
- Moved Home Cards for Weather, Chart, AI English to SQL Query, Tabs, Bsky Purge.
- Added Settings for Bsky Handle, App Password, and Server.

2025-12-09-16-58-19
- Planning to update from PHP 8.3 to PHP 8.5. Added to In Progress a PHP 8.5 Find/Replace.
- Fixed PHP 8.5 issues and many items from PHPStorm Problems also using PHPStorm Problem Suppression on a File, Function, and Statement Level.

2025-12-04-10-57-42
- Updated \xan\xanDoProgressLoop to support loop levels.
- Updated \xan\printer to use \xan\xanDoProgressLoop.
- Added \xan\pdfMan to manage PDF utilities for manipulating PDFs.
- Updated \xan\filenameClean \xan\filePathDeleteOlder and \xan\filePathCreate_Working.
- Updated /xan/openAI/englishToMySQL_instructions.txt for MySQL 8.
- Updated LoadingM for \xan\xanDoProgressLoop.
- Updated HomeM creating cardWeather, cardChart, cardAI, cardTabs, cardBSDelete as their own cards.

2025-11-15-15-46-43
- Added xan.css.css styles for ".xanBadgeNotSet" and ".xanBadgeNotSet .xanBadge".
- Updated \xan\recs->colValue and colvalueFormatted to optionally apply htmlspecialchars function.
- Added functions-helpers.php function sqlWherePermutations and sqlDebugIBindValuesA.
- Updated functions-files-paths.php function fileNameClean to replace newline, return, and tab.
- Updated eleValuesBadges.php and eleValuesBadgesDB.php formatting.
- Added ContactsMT function contactNameLine( \xan\recs $recs, $line ) and updated the other Name functions to use it.

2025-11-05-12-30-05
- Updated Contacts to have both a CustNum and CustInteger.
- Updated SettingsCompanies to add a NumSaleNext column to work with the function SettingsCompanies->numContactGet.

2025-11-04-17-19-15
- Updated recs.php recordUpdate, recordDuplicate, recordDuplicateRelated to only set normal columns, not Generated Columns.
- Updated page-resp.php to merge Schema Update with Triggers Update. 
- Updated do-schema-update.php to run Triggers and Generated Columns, Modules update, then Schema update.
- Removed do-triggers-update.php.
- Removed SettingsMT/do.php TriggersUpdate.
- Added functions-helpers.php sqlUpdateColNameQuestions function.
- Updated functions-dataMassage.php isEmpty and isNotEmpty to handle empty date 0000-00-00 and empty timestamp 0000-00-00 00:00:00.
- Added SettingsCompanies function numContactGet that returns and increments the next Contact Integer ID.
- Added ContactsMT/class.php to set Cust Integer if empty or 0.
- Added ContactsMT/class.php to set Cust Num if empty.

2025-10-30-14-10-10
- Updated ContactsMT->formOverlayW9 with a Watermark.

2025-10-29-12-04-18
- Added xan.js.js and response.php functions for jsRenameID.
- Added module.php function recCol_Input_InsertIf for Insertable Inputs.
- Updated functions-helpers.php formOverlayEle functions.
- Added functions-dataMassage.php valueItem_Like function.
- Updated doSave.php for Insertable Inputs
- Updated modules Contacts and Addresses.

2025-10-20-12-41-25
- Added /templates/form-default style.css back. It's inert unless used.
- Updated module->cardActionsDetail function to use the template pdf-default.
- Renamed template html-default to form-default.
- Updated functions-helpers.php, adding backticks on more tables and column references.
- Renamed formOverlayAssociationApplication to formOverlayW9.
  
2025-10-19-14-09-59
- Added PDF Forms with Editing and Printing using W-9 as an Example.
- Added templates/html-default.
- Added functions-helpers.php functions for formOverlays.
- Updated printer.php. Cleanup and Empty Array Checking.
- Updated module->cardActionsDetail using $actionsABegin and $actionsAEnd.
- Fixed module instances usage of $cardHeaderContentRight to be consistent.

2025-10-14-15-38-54
- Added module LoadingM to replace loading.php.
- Added URL_ROOT_BOX to URL_ROOT_FILES for files like PDFs, not in the database URL_ROOT_BUCKET.
- Fixed a bug in xanDoProgressContinue when trying to set spinnerTitle when staying in the same window.
- Updated ContactMT/do-print.php to use Limits and Offsets to save memory. mPDF conversions are slower than expected.

2025-10-12-16-06-43
- Updated xanDoProgress New Window option to flow better for the user. Before it was click, run function and optionally open a new window. Now it is click, run function and optionally open a new window, THEN run the functionContinue in the new window. Now when opening the new window, progress can be shown.
- Updated xanDoProgress Loading, now uses the module LoadingM instead of loading.php. This keeps the interface similar except for the larger progress bar info.
- Added new response->jsPageURLSetNewWindow.
- Fixed Readonly Elements by using a class .xanControlReadOnly as using the readonly tag also include flatpickr and select pickers.
- Updated ContactMT/do-print.php to use xanDoProgress.
- Added a Bluesky API example. Need to move to Xan Labs.
- Added ContactMT->contactName* functions option to pass either the first or second part of the name.

2025-10-06-14-18-57
- Uppdate eleMeta. Added properties and moved eleMeta functions to functions-helpers.php.

2025-10-02-14-02-44
- Updated /xan/xan.css.css styles for mark.
- Updated /templates/pdf-default/style.css for more styles.
- Updated mPDF from 8.2.0.0 to 8.2.6.0.
- Updated functions-helpers.php->colValueType() to use \xan\xan::$schemaD[ $tableName ][ $columnName ][ DBS_DATATYPESIMPLE ].

2025-09-28-14-00-36
- Updated functions-helpers.php colValueType() to now return the DBS_DATATYPESIMPLE instead of DBS_DATATYPE.

2025-09-28-12-00-45
- Removed module->$this->tableSelectAsAppend() from the List Query becuase AS columns cannot be queried.

2025-09-27-16-32-27
- Updated content-page.php for Modules to append $mmTable->tableSelectAsAppend() to Detail Queries.

2025-09-27-16-20-55
- Updated xan.php and eleMeta Schema to add isNullable, isGenerated, $extra, $defaultValue, and  $comment.
- Updated module.php:
    - Added a new abstract function tableSelectAsAppend to append calcs in the form of AS.
    - Added automatic readonly if $eleMeta->isDefined === 'AS' || $eleMeta->isGenerated === 'Yes'.
    - Updated function cardListCard query to append $this->tableSelectAsAppend();
- Added function tableSelectAsAppend to each module.

2025-09-25-14-47-58
- Updated DB_SERVERNAME from the direct server to db.xanweb.app.
- Updated SQL calls with FROM tableName WHERE to wrap the tableName in backticks. 

2025-09-20-17-35-24
- Added functions-helpers.php function eleButtonViewRender for loading MySQL Views as a Search.
- Updated content-page.php to handle when $resp->reqID === 'view'.

2025-09-18-10-53-39
- Updated router.php to support Module Views.
- Added Home Buttons for Contacts Active and Contact Not Active.

2025-09-17-13-51-12
- Updated module.php to support using MySQL Views as an alternative to All Records.
- Update HomeM eleTabs Example.
- Renamed ContactsMT contactName functions from contactNameDisplay to contactNameAsHTML. Added contactNameAsLine.

2025-09-15-15-25-37
- Updated eleTabs to use eleCards as a base with Tab Buttons in the Header and Tab Content in the Body.
- Updated strLoremIpsum to be able to generate more than 69 words.

2025-09-14-16-44-25
- Updated eleCard and eleTabs to default to auto overflow, resizeable, and an Expand Button.
- Started process of moving cardExpandButton from \xan\modules to \xan\element.
- Updated calls to eleCard and eleTabs to remove the params for overflow, resizeable, and an Expand Button. Added param to pass \xan\response for the js needed for the Expand Button.

2025-09-13-17-57-34
- Added xan.css.css settings for Card Header, Tabs Active, Tabs, Inactive, Tabs Disabled.
- Renamed strSubstituteValuePairsD to strSubstitutePairsD.
- Renamed eleCheckboxGroupDB to eleValuesBadgesDB.
- Added eleTabs.php for a Tabs Element.
- Added on Home, cardTabs Example.

2025-09-12-12-56-33
- Added functions-internet.php function urlProtocolCheck to make sure https:// or others is included.
- Added functions-dataMassage.php function strStripTagsAndSubPairs to, by default, sub HTM_BR to ' / ' and then remove tags.
- Updated calls to set $resp->headMetaTitle to use \xan\strStripTagsAndSubPairs.
- Updated Comms Website Button to use /xan/urlProtocolCheck.

2025-09-11-13-47-32
- Updated constants-arrays.php to add an example for Choices Override using Comms Type = Phone/Email as and example.

2025-09-10-19-02-32
- Updated module.php recColRenderAs to handle Choices Overrides.
- Updated functions-helpers.php function eleLogAuditTable so TEXT columns are height constrained.
- Updated eleMeta.php function selectChoicesArray to simplify.

2025-09-09-13-07-20
- Renamed SQL Arrays from SQL_ to ARRAY_SQL_

2025-09-08-18-20-30
- Updated sql connections to use utf8m4 instead of utf8.
- Added new element DB type: eleCheckboxGroupDB.
- Updated xan.js.js: xanEleCheckboxGroupUpdate, xanEleMove, Queued xanDoSave.
- Updated Session.php session init to try and prevent unexpected logouts.
- Updated SQL functions to wrap col names in backticks with an override for *.
- Updated init.php to make it easier to see when files were last minified in the console.
- Updated Contacts Cards to xandev after syncing with another project.

2025-08-28-15-55-18
- Updated /blog. Almost done. Need to add Tags, Author, and Media Image.

2025-08-25-17-31-49
- Added /blog from https://github.com/Cristy94/markdown-blog. Is based on htaccess. Need to add router entries for the List: /blog/, Posts: /blog/foo-thing, and /blog/rss.xml.

2025-08-24-16-30-19
- Renamed date, datetime, and time now functions.
- Updated recsPDO.php to have colValue, colValueSet, and recordInsert.
- Added FMDump Migrator to XanLabs.

2025-08-20-14-24-37
- Added functions strFilterURLComponent and strRandomNoun.
- Added /xan/data-nouns-2315.txt for generating passwords.
- Added xanLabs User Bulk Password Set.
- Updated xanLabs Page Buttons organization.

2025-08-11-15-17-00
- Updated openAIAPI.php which now can create SQL Queries from English! Tried passing Instructions and Schema as files, but as one big question worked better.
- Added English to SQL test on Home.

2025-08-09-12-40-22
- Updated Sales ProjectsTasks Portal.
- Added openAIAPI.php for AI queries.

2025-08-07-11-29-27
- Updated module.php to optionally hide Picker Images. Needed this for Projects Tasks Portal.
- Added to Projects a function ProjectsTasksSetUser to apply the Project User to ProjectTasks.
- Updated Sales with a Projects Tasks Portal. Need to finish.

2025-08-06-13-54-06
- Updated Users Picker to no longer include Active.
- Updated Users Pickers to all now show as Brief.
- Updated ProjectsTasks Portal to fit the UUIDUsers Picker.

2025-08-05-18-36-36
- Updated xan.js.js function xanDoJS case 'jsHTMLSet' to rehydrate script tags.
- Fixed Bug where Pickers would not set in a Portal. Item above fixed it.

2025-08-05-15-36-47
- Updated ProjectsTasks to included a User Picker. Need to finish.
- Found a bug that is repeating Portal Pickers repeating its contents.

2025-08-04-17-24-18
- Updated Contacts and Sales Column Payment Terms to be a Select that uses the ARRAY_PAYMENTS_TERMS array.

2025-08-04-16-42-18
- Removed Payments.DateReceived from Code and SQL.
- Updated Payments and Disbursements.

2025-08-03-17-47-51
- Updated do-portal-payment-paymentDisburse.php to use JS to update the loaded page.
- Added PaymentsMT content-page.php Disbursements Portal.
- Removed DisbursementsMT content-page.php Disbursements Portal.
- Updated all but ContactsMT that had a default Active  or Pinned colValueSet.

2025-08-03-14-46-26
- Added xan.php function schemaExportAI which runs at the end of the function schemaUpdate. It exports a text file with Tables and Column info to xanApp/xan/xan-schema-ai.json.

2025-08-02-12-07-56
- Fixed DocumentMT->recMassage updating of file attributes.

2025-08-01-14-42-21
- Updated constants-index.php function requestReject to log Request Rejections. Removed curl from Bots since we call php via urls.

2025-07-31-16-52-43
- Removed router.php Path Part Rejects.
- Fixed a bug in router.php where a wrong var was used.
- Updated Aloe/response.php use of functions to be native instead of from Xanadu to load less until the request is accepted aka not rejected.
- Updated index.php to reject requests for common AIs and intrusions. Now loading xan/constants-index.php with minimal constants, loading Aloe, and then seeing if the request should be rejected.

2025-07-30-14-57-00
- Moved Printer pageContentCardFitterTEST to Xan Labs.
- Update Xan Labs button style and organization.

2025-07-29-13-54-05
- Added printer.php function pageContentCardFitterTEST to test pageContentCardFitter output. 
- Added functions-dataMassage.php function strLoremIpsum to generate random words that look like sentences.
- Added the pageContentCardFitterTEST on Home.

2025-07-28-14-24-37
- Added printer.php function pageContentCardFitter to help create mPDF cards that flow into a multicolumn table.

2025-07-27-15-34-10
- Added recs.php function recordDuplicate param for setting default values.
- Added printer.php functions for creating multi column pages that flow down. It uses mPDF->GetY before and after placing html. Proof of concept for now.
- Updated module.php function cardModalsNewDupDel to accept $colValues to update columns when calling New or Duplicate Record.
- Continued with Sales Payments.

2025-07-23-17-13-47
- Updated PaymentsMT Disburse Button and Modal.

2025-07-22-15-25-33
- Fixed xan.js.js xanDoJS jsAttrSet.
- Added xan.css.css selector for read only xanControl and form-control.
- Removed get.php css from TAGS_ELE_INPUT_READONLY.
- Updated uses of [$recs->rowsD[ $recs->rowIndex ][ $this->nameKey ] ?? ''] with [ $recs->keyValue() ].
- Updated do-portal-payment-paymentApprove.php to Approve Disbursements.

In Progress 
- Sales, Sales Items, Payments calcs.
- Projects Items, Project Tasks calcs.

2025-07-21-12-45-46
- Fixed a bug in recs.php function colValue that was setting $dataType to 'decimal'.

In Progress 
- SalesItemsMT->recMassage calcs.
- Sales Payments calcs.

2025-07-20-16-24-05
- Added recs.php function colIsSet that calls array_key_exists.
- Removed Traits from module.php.
- Removed \xan\UsersMT::inst()->sessionUserSet(). It performed a Query without using the result.
- Updated all module.php instances to check if the recs->colIsSet to make sure there is a $colName key.

In Progress 
- SalesItemsMT->recMassage calcs.
- Sales Payments calcs.

2025-07-19-15-34-58
- Added xan.php var $consoleLogA to store consoleLog message. page-resp.php sends the array items to the console.
- Updated recs.php function recordUpdate. Fixed a bug and refactored to no longer select the record at the end.
- Update page-resp.php function xanInit to update the generated DatePickr classes and styles from its source on page load and ajax.
- Updated module.php functions recNew, recDuplicate, and recDelete to handle returning a page load or a portal.
- Updated init.php cookie lifetimes and added last minified js and css timestamps.
- Removed eleDate, eleTime, eleDateTime functions renderScriptsInit now that xanInit.php handles it generically.
- Continued on Sales Payments.

2025-07-17-13-27-23
- Updated every \xan\module instance to clean up recsMassage to use $recs->colValue( $colName ) instead of $rowD.

2025-07-16-13-32-50
- Fixed \xan\module->recCol_BucketEle and \xan\module->recCol_BucketButtons as an extra # was added to IDs.
- Updated every \xan\module instance to clean up recsMassage, recColFormattingTags, and recSaveAfterJS.

2025-07-15-16-20-57
- Updated \xan\modules code order for all Modules and added function dividers.

2025-07-15-14-03-21
- Updated function \xan\arrayValueFound to accept a value or array.
- Updated \xan\modules code order and code styling for Sales and SalesItems.

2025-07-14-16-57-47
- Updated SalesItems to revert recColFormattingTags back to simply returning tags as needed.

2025-07-14-16-11-08
- Updated SalesItems to split recColFormattingTags into recColFormattingTags, recColFormattingColNameA, recColFormattingDo. This was done so recSaveAfterJS can auto format the columns with formatting.

2025-07-13-14-35-33
- Renamed function \xan\eleGetIDRecs and \xan\eleGetID to \xan\eleIDSelector.
- Updated Sales, SalesItems, Payments.
- Updated Router to try and detect logouts during ajax.

2025-07-11-17-19-40
- Updated Trigger Procedures to use Session Vars for consistency. 

2025-07-11-13-32-20
- Renamed Trigger Procedures to "triggerTableName".
- Renamed triggerSales param to pUUIDContacts.

2025-07-11-12-39-01
- Updated User and Xanadu icons.
- Updated SalesItems and ProjectsTasks 
- Removed moduleTriggerWait functions recColFormattingTags to commit immediately instead of waiting for the trigger. The stored procedure is now called, which checks to see if the stored totals match the unstored totals before updating.

2025-07-10-12-13-47
- Updated xan.js.js xanDoJS() functions to use pure JS instead of jQuery.

2025-07-09-16-03-07
- Updated Bootstrap to 5.3.7.
- Updated xan.js.js xanDoJS() jsCSSSet to handle !important.
- Added \xan\tags function valueWithTagsRespJS.
- Updated Sales TotalDue Color to red when >0 and green when <0.

2025-07-08-18-11-57
- Added xan.js.js jsClassSet and jsClassRemove.
- Renamed all xan.js.js jsSet* to js*Set.
- Changed /logout/*|* calls to use a hyphen instead of a pipe.
- Added \xan\tags function valueWithTagsRespJS.
- Updated \xan\recs->colValueFormatted to handle render on server and update with Javascript.
- Updated \xan\strAppend params to all be required and the order of the params are sequential.
- Updated doSave.php to use $recsTable->massageColsForGUI instead of duplicated code.

2025-07-03-11-02-39
- Added recs->colValueSet function.
- Added Special Instructions to Contacts which is then set on Sales.
- Added ARRAY_SALES_TAXSTATUS Constant array.
- Updated Sales, Contacts, Products calcs.

2025-06-28-14-49-11
- Updated calls to /logout/ with a reason component to help find the unexpected logout bug.

2025-06-27-15-41-51
- Updated tableTriggersInstall formatting to be cleaner and on SalesItems.
- Fixed an issue with eleMeta setting eleSelect Choices generated from SQL.
- Updated Sales, Products, and Vendors.
- Need to finish Sales Items recMassage and recSaveAfterJS.

2025-06-25-16-18-01
- Updated module do-print to have detail info 5px padding, but Projects and Sales are tighter.

2025-06-25-14-51-50
- Updated Sales module and print. Need to finish SalesItems.

2025-06-25-12-07-08
- Updated do-print.php pad5 to pad2.
- Updated do-print.php Sales and Products

2025-06-23-17-54-47
- Renamed Addresses Street1 to Street.
- Added /templates/pdf-default/style.css pad and width variants.
- Updated do-print.php divs to use width css classes.

2025-06-22-19-06-12
- Added /templates/pdf-default/style.css widths.
- Renamed strPostalAddressFormat to strAddressFormat. Updated to be a generic address concatenator.

2025-06-22-16-14-04
- Renamed Pounds to Weight with an assumed unit of measure in Products, Sales, and SalesItems.
- Added \xan\tags->valueWithTags.
- Added \xan\recs->colValueFormatted.
- Updated printer.php htmlToFile to remove uses of !important.
- Removed \xan\module->recCol_StringInlineMPDF in favor of \xan\tags->valueWithTags.
- Updated modules do-print.php files to use \xan\recs->colLabel and \xan\recs->colValueFormatted.

2025-06-21-16-35-08
- Updated do-print.php for CalendarEvents, Contacts, Documents, Products, and Vendors.
- Fixed bug in \xan\recs where recImage and recTitle functions. Requires either Recs or and ID.

2025-06-20-14-48-27
- Updated eleDateTimeDB, eleDateDB, and eleTimeDB to better place the Magic Dates Selector.
- Updated all module class.php files recImage and recTitle functions to return empty string on null $recs.

2025-06-19-15-38-10
- Updated CalendarEvents do-print.php.
- Updated CalendarEvents recMassage.

2025-06-19-14-26-45
- Updated xanModifiers to add metaKey.
- Updated xanGoURL to no longer open a new window on xanModifiers.altKey as it was overlapping with Mac access keys, control / alt.

2025-06-19-11-50-09
- Renamed /templates/pdf-default/style.css styles.
- Updated Contacts and Projects do-print.php.

2025-06-18-14-04-13
- Git test 2.

2025-06-18-14-02-48
- Git test.

2025-06-18-13-54-07
- Set up Local Git

2025-06-17-17-34-52
- Removed CHANGELOG in favor of README and splitting off README_Before_2025. Plan to create one file per year.

2025-06-17-16-57-14
- Removed Xanadu from GitHub. No longer using git until there's a reason.

2025-06-17-15-32-51
- Added to XanLabs a ChartJS example. Also refactored how examples are loaded.

2025-06-17-14-37-08
- Added a sample PWA app in /pwa/. Safari's limitations make it less useful.
- Fixed missing renaming of Modules and Recs attributes.
- Added an openWeatherMapAPI class with functions for both  City and GPS Coordinates.
- Added an openWeatherMapAPI Setting for the API Key.
- Added \xan\strCaseTitleSmart that ignored 'small' words.

2025-06-13-12-50-02
- Renamed moduleMini properties to start with a lowercase char.

  2025-06-12-16-26-28
- Added module->tablesRelatedParentA and module->tablesRelatedChildA.
- Renamed module properties to start with a lowercase char.

2025-06-12-14-02-51
- Moved to from CampSolutionsInc to campsoftware

2025-06-12-14-01-04
- Moved to from campsoftware to CampSolutionsInc

2025-06-12-12-27-30
- Updated recs->recordDelete to combine recordDeleteRelated.

2025-06-11-16-51-54
- Added anchors to calls to 'window.location.href = "/logout' to find where the unexcpected logouts occur.
- Renamed recSaveAfter to recSaveAfterJS to be clear about its purpose.
- Updated ProjectsTasks recSaveAfterJS Trigger check refactor added a function moduleTriggerWait.

2025-06-11-15-27-22
- Removed modules->recMassageDo in favor of running some empty functions instead.
- Removed modules rec Before/After Traits by commenting them out.

2025-06-11-11-56-08
- Renamed tons for consistency.

2025-06-10-17-59-36
- Updated functions files to organize functions.
- Renamed tons for consistency.

2025-06-09-16-41-21
- Updated Sales and Projects recTitle and recColFormattingTags.

2025-06-09-15-40-08
- Fixed a bug in recsPDO.php. Fixed by assuming values are strings unless is_numeric.

2025-06-09-14-54-04
- Added Schema DataTypeSimple to set nulls to the correct type defaulting to "" or 0. Works with MySQL COUNT, but does not work with SUM, AVG, MIN, MAX, GROUP_CONCAT, STDDEV, VARIANCE if no recs ard found. COUNT will equal zero, but the others will be null. Can use COALESCE( SUM( Amount ), 0 ) to not return a null.

2025-06-09-11-01-38
- Fixed an issue in module->recCol_Picker.
- Renamed functions-internet.php emailAddressIsValid to emailAddressIsNotValid.
- Added functions-internet.php emailAddressIsValid.
- Updated eleTable->render default width from 99% to 100%

2025-06-08-17-03-50
- Updated recs and recsPDO to set all null values to an empty string.
- Updated two functions files using AI Find Problems. Fixed a few issues.
- Updated functions-dataMassage.php params to accept "?dataType $var" and immediately replace a null "$var ??= ''"

2025-06-07-18-21-28
- Updated \xan\recs but commented out for now. Looking into dealing with unexpected NULLs.
- Updated ProjectsTasks->recMassage Titles formatted as "Hal Notes" to check for nulls in the exploded values. Added a check for a hyphen in \xan\strLeft( $taskDesc1, 1 ).

2025-06-07-14-44-53
- Removed window.logoutAutoDT and replaced with a local variable.
- Updated ProjectsTasks to process notes formatted as "Hal Notes".

2025-06-06-15-37-33
- Added calls to xanAutoLogoutCheck in xanDoSave and xanDo.

2025-06-06-14-48-07
- Updated xan.js.js to show its Minified Timestamp.
- Updated xanAutoLogoutCheck in page-resp.php and xan.js.js.
- Removed all router redundant calls to \aloe\session_init in favor of one call.

2025-06-05-15-41-34
- Updated do-print.php to pass a table instead of values.

2025-06-05-12-45-01
- Removed $addBottomBorder and $backgroundColor from the TAGS_CELL_* functions. Was used in one function.

2025-06-05-11-15-43
- Fixed a bug in xan.js.js xanDoSave.
- Updated pdf-default to share a style.css file.
- Updated do-print.php files to use the shared style.css file.
- Updated pdf-default to no longer use a default header, instead replacing "[[HEADER]]".
- Added a new element recCol_StringInlineMPDF that calls recCol_StringInline and removes all uses of "!important" which has issues in mPDF.
- Updated Projects do-print.php.

2025-05-31-15-49-46
- Updated ProjectsTasks recColFormattingTags.

2025-05-31-15-11-36
- Added function xanStrPatternCount to xan.js.js.
- Added resp->jsSelectorTriggerChange.
- Added xanDoSave option with default to only update the Saved Column.
- Fixed a bug in eleTable.php setting \xan\tags->extrasD.
- Change the function order in \xan\modules to group recColFormattingTags with recMassage and recSaveAfter with tableTriggersInstall.

2025-05-29-12-16-25
- Updated recCol Portal function parameters to be in the same general order as Non Portal functions.

2025-05-29-11-49-59
- Fixed a bug in xan.js.js to check for null on xanTimeTotal.
- Fixed a bug in eleTable.php that was putting out one "<>" for each record - 1.
- Updated Projects.

2025-05-27-16-18-25
- NOTE: Been tracking load time of Xanadu and was getting worried that it's taking around 1.5 sec to load the page in Safari. Chrome and Firefox both load in HALF the time.
- Updated doSave to display 4 decimials rather than 3.
- Updated Projects Module.

2025-05-25-13-01-05
- Replaced the longer Message Names.

2025-05-24-15-10-31
- Updated xan.js.js to now show the xanMessageDisplayQueue serially with a message count. This prevents the Queue from wrapping to multiple lines.

2025-05-23-17-47-01
- Updated xanDoSave to handle regular inputs and hidden/select inputs.
- Updated \xan\recs recordInsert and recordUpdate to be more efficent and correct.
- Updated init.php to set session clean up.
- Updated ProjectsTasks to by default set the Status to "Not Started" and SortOrder to count of existing recs + 1.

2025-05-22-14-28-18
- Added in page-resp.php, the AutoLogout code page-resp.php after taking it out recently.
- Added in init.php, PHP INI values for session.cookie_lifetime set to APP_COOKIE_SESSION_SECONDS [2 hours] and session.gc_maxlifetime set to APP_COOKIE_SESSION_SECONDS_MAX [12 hours]. This may fix the AutoLogout issue of random logouts.

2025-05-21-18-03-01
- Commiting Again

2025-05-21-18-03-01
- Updated the Selected Record Checkboxes titles. That caused a bug reading the xan.js function xanSelectionLoad_Checkboxes.
- Updated Icons for the Print Menu.
- Updated Icons for Actions Running Man to FI_ACTION_DB.
- Added IDs to List and Portal Checkboxes to reduce warnings in FireFox and Chrome. DatePickr still spawn warnings...
- Updated init.php Include URL and Path and NGINX to use a shared local "includes" folder.
- Updated \xan\modules->cardPortal Selection Checkboxes to set the ID.
- Fixed ProjectsTasks New Record from ProjectsItems New Item Button.
- Deleted from Comms Portal the Addresses code from when Comms and Addresses were split.

2025-05-19-13-11-08
- Fixed bug with List Selection Checkboxes clicks going to the record instead of ticking.

2025-05-19-10-45-11
- Updated page-resp.php to use JS Navigation Timing.
- Updated xan.js.js xanDoSave, xanDo, xanDoProgress, and xanDoResponse to include Browser and PHP timing like: BrowserTime [ServerTime].
- Moved setting $pageload_begin = \microtime( true ); from init.php to index.php and now setting a Response Header for "xanTimeTotal".

2025-05-17-17-57-45
- Updated \xan\module->recColRenderAs to encode the value as the first step rather than after tags are applied.
- Updated \xan\module->recColRenderAs and Updated \xan\module->recCol_StringInline to pass $subValuePairsD to run a substitute on the value and keeping its \xan\module->recColFormattingTags. An example is Active: Yes => Active, No => Inactive.
- Added \xan\strSubstituteValuePairsD. Can pass a string to substitute an array of value pairs.
- Modified \xan\eleLabel from span to div.
- Added constants QS and QD for Single Quotes and Double Quotes.
- Updated Contacts module to use the updated \xan\module->recCol_StringInline with $subValuePairsD.

2025-05-17-16-06-46
- Updated modules content-page.php to no longer show an error if a detail record does not exist.

2025-05-17-14-45-33
- Fixed a bug with UUIDContactsTagsJoin where they keyname in the database had Join captialized.
- Removed an unused parameter on \xan\module->recCol_Picker_Content.

2025-05-16-14-56-24
- Fixed a bug in eleDate, eleDateTime, and eleTime where the selectors were using a class, not an ID.

2025-05-16-12-20-42
- Updated and Removed the caching of some Module function "Chunks" like recImage, recTitleBrief, recTitleMore.
- Updated the function "Chunks" to no longer pass the Table KeyName.

2025-05-13-16-40-35
- Removed an extra call to \xan\eleMeta.
- Renamed \xan\modules->recTitleBriefHeader to \xan\modules->recTitleHeader.
- Renamed \xan\modules->recTitleBriefMore to \xan\modules->recTitleMore.
- Updated \xan\modules->recTitleBrief and \xan\modules->recTitleMore value comparisons like ( $recs->colValue( 'Active' ) === "Yes" ? "Active" : "Inactive" ) ).

2025-05-13-14-27-37
- Removed xan.js.php and moved the code to init.php.
- Updated init.php to read xan.js.js and minify to xan.js.
- Updated init.php to read xan.css.css and minify to xan.css.
- Moved the SearchBar Filter Tooltip from the Find Button to the Clear Button.
- Updated DB_LIMIT from 100 to 50.

2025-05-11-15-55-08
- Moved functions recID and recCount from \xan\modules to \xan\recs.
- Renamed \xan\recs colNamesToMassageA to massageColNamesA and massageRowForGUI to massageColsForGUI.

2025-05-11-15-02-24
- Updated all \xan\module instances function order for the main functions.
- Updated several \xan\modules Conditional Formatting.

2025-05-10-16-40-19
- Removed \xan\recs->massageColForEcho and replaced with \xan\module->recCol_StringInline. This makes column values work like other elements with \xan\modules->recColFormattingTags.
- Changed Label html tag from div to span.

2025-05-08-13-27-51
- Updated content-page.php pages to init $recsDetail before the if.
- Added Modules for Tickets and TicketsMessages.

2025-04-29-18-01-29
- Updated xan.js.php to break the JS out into it's own file xan.js.js. Now the JS can be code formatted.

2025-04-29-16-47-33
- Updated xan.js xanMessageDisplay to optionally pass idSet to add an ID to the Message and idRemove to remove and ID. Now shows "Foo..." with an ID Set. Then when the completion time is displayed the ID that was set is removed.
- Updated xan.css --xan-bg-color-active color from Teal to LightCyan. Added --xan-bg-color-message as LightCyan.
- Updated \xan\response constructor to minimize repeated code in the module content-page.php.
- Removed \xan\eleInputsMeta everywhere. Not obsfucating anymore. Added Table Name to each DB Element and passed to doSave.php.
- Renamed FORM_OBFUSCATE_KEY to ENCRYPTION_KEY.
- Renamed FORM_META "Meta" to "meta".
- Updated content-page.php metaSet by adding \xan\module->metaSet function on individual Modules and then calling \xan\response->metaSet.

2025-04-27-12-20-09
- Changed Active Background Color from teal to lightcyan to no longer need to use dark mode colors on text.
- Updated \xan\module->recColRenderAs to include the now removed \xan\module->recColRender.
- Updated Khan and generated CalendarEventsMT.
- Updated Calendar to now be 100% wide so it can auto size.

2025-04-20-17-13-24
- Renamed do-tasks-monthly to do-tasks-weekly.
- Added Calendar Events Auto Update for ModFlag = DEMO Events.

2025-04-20-11-38-46
- Updated module->cardActionsDetail Buttons to be a Print Dropdown and a Database Record Dropdown with Duplicate, Delete, and View Access log.

2025-04-19-17-28-27
- Added Constant for APP_RIGHT_CLICK_DISABLE.
- Added a Response var $contentHeaderEnd for Module Buttons.
- Updated Modules to move Buttons from the First Card to $contentHeaderEnd.

2025-04-19-15-01-26
- Removed eleCard.php float-start. Not needed with d-flex flex-wrap w-100.
- Updated Portal Selectors to be under the index.

2025-04-19-13-19-13
- Updated \xan\module->cardListItemTable so the Selector is under the index.

2025-04-18-17-10-14
- Updated \xan\module->cardListItemTable to move the Selector right.

2025-04-17-14-19-16
- Updated all Module Portals to move the Selector to the end, before the Index.

2025-04-15-16-36-49
- Updated xanAutoLogoutCheck messages to the Console and logout cookie.

2025-04-15-14-03-20
- Added function redirectNow to \aloe\response that uses an http 302 location header.
- Moved \xan\UsersMT->pathLastSet storage from Cookies to text column Users::PathLastModules as json.
- updated \xan\UsersMT->pathLastSet redirect method from window.location.href to http 302
- Replaced the loading.php spinner with a green spinner. Added an optional $_GET[ "redirect" ].
- Updated Bootstrap from 5.3.3 to 5.3.5.
- Updated FontAwesome from 6.5.2 to 6.7.2.

2025-04-03-13-27-09
- Removed Login RememberMe.
- Removed Function isXanWorker.

2025-03-29-17-51-16
- Updated Card Functions from "Foo Ran" to "Ran Foo".

2025-03-29-15-33-14
- Renamed many of the get* functions in module.php for clarity.

2025-03-29-17-00-01
- Renamed recColRenderTypeAs to recColRenderAs.

2025-03-29-17-34-34
- Removed Selectors as Date, DateTime, and Time have selectors follow the input.
- Renamed db* functions to table*.

2025-03-29-16-54-02
- Started to replace the need to pass \xan\response and \xan\recs, but rolled back.

2025-03-28-17-57-52
- Added PHP Constant COLOR_BG_RGB for JS Signature Background.
- Renamed PHP Constant COLOR_ACTIVE_BG to COLOR_BG_ACTIVE to match.
- Updated xan.js.php with PHP Constant Tags like {php:FI_PSOS_CLOUD}.

2025-03-25-16-24-16
- Deleted xan.js.workerSafe.js and xan.js.
- Added xan.js.php which merges PHP Global values into the JS.
- Moved Global Vars, xanDoSave, and JS Helpers into xan.js.php.

2025-03-23-16-08-49
- Added ELE_TYPE_SIGNATURE_DB that saves as a Data URL.
- Moved xanDo, xanDoProgress, and xanDoResponse from page-resp.php to xan.js.

2025-03-16-16-23-01
- Updated \xan\recs and \xan\recsPDO bind types and replaced $sqlIsSelect with $ps->columnCount() > 0.

2025-03-16-14-55-13
- Removed doProgress.php example. Best Example is Schema Update.
- Removed xanDoProgress alert.

2025-03-16-14-32-10
- Looked into replacing xanDo with xanDoProgress.
- Updated native php commands with a leading backslash.
- Updated xanDoProgress to simplify and xanDoProgressMsg by checking for !connection_aborted() in the function.
- Removed old Actions button from Products content-page.php.

2025-03-13-14-35-29
- Big update again. Forgot to Commit!
- Renamed JS functions to prefix with 'xan'.
- Added functions to highlight search terms.
- Added xanDoProgress which is like xanDo but sends progress info back the browser.
- Reworked xanDoSave elements to remove redundant element data.
- Added router.php Rejections of some common path text.
- Added response.php $scriptsElementsA for a common script section.
- Deleted page-resp-jsWorkers.php to fouc on xanDoProgress.
- Updated xanToast to appear at the top in the same space as xanDoProgress.
- Added the beginnings of using search operators in the Module Search.
- Updated logEventToSQL to optionally skip logging UptimeRobot or other Events.
- Updated filesDeleteRecursive with an optional $timestamp param to delete files order than the $timestamp.
- Fixed codeContentAndScripts that was adding prior items again several times due to not resetting array vars in Modules->cardPortal.
- Added function sslCertDateExpires.
- Updated functio strFunctionNameJS to add an underscore like: fn_1234.
- Updated do-tasks-weekly-logDumpSQL.php to handle large record sets.
- Updated do-backup.php to backup PATH_ROOT_XANAPP instead of only PATH_ROOT_APP.

2025-02-11-14-42-14
- Renamed and Reordered Card functions for clarity.

2025-02-11-15-23-21
- Added Card Expand Buttons to All Cards.

2025-02-06-16-06-16
- Updated eleCard to make List and Regular card styles as similar as possible. Both now have the same params and param order. Both now have $contentHeader2 and $contentFooter.
- Removed Portal Cards Header Records Page Nav with a Footer Records Page Button Group.
- Replace all SQL Count(8) with Count(*) since it makes no real difference.
- Fixed a bug in eleSelect. The Selected Item now compares as a string.

2025-01-28-13-25-02
- Updated Contacts Cards.

2025-01-25-16-51-19
- Fixed page-resp.php pageContentColumnsFixedHandler(). Now checks to see if fixedColumn exists before trying to Toggle.

2025-01-25-14-39-01
- Removed eleSearchBarListDB.php and eleSearchBarSimpleDB.php.
- Replaced QueryBuilder with a single field search plus a select to choose All fields or a specific field from \xan\modules->SearchTablesA.
- Removed schema isIndexFullText for now. Reverted to using LIKE which is fast enough, for now.
- Updated page-resp.php to use CSS vars to track the height of the nav and Header to place the pageContentColumns correctly.
  Updated page-resp.php to have a left column for lists \xan\response var $contentLeftA was added. If the array has no elements, the left column and button to toggle are not displayed.
- Added a body background color to make the page be less bright.
- Added Module vars for the new search: SearchTerm, SearchSort, SearchFilter, SearchWhere, SearchBindValuesA.
- Updated eleSelect to support Disabled and Checked.
- Updated eleCard to have min-width and min-height so they cannot be undersized.

2025-01-14-16-03-23
- Renamed the page-resp.php backup to page-resp-jsWorkers.php for future use.
- Added code and classes for Web Awesome.
- Removed code and classes for Web Awesome. It's nice but not a huge benefit over Bootstrap.
- Updated xan.php to have an eleHash function used for Web Awesome Ajax Save.
- Updated \xan\xan->schemaUpdate() and added properties for isFindable and isIndexFullText.

 [Before 2025](README_Before_2025.md)
