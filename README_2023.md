# Xanadu Pro Change Log 2023

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, Refactored, NOTE ]

**Change Log**

2023-12-31-16-59-50
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated FontAwesome Free version to 6.5.1.
- Updated Recs, Portals, and Module List New to have a specific Modal name like 'RecDupContacts' but all use Action names like RecNew, RecDup, or RecDel.
- Updated Routers with shared 'do.php' files for related tables to now use their own folders with their own do.php and router.php files.
- Moved API files to the APIRequests folder.
- Renamed all printing files to be "do-print.php". Additional printing files can be called "do-print-foo.php".

2023-12-30-14-20-16
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Changed SettingsCompanies Icon to be fa-bell-concierge.
- Added a class moduleMini that is like module, but minimal.
- Updated mmHome and mmCalendar, mmCheckout to no longer extend as a module but as a moduleMini. Kept since the are substantial. Didn't add back UsersLogin, UsersLogout, UsersPasswordReset, UsersRegister, or Xan_Labs since they are minimally accessed.
- Updated mmHome and mmCalendar by moving the Card to their moduleMini file.

2023-12-29-17-36-41
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated each router file require_once statements to use relative paths.

2023-12-29-17-24-14
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Renamed ContactsAddresses to Addresses.
- Renamed ContactsCommsto Comms.

2023-12-29-16-00-52
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated all $aloe_response->content_set( require_once( PATH_PAGE_RESP ) ); to use require.
- Renamed urlShortener to linkShortener.
- Moved "Link Shortener" form form Home to the Menu Dropdown.
- Added a php function getEleID to return a database input ID.
- Renamed Link Shortener New from "lNew" to "linkNew". Go to link "l" remains the same.
- Updated Javascript "arrow functions" to use "function" for simplicity.

2023-12-28-17-49-10
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Removed Module xan_labs since it's not really a Module.

2023-12-28-16-56-43
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Removed Modules: UsersLogin, UsersLogout, UsersPasswordReset, UsersRegister, ServerStats
- Moved Folders for UsersLogin, UsersLogout, UsersPasswordReset, UsersRegister folders to app/users/logins as login, logout, passwordreset, register.
- Updated app/users/logins Pages and do Files to no longer rely on a Module as they don't actually have a Module but are parts of Users.

2023-12-27-14-13-19
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Added router.php files for each Module and the main router.php to mostly use a switch by component 1 character 1 rather than many, many ifs.
- Replaced the File Browser as the prior library would not work in PHP 8. Needed to download the include files and fix the FontAwesome Icon Names.
- Updated \xan\fontIcon calls in each modules Action Menu to be wrapped in \xan\fontIconButton so each is the same width.
- Updated do-record-print.php pages to use NameSignular for the Page Title and Doc Title.

2023-12-24-17-53-01
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Added TODO: Settings Example IMAP was not connecting. Added a note.
- Added TODO: Settings Example Stripe was not working. Needs to be updsted to PHP 8.2.
- Removed the Includes for EDI X11.
- Removed the Exception Handler in the Xan Class Autoloader. It was preventing the AWS Textractor from performing its Autoloader.
- Moved the DB Compare code from Home to Settings Examples.
- Updated calls to \xan\sendSMSDebug to \xan\sendEmailDebug.

2023-12-21-18-04-27
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated urlShortener "URLs" Table Name to be "Links".
- Updated Router so the Links API calls could be saved in app/links as a second router file. Added at the top of router.php for speed.

2023-12-21-17-16-01
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated page-resp.php Menus placing Logout at the end.

2023-12-21-16-30-57
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated git files that were not pushing. Added special files to ignore.

2023-12-21-16-04-08
- STILL IN THE MIDDLE OF UPDATING PORTALS: Need update other tables Portals to match.
- Updated Settings Inputs to be Reveals.
- Added Schema column InputMode for mobile. Default is none or "decimal" for numbers columns.
- Renamed colMeta to eleMeta.
- Renamed functions.php to constants-and-settings.php.
- Renamed functions-schema.php to functions-eleDB.php.
- Updated xanSchedAutoLogout check interval from 5 min to 1 min. Updated to show its status on load.
- Updated AutoLogout to use the Settings AutoLogoutSeconds. There were two contants with similar names. Removed the one set to one hour and replaced with Settings AutoLogoutSeconds.

2023-12-07-18-39-09
- STILL IN THE MIDDLE OF UPDATING PORTALS: Contacts and Khan are inline. Plan is to keep them in sync. Need update other tables Portals to match.
- Lots and lots of changes to get Khan working based on Contacts Portals.
- Now looking for bugs...

2023-11-14-17-27-46
- STILL IN THE MIDDLE OF UPDATING PORTALS
- Many Modules now have their Cards and Portals defined. Need to update the remaining modules and then replace Khan.

2023-11-09-17-23-08
- STILL IN THE MIDDLE OF UPDATING PORTALS
- Removed GLOBALS in favor of Singleton. $xan and $dbSchema are now accessed via \xan\xan::inst();

2023-11-07-16-08-32
- STILL IN THE MIDDLE OF UPDATING PORTALS
- Refactored Modules to Singleton. Can instantiate anywhere: $mmSalesT = \xan\salesMT::inst();

2023-11-05-14-37-49
- STILL IN THE MIDDLE OF UPDATING PORTALS

2023-09-24-14-47-24
- IN THE MIDDLE OF UPDATING PORTALS.
- Updated Ajax calls for Products Prices.

2023-09-16-18-12-20
- Pickers now have a border like XanControl.

2023-09-16-17-37-45
- Huge updates from PHP 7.4.x for prior commits. Now PHP 8.2.x.

2023-04-20-17-42-45
- Added Setting for the Default UUIDSettingsCompanies.
- Added Settings Constants for several that were missing.
- Added Settings Constant APP_UUID_SETTINGSCOMPANIES to be auto assigned on Sales Records.
- Updated \xan\module Search to Limit to DB_LIMIT.
- Updated \xan\module->QueryOrderByDefault uses of 'Active ASC' to 'Active DESC' so 'Yes' will appear before 'No'.
- Updated the in progress Sales Module.

2023-04-20-15-07-01
- Added xan.js xanDoJS option for triggeringEvents. Using to update a column and save.
- Added xan.php ARRAY_PAYMENTS_FORM Constant.
- Updated xan-do-save.php to get the values before updating and then use to compare to changes.
- Updated all uses of "xf_" to the FORM_PREFIX Constant.
- Renamed \xan\recs->moduleMeta to \xan\recs->module.
- Updated \xan\recs function recordInsert to aut insert the passed rowD, then apply the \xan\module onInsertColValues, then build the SQL statement.
- Added xan-functions-dataMassage.php function strToNum( $text ) which will convert text to a number by filtering non-numeric chars and then cohersing into either an int or float.
- Added xan-module.php getCol functions for Notes FileNameImage, and FileNameLabelWButtons.
- Updated xan-module.php getCol functions Input and Input_Portal to be display: inline-block;
- Updated defined modules to use Font Icon Constants for easy reuse.
- Updated defined modules function onInsertColValues to pass \xan\recs instead of $rowD. The function uses $recs->rowsD.
- Updated defined modules function onSaveColCalcs to use the updated tooltip functions.
- Updated \xan\tags functions tooltipTagsString and tooltipExtraD to add the 'data-bs-trigger' = 'hover' to have tooltips auto hide for Selects and Buttons.
- Updated page-resp.php xanInit Tooltip Init to use jquery and set onMouseLeave to blur to to have tooltips auto hide for Selects and Buttons.

2023-04-15-16-51-59
- Renamed \xan\tagExtraToolTip to \xan\tooltipTagsString. Added \xan\tooltimExtraD.

2023-04-15-14-55-33
- Added IMAP Settings
- Renamed SMTP Settings.
- Added IPStackKey Setting.
- Added IMAP Settings to Users.
- Renamed the SMTP Constants. Removed "_MAILGUN" from the end.
- Fixed a few uses of \xan\eleMeta->eleFormatAs.
- Removed setting of the attributes on eleDB: data-format, data-key, and name. Each was redundant.
- Updated all uses of data-format, data-key, and name.
- Renamed \xan\formTag to \xan\inputsMeta and moved the class to its own file.
- Renamed all uses of $formTag to $inputsMeta.
- Added the function urlEncodeComponent to encode spaces and such in urls.
- Updated xan-imap.php to use the new Users IMAP Settings.
- Removed IMAP and IPSTACK Constants from the init files.

2023-04-13-13-50-30
- Updated \xan\tags to convert extrasA array to extrasD dict. Changed string extras to dict values.
- Updated xan.css .xanControl to include read-only for flatpickr elements.
- Removed tag variables from \xan\eleMeta.
- Updated \xan\recs to have query() and queryModule(). The latter would query and store a reference to the \xan\response and \xan\formTag.

2023-04-02-17-22-41
- Added xan.css style .tooltip to prevent the pointer from changing which stops the flicker.
- Added xan.css styles .xanCheckbox100 to .xanCheckbox300 to scale checkboxes size.
- Updated xan.js and xan-response.php to replace Dict Values with Vars to make it easier to read. Added functions for jsRemove, jsBlink, jsSetValFlatpickerDate, jsSetValFlatpickerDateTime, jsSetValFlatpickerTime, and jsSetScrollTop.
- Added xan.php Constant COLOR_TABLE_HEADER_BG for Headers.
- Updated \xan\fontIcon function to remove unneeded classes.
- Updated \xan\eleTable to fix bug in ColMax where RowGroup and IsSticky values were treated as a Col Value. Now defaults to Col = 0.
- Updated \xan\TAG_CELL functions so $classA, $styleD, and $extrasD can be passed.
- Added /app/home/ Contacts Portal Selection Check Boxes to select one or many contacts. Clicking View will show an Alert of the Contact IDs.
- Added /apps/server-stats contentCard-stats-diskRam.php PHP version to also show the User Name that is running PHP using exec('whoami').
- Updated /app/projects content-portal-projectstasks-table.php to have a floating header for the Title/Desc and a Leading Break on Project Item Title.

2023-03-12-17-27-13
- Removed TAGS_ELE_INPUT_PORTAL default height as it was not needed.
- Added function \xan\cssSizeAdjust( $sizeUnit, $adjAmount ) which does math like 10rem, -2: 8rem; 10rem 2: 12rem.
- Updated \xan\eleTextAraDB to automatically set its height to 100% if there is not a height already set as most cases the TextArea's cell is set to a specific size.
- Updated Contacts Notes, Projects Portal ProjectTasks Table, User Privs.

2023-03-11-16-44-48
- Updated Content Records to now set its $colName rather than repeat the column name text.
- Updated Portal Comment for the Table Index Header.

2023-03-11-14-58-35
- Renamed $tableRowIndex to $rowIndex.
- Updated /apps/projects/content-portal-contacts-table.php as it needed two Row Indexes to build the main table and sub tables: $rowIndex and $rowIndexSub.

2023-03-11-14-07-58
- Renamed \xan\module "getColEleRendered" to "getCol". Added recCol_LabelBlock, recCol_LabelInline, recCol_Input, recCol_Selector, recCol_LabelBlock_Portal, recCol_LabelInline_Portal, recCol_Input_Portal.
- Renamed \xan\tags get helpers TAGS_CELL_LEFT_TOP, TAGS_CELL_LEFT_MIDDLE, etc to TAGS_CELL_LT, TAGS_CELL_LM, etc.

2023-03-08-17-49-06
- Renamed ELE_AS_LABEL to ELE_AS_LABEL_BLOCK and added ELE_AS_LABEL_INLINE to be able to use line-height for Labels.
- Updated all uses of ELE_AS_LABEL to either ELE_AS_LABEL_BLOCK or ELE_AS_LABEL_INLINE. Portal Tables tend to use ELE_AS_LABEL_INLINE.

2023-03-02-17-35-59
- Removed the Menu Item to "Reset Page Card Sizes".
- Updated Portal Tables from TAGS_DIV to TAGS_CELL_ and set to be either thead or tbody.

2023-02-28-22-06-13
- Updated Portal Ajax in Comms on Khan's zzTableTemplate Portal.
- Now uses the CardID so Grid and Table versions can both work at the same time.

2023-02-28-16-16-22
- Added functions to xan.js: xanFadeOut, xanFadeIn, xanFadeOutAndIn.
- Added functions to response.php: xanFadeOut, xanFadeIn, xanFadeOutAndIn, and jsSetScrollTop.
- Renamed response.php function "jsOnLoadSelectorFocus" to "jsSetFocus_OnLoad".
- Added in xan-element-card.php an optional parameter $contentBodyEnd in renderCardWithDiv.
- Updated /app/contacts/ files so Comms Grid New, Delete, and Duplicate replace the Card Body Contents and update the record count in Card Body Header.

2023-02-23-17-42-26
- Added a xan.js XanToggleDisplay object parameter to be able to access the ele.style.display back to the calling function.
- Updated app/contacts/do.php to add do-contactscommms-urlGet.php back in. Found that the Comms url buttons were not working. Like lost it when generating Contacts module via Khan.

2023-02-20-10-41-08
- Removed DataTables includes. Now using tableDnD and TableFilter.
- Renamed \xan\response js action 'setFocus' to 'setFocusOnReturn'.
- Disabled Resizeable Observer automatic Card resizing as the behavior is off. Planning to add back in the future where the user chooses to save Card default sizes.
- Updated /app/sales/content-portal-salesitems-table.php Card to be wider.
- Updated Portals to init the \xan\formTag before loops as some comments needed to access the values.
- Updated Contacts Cards to be taller via $resp->cardHeight.

2023-02-19-14-58-28
- Updated \xan\eleTable to add a $tableStyleWidthMax setable via the Constructor. Defaults to 99%.
- Added a Contacts Card for 'Associations'. Removed two columns on 'Associations' from 'Other'.

2023-02-19-13-27-59
- Updated use of \xan\module->getColEleRender[ed] and getPicker, module instances, record cards, and portal cards to remove the params \xan\recs $recs, \xan\formTag $inputsMeta, \xan\response $resp to reduce duplication as they can be passed using the set Functions.
- Removed \xan\module->getColEleRenderLabel, getColEleRenderInput, getColLabel, getColLableEle replaced with the longer functions as they were not used in many instances.
- Added xanDo js function to add commpent with ideass for swapping elements on returning the response.
- In app/contacts/content-record-contacts.php, experimented by adding labels and inputs in a loop of a column name array.

2023-01-26-18-28-12
- Removed eleTable DataTables which were a bit complicated due to working with data and rendered.
- Added eleTable TableFilter and TableDnD to replaced DataTables functionality.
- Updated eleTable->rowSet to pass an ID for the row.
- Updated eleLabel from using div to span so eleTable TableFilter can place the sort indicator properly.
- Added Contants for INDEX_WIDTH, ZINDEX_THEAD_TFOOT, TOOLTIP_TABLE_FILTER.
- Added xan.js xanScrollTo, xanToggleDisplay, and xanToggleVisible.
- Added xan.css trdrag, nodrag, nodrop.

2023-01-05-16-23-17
- Added function numDisplayCurrency( $num, $dec = 2, $currencySymbol = APP_CURRENCY ).
- Added Total Sums to Portals: Sales, Purchases, SalesItems.
- Modified from using Grids to Tables for the most part. Grids tend to create tall content but stack data nicely.
- Modifed Home to use Tables for Projects, Sales, and Purchases.

2023-01-05-12-39-46
- Updated \xan\eleTable to set cell 0, 0 to "" to avoid error when no cells are set.
- Removed queries on zzTemplate on content-portal-related.
- Updated Contacts Projects and Sales to show as a portal. Added a Picker as a GTRR.

2023-01-04-19-06-06
- Updated Projects by generating using Khan, then moved card contents.

2023-01-03-18-51-19
- Renamed function \xan\arrayContainsString to \xan\arrayContainsValue.
- Added first version of Module onInsertColValues. Needs testing.

2023-01-03-14-24-30
- Renamed xan files to remove "adu" from the filename. Also renamed "fns" to "functions".

2023-01-03-14-07-25
- Added \xan\module variable $FocusColName. Added in each module and in each do file.

2023-01-02-17-16-38
- Added a quote parameter to function tagExtraTooltip.
- Added \xan\response "jsSelectorTriggerChange_OnLoad" to trigger a change on an array of selectors via a php session array.
- Renamed \xan\response function name from "jsSetFocusOnPageLoad" to "jsSetFocus_OnLoad".

2023-01-02-13-19-22
- Added \xan\module->getPortalCard to separate it from getListCard. There were enough differences that it should be its own function.
- Updated each \xan\module->getContentTextBrief to return '[ New ' . $this->nameSingular . ' ]'. No longer need to set a column value to show in Lists.
- Updated each app/module do-record-new and do-portal-new/dup/del files to support passing $doParam[ 'ColVals' ].

2022-12-31-15-42-26
- Fixed Portal Delete Buttons from $xanDoDelete to $xanDoDel.

2022-12-31-13-37-41
- Updated Contacts and Sales to work like the Khan changes.
- Updated each \xan\module->onSaveJSActions to add an underscore before "Label".

2022-12-31-13-37-41
- Updated Products, Purchases, SettingsCompanies, Vendors to work like the Khan changes.

2022-12-30-16-05-05
- Khan ran for Contacts, Products, Sales, Purchases, SettingsCompanies, Vendors. Made the Kan Module the default for all but Contacts and Sales.

2022-12-29-16-24-07
- Updated Khan. Renamed files and updated code to make records vs portals clear.
- Updated \xan\filenameClean to have a default but overridable space char set to " ".

2022-12-29-13-52-43
- Updated Khan with new module file names.
- Updated \xan\filenameClean to remove "#" and replace "",-" with ",".

2022-12-28-11-02-50
- Updated Products ProductsPricing Portal so it can be used on Products and Contacts.
- Updated Khan to optionally include a Portal for the Module Table for ease of adding to other modules.
- Updated Khan to add a suffix "khan" to prevent overwriting existing modules. Module folders are suffixed and Module files are prefixed.
- Updated Khan Portals and do-New/Dup/Del so they can be used on other Modules.

2022-12-26-17-51-27
- Modified Contacts Pinned Icon. Moved from getContentTextBrief to getContentList Text.
- Modified Card Header font-size from default to "larger".

2022-12-26-17-24-15
- Modified Card File Names to begin with "z-" for unused cards. Removed the commented out uses.
- Modified Primary Card require_once to use the lower case table name rather than a calcuated name.

2022-12-26-16-34-25
- Added \xan\module->getColLabelEle to return a Label with Alignment.
- Removed \xan\eleLabel Render parameter $isPortal as the tags are now passed.
- Updated each card with the five line code for labels down to two lines by calling \xan\module->getColLabelEle.

2022-12-22-17-49-08
- Found a bug in js xanResizeableSave. Card width would get narrow. Found that each reload would take 10px off the width. Fixed by no longer using ResizeObserver entry various width and height and replaced using jquery width and height which is used to set the values.

2022-12-22-16-13-26
- Removed New Record Modal from each content-page.php since the List Card includes the Modal definition.
- Changed all uses of "= /** @lang JavaScript */" to use "/** @lang JavaScript */ = " so the code will be on the same line.

2022-12-22-14-27-09
- Updated Contacts with a Pinned = Yes/No column.
- Updated the sort on Contacts List and Home Recent Contacts so Pinned Contacts appear at the top.
- Updated mmContactT.php onSaveColCalcs to automatically set blank or null values for Active and Pinned columns to 'No'.

2022-12-20-17-53-30
- Added \xan\Module\getListCard to create a Card List with Search as a function.
- Updated Each List Card with \xan\Module\getListCard. Removed a ton of repeated code.
- Updated \xan\element\eleSearchBarListDB to pass optional params to make reuse of List Cards possible.
- Moved \xan\element\eleSearchBarSimpleDB below \xan\element\eleSearchBarListDB.

2022-12-18-15-28-00
- Updated Products to use the Attr Labels from Settings.
- Updated mmSalesItemsT.php onSaveColCalcs to support a Code col as a typeahead field. Editing replaces the selected Product using the Code.
- Updated mmSalesT.php header and picker to show like: Invoice #100, 11/16/2022, $120.
- Updated \xan\eleMeta so choices can use a Constant that ends with "_CHOICES_SQL" which is an array with the Table Name and an SQL Statement.
- Updated \xan\modules so Pickers use the shorter Header Text over the longer List Text.

2022-12-15-17-56-59
- Renamed DB Columns "Desc" to "Description".
- Renamed Products "Title" to "Name".
- Removed addtional ELE_AS_INPUT_TEXTHIDDEN from Cards that use Picker since the Picker adds it own ELE_AS_INPUT_TEXTHIDDEN.
- Decided on Grid vs Wide table for Products Pricing, Vendors Products, Sales Items.
- Updated Picker to include an optional Image along with the text.
- Updated Picker to include a Clear Button when the Search Button is displayed.
- Updated the $mm module var to $GLOBALS[ 'mm' ] so modules can be available within functions.
- Updated AutoLogout to check on the browser tab focus to see if the user should be logged out.
- Renamed the xan-save.php to xan-do-save.php to group with future global do files.
- Updated xan-do-save.php to pass the changed columns onto \xan\Module->onSaveColCalcs to know what calculation to apply.

2022-12-08-17-37-00
- Added a new ELE_TYPE_FILE_BUCKET_DB Render ELE_AS_LABEL_AND_BUTTONS used to create the Label, Upload Button, and Clear button. Also added ELE_AS_FILE_BUTTON_UPLOAD and ELE_AS_FILE_BUTTON_CLEAR.
- Added a Module doFileBucketSetURL function to make easier use in do.php.
- Added a PhotoFN for Users table. Added the Photo to Users Detail with a Gravatar Set Button. Added the Photo to the List Table.
- Added Constant STR_GRAVATAR_SET_PHOTO for the text on the "Set Photo to Gravatar" button.
- Added Constants IMAGE_HEIGHT_LIST, IMAGE_HEIGHT_INPUT, IMAGE_HEIGHT_LARGE for Image Size consistancy.

2022-12-04-17-42-28
- Removed Contacts standalone picker. Will replace using a version of the existing picker when needed.
- Modified \xan\Module->getContentImage to return a rendered string instead of the object.
- Modified \xan\Module to add a $tagsCellImage property for the image cell size.
- Removed \xan\Module->getListItemTableForPicker now using \xan\Module->getListItemTable everywhere.
- Removed \xan\Module->getListItemTable_Text and \xan\Module->getListItemTable_ImageAndText. Now can call \xan\Module->getListItemTable include the image automatically, if defined.

2022-12-04-12-36-36
- Modified xan.php into 25 separate php files, each required in init.php.
- Removed Module->getContent and replaced with calling the content types directly like Module->getContentTextBrief.
- Renamed eleURLImage to eleImage as the URL is a parameter.
- Renamed Module->doPicker to Module->getPickerContent.
- Renamed Module->getListItem to Module->getListItemTable.
- Renamed Module->getListItemWImage to Module->getListItemTableWImage.
- Renamed \xan\phpFileInfo to \xan\logEventPhpFileInfo to make it part of the log functions.

2022-12-01-15-38-40
- Updated Picker to use the Column Name passed instead of the default Table Key Name to support using fields like ReferredUUIDContacts.
- Updated Picker to use the cell instead of the text for the onclick. Using the text result areas not being clickable.
- Added to Contacts: Picker for Salesperson Staff and Picker for Referred By Contact.
- Updated app/module/content-page.php to not define an image. Inead now calls the Module->getListItem function or getListItemWImage.
- Added Module->getContentImage.
- Updated xan.js xanMessageDisplay to remove the Saved Column Name from being displayed in the menubar. Now states "Saved". The Column Name is included in the Browser Console.
- Added xan.js functions for xanStrSubstitute and xanStrBetweenNeedles. Using same names as php functions when possible.

2022-12-01-11-14-39
- Updated \xan\Module->getPicker. Was using the page Record Key and now using the Module Record Key. This make it possible to work with Portals.
- Updated all Modules->getListItemTableForPicker so the Module ListRow content can be reused.
- Added PICKER_SHOW_GO_BUTTON Constant for a default to show a Go Button for Pickers. Default is false as the ListRow data is a button itself.

2022-11-28-09-07-58
- Updated the order of the Menus to move Projects before Sales.
- Updated File Browser menu item to open in a New Window.
- Updated the background color of Picker data.

2022-11-27-17-52-04
- Updated Column Value Massaging. Now optionally Massages all Detail values, post query. List values Massaged as specified in the Module getContentListRow and getContentHeader.
- Renamed massageColsForGUI to massageRowForGUI.
- Added massageColForEcho to massage one value.
- Added examples to getContentListRow and getContentHeader for getting the Actual or Massaged value.
- Added a Clone function in \xan\recs. Experimented with Cloning Recs.
- Added a function \xan\arrayClone for Cloning Arrays.
- Added a function \xan\objectCloneDeep for Cloning Objects.
- Added Khan to the User Menu for Admins.

2022-11-23-19-14-29
- Added \xan\xan\products, \xan\xan\purchases, \xan\xan\settingscompanies, \xan\xan\vendors. Some were not added to git.
- Added Settings Columns for the three Product Attribute Labels.
- Changed Products Cards to use the Settings Product Attribute Labels. Need to use as labels everywhere.
- Renamed Settings Cards numbers for grouping.

2022-11-22-17-48-15
- Updated Khan Module Header to break each column into its own append so commas will be presented correctly. Auto adds the first four columns.
- Added Vendors Module using Khan.

2022-11-22-15-53-30
- Updated \xan\modules->getContentHeader and \xan\modules->getContentListRow to be in that order and to call \xan\recs->massageColsForGUI only one time.
- Updated the new modules ( SettingsCompanies, Vendors, Products, Products Pricing, and zzTemplateModule ) to define columns for the Header and ListRow.

2022-11-22-12-28-27
- Added Module Settings for SettingsCompanies, Vendors, Products, and Products Pricing.
- Added SettingsCompanies Module generated with Khan and fixed Khan issues.
- Fixed \xan\module->getListItem to set the cell to 0, 0 instead of 0, 1.

2022-11-21-11-26-18
- Renamed Module and Table Events to CalendarEvents.
- Renamed Module and Table Trans and TransItems to Sales and SalesItems.
- Added Module and Table Purchases and PurchasesItems.

2022-11-15-14-34-07
- Renamed Root folders to xanApp, xanCache, and xanStorage with constants PATH_ROOT_APP, PATH_ROOT_XANCACHE, and PATH_ROOT_XANSTORAGE as App conflicted with PATH_ROOT_APP.
- Updated Settings and Stats to use the new paths for xanApp and xanStorage.
- Added /xanApp/xan/xan-mysqlReports.php for creating FileMaker like sub summary reports with an example.

2022-10-18-16-14-51
- Set All Cards to default to a height = $resp->cardHeight which defaults to CARD_HEIGHT_0100. Settings > Users overridden to CARD_HEIGHT_0125, a newly added card height.

2022-10-02-16-44-08
- Updated Contacts Comms spacing.
- Updated Projects > ProjectsTasks with Dividers only below records and not after ProjectsTasks.
- Disabled Loading the last record if no record is loaded. Can be enabled again.
- Updated in xan.css the xan-font-size-portal from 0.7rem to 0.8rem.
- Removed Constant PORTAL_LABEL_FONT_SIZE.
- Added Constant PORTAL_HEADER_HEIGHT.

2022-10-01-18-10-12
- Added Module automatic last record reload if going to the Module without a record selected, mimicing FM selected record. The Found Set is NOT restored, only the last record viewed.
- Updated Pickers to use DB_LIMIT.
- Updated Projects > Print like our old FileMaker database.
- Updated Projects > Print can receive a comma delimited list of ProjectsTasks IDs to print only those ProjectsTasks to the Ballpark Estimate.
- Updated templates/pdf-default Footer to use the Printed Date by replacing [[DATE-PRINTED]] to show localized dates. The wkHTMLtoPDF dates were in non-US formats.

2022-10-01-13-26-37
- Added an ID to each instantiated \xan\eleCard to auto save and restore its width and height.
- Added a User Menu Item to "Reset Card Sizes". This will clear the saved Card width and height values for the current page.

2022-09-29-16-15-41
- Added DisplayedShortcut Keys to Print PDF and the SearchTerm.
- Added in Projects Checkboxes to Select ProjectsTasks that remember their Ticked State in the Browser Local data.
- Added in Projects on ProjectsItems and ProjectsTasks Cards that remember their width and height in the Browser Local data.
- Added in Projects the ability to select a ProjectsItem to see only the related ProjectsTasks.
- Updated Projects Print to match our Ballpark Estimate format. Need to finish.
- Added to Modules the getColEleRender function that can be used for Conditional formatting of data using style and color classes.
- Added templates/pdf-default CSS includeds for the Color Classes and Font Awesome. Added to the Header, Body, and Footer.
- Added FontIcon Constants for Modifier Keys. Also added a version with simple chars for where Font Icons cannot be used like Input Placeholders.
- Fixed \xan\xan-printer.php so the Headers and Footers work. Was checking the Header replacements as a string, but needed to be an Array Count.

2022-09-18-15-48-14
- Added a Query Limit of 100 when doing a Find with an Empty Search Term.
- Added an Asterisk Button to the SearchBar to Find All with no Limit.
- Added the Total Record Count to the Card Title with the Found Record Count like "100 of 487".

2022-09-18-15-00-27
- Added a link to CHANGELOG.md in README.md.

2022-09-18-14-56-09
- Fixed Bug in \xan\paramDecodeQuotes used in QueryBuilder. Spaces ended up around the ampersand in &quot.

2022-09-18-14-26-17
- Renamed \xan\module->getDisplayHeader to \xan\module->getContentHeader.
- Renamed \xan\module->getDisplayList to \xan\module->getContentListRow.
- Replaced calls to \xan\module->getContentHeader with \xan\module->getContent which acts as a mini router for table calcs. Can pass already queried \xan\recs or an ID to perform a fresh query.
- Added \xan\cacheGet and \xan\cacheSet to be used with \xan\module->getContent but the small bits of data read from disk was slow. Keeping for future use.
- Updated xan.js xanGoURL to support using the alt/option key to open links in a new window.

2022-09-13-14-26-41
- Updated \xan\module->getPicker so the Search and Go buttons are optional.

2022-09-13-13-23-14
- Fixed Contacts > Comms switching between Comm Types.
- Renamed Projects Cards to use the standard naming.
- Updated Projects to show the Sum of Hours for Estimated and Actual.
- Fixed eleGrid Margins and Padding.
- Updated Tooltips in xan.css so Tooltips can be be as wide as needed. Use <br /> to force breaks.
- Added xanModifiers in xan.js can now check xanModifiers.altKey to see if alt/option is pressed.

2022-09-08-18-55-05
- Updated Projects Tasks element placement.
- Added in xan.css ".row.active" so the selected Grid Row is highlighted.
- Added a white border to the standard buttons for contrast on a selected Grid Row.
- Added to HTML_DIV_DIVDER the class "m-1" to add a slight space between rows.
- Updated all uses of Tooltips to use \xan\tagExtraTooltip function.
- Added Projects > ProjectsItems Tooltip on Status Label. Shows Sum of Related ProjectsTasks HoursEstimated and HoursActual.

2022-09-08-16-13-18
- Looked at removing JQuery where possible, but we're using a few libraries that use it heavily. Doesn't seem worth the time right now.
- Changed xan.js use of "bind" to now use "on".
- Fixed Settings > LoginWith2FA as the wrong field was used.
- Changed the User Menu divider groupings.
- Added Constant STR_URL_SEP. Already had STR_DIR_SEP and STR_SEP.
- Updated Projects > ProjectsTasks Duplicate and Delete to reload with the ProjectsItems ID in the URL.
- Renamed in \xan\response  jsSetFocus to jsSetFocusOnReturn which will set the Focus on xanDo Return.
- Added in \xan\response jsSetFocusOnPageLoad which will set the Focus the next time a Page Loads.
- Updated Projects > Tasks Duplicate and Delete so when the Page Loads to include the ProjectItems ID.
- Updated Projects > Tasks Duplicate to set the Focus to the ProjectsTasks Title after the Page Loads.
- Added Calling Examples to \xan\timeDiffInSeconds and \xan\timeDiffInHours.

2022-09-06-16-02-32
- Added Form for Projects > Items > New Task Dialog to enter Title, Desc, Hours, or a 'Formatted' Task.

2022-09-06-14-02-32
- Added eleGridArticles element that can show floating Articles, similar ot floating Cards but with no borders.
- Added eleGridOfRows that behaves like the existing eleGrid, but less complex.
- Removed eleGrid and eleGridRow after updating to eleGridOfRows.
- Updated \xan\eleMeta columns to use the Column Name if the Label is not set.

2022-09-05-14-17-47
- Added Settings > Features LoginWith2FA.
- Updated Settings > Features Auto Logout Seconds to have a Tooltip: -1 to Disable; 3600 for 1 day; 25200 for 7 days;
- Updated navItemDropdownModule and navItemDropdownCustom FontIcons to be the same width and centered. Previously, each icon was left justified, but Icon widths varied.

2022-08-23-16-51-01
- Added Contact fields EmailTo, RateHourly, DriveMiles, DriveHours.
- Added /xan/Module function getListItemTableForPicker and added function to each class instance.
- Added /xan/Module functions getPicker that renders a picker and doPicker that handles the picker search results.
- Added Projects field pickers for Contact and Staff.
- Added Tooltip Underlines to objects that can show underlines. FontAweseome buttons do not underline.
- Added class to xan.css xanControlBackground so picker value text have the background but not a border like regular controls.
- Added ElementAs Type ELE_AS_INPUT_TEXTHIDDEN for the UUID Input for the picker.
- Added Schema LabelENTooltip to be able to have system wide Field Tooltips like Contacts 'EmailTo'.

2022-08-16-15-13-12
- Continued on Projects...
- Added Note about how to generate an in file password in /xan/xan-file-browser.php.
- Added TAGS_ELE_LABEL_PORTAL for Labels not in the Header.
- Updated /xan/xan-save.php to enclose Column Names in backticks. Updated to skip updating values if the Element Value = '' and the DB Value = NULL.

2022-08-13-17-40-17
- Started to edit Projects.
- Removed old File Editor, PHEditor.
- Added Files Browser available from Setting Actions menu. Connected to the session and will log out when the user logs out.

2022-08-09-18-08-42
- Added Module files for Disbursements, Projects, ProjectItems, ProjectTasks, Trans, TransItems.
- Added \xan\Response variables req1 thru 5.
- Updated Projects to Show ProjectsTasks from ProjectsItems. Added New ProjectsTasks button that works even if the Item is not selected.

2022-08-09-15-37-13
- Added Khan Generated Projects and Transactions to Git.

2022-08-08-10-02-15
- Removed Khan Transactions and Projects. Added Demo for Plans based on Projects, but renamed. Plans will be kept as an example for Khan.

2022-08-07-15-38-03
- Added a Schema Update Menu Item in Settings Actions which loads and saves a JSON file as a cache stored at PATH_ROOT_XAN . FILENAME_SCHEMA.

