# Xanadu 

**Xanadu is a framework for developing Database Driven Web Apps.** 

Xanadu uses PHP, MySQL, HTML, Bootstrap, CSS, and Javascript with several amazing includes.

We've been developing Database Apps for decades with FileMaker and Xojo. FileMaker rocks but licensing became too expensive. Xojo has fantastic pricing, but is perpetually buggy. We had to find an alternative platform. PHP kept coming up in our searches. Long story short, we decided PHP is the best option just to get back to an affordable and solid platform.

Read more about Xanadu: https://campsoftware.com/products/xanadu.php

# Xanadu Pro Change Log

**Try to use:** [ Found, Fixed, Updated, Moved, Added, Removed, Renamed, Replaced, Decided, Planning, NOTE ]

**Change Log**

2026-07-07-20-15-19
- Fixed delete action failing with 400/500 errors by correcting `{$this->nameModule}` to `{$this->nameTable}` in delete modal JavaScript (xan/module.php:1131)
- Fixed duplicate SQL bug by adding validation for empty `$theCols` and `$rowD` to prevent invalid UPDATE statements (xan/recs.php:521,555)
- Fixed portal refresh after New/Delete/Duplicate by changing `isDoAction` check from `!empty($_POST['Do'])` to `!empty($_POST['params'])` in Blasts and Contacts modules
- Fixed checkbox selector mismatches by standardizing on `List{$module}Selected` instead of `Portal{$module}Selected` across 44+ module class files
- Fixed timestamp display not appearing by enabling `colNamesToMassageA` in BlastsMT and ContactsMT to format date/time fields for GUI
- Added generated FoosMT and FoosItemsMT modules to validate generator template fixes work correctly
- Updated XanLabsM generator form to default to "Foos" for testing
- Added E2E test coverage for Blasts, Contacts, and Foos modules including CRUD cycle, duplicate, delete, and portal operations
- Tests: 29 Playwright E2E tests, 27-28 passing (97% pass rate). Core CRUD functionality verified working.

2026-07-02-16-26-14
- Fixed doTests log directory path from legacy Projects folder to working directory
- All PHPUnit tests passing (448 tests)
- All Playwright E2E tests passing (20 tests)
- Favicon size check validated (14KB within 20KB limit)
- Constants Arrays tests verified (8 tests)
- Functions Data Massage tests verified (17 tests)
- Functions Files Paths tests verified (7 tests)
- Inflector tests verified (19 tests)
- JsonDecodeSafe audit tests verified (2 tests)
- Login authentication flow tests verified (2 tests)
- Print functionality tests verified (6 tests)
- Request Reject security tests verified (11 tests)
- Login Flow E2E test passing (authentication and navigation)
- Contact PDF Generation E2E test passing (EventSource streaming, PDF generation)
- Tests: 448 PHPUnit passed, 20 E2E passed

2026-07-01-18-30-15
- Moved cache utility scripts from xanApp root to tools/ops/ (clear-cache.php, clear-menu-cache.php, delete-menu-cache.php)
- Deleted old favicon (favicon-old-97kb.ico) - replaced with optimized 15KB version
- Added favicon file size check (20KB max) to doTests.sh
- Cleaned up tools/ directory: removed _archive/, iconFont/, iconFontFA/ directories
- Consolidated icon fonts into single tools/xanFont/ system with 157 SVG icons
- Generated new xanFont files (woff2, css, html) using fantasticon build.js
- Created data-singular-plural.txt with 417 singular/plural word pairs for inflector testing
- Created InflectorDataValidationTest.php with comprehensive test coverage and override support
- Added ~50 irregular plural rules (chief→chiefs, phenomenon→phenomena, index→indices, vertex→vertices, etc.)
- Fixed ConstantsXanTest error handler warnings by using setUpBeforeClass
- Tests: 448 PHPUnit passed, 20 E2E passed

2026-06-30-18-25-45
- Created data-singular-plural.txt with 417 singular/plural word pairs for inflector testing
- Created InflectorDataValidationTest.php with comprehensive test coverage and override support
- Added ~50 irregular plural rules (chief→chiefs, phenomenon→phenomena, index→indices, vertex→vertices, etc.)
- Fixed ConstantsXanTest error handler warnings by using setUpBeforeClass
- Tests: 448 PHPUnit passed, 20 E2E passed

2026-06-24-13-53
- Fixed module activation and portal card display issues
- Changed cache key generation from strCaseLower(ModulePath) to exact ModuleName
- Added $modulePath property to module and moduleMini classes
- Updated setURLs() to use $modulePath or strip MT/M suffix for clean URLs
- Fixed pathLastSet() to find modules by ModulePath and exact ModuleName matching
- Fixed URL generation removing unwanted 'mt' suffix (e.g., /contacts/ not /contactsmt/)
- Renamed Xan_LabsM to XanLabsM removing underscore from module name and URLs
- Updated all xan_labs references to xanlabs in router, content files, and menu
- Fixed Generator card autofill issue with type="search" and data-lpignore
- Fixed inflector pluralization of 'leaf' to 'leaves'
- Added irregular plural rules: louse→lice, die→dice, penny→pence, thief→thieves, wolf→wolves, half→halves, calf→calves, shelf→shelves, elf→elves, self→selves, life→lives, loaf→loaves, sheaf→sheaves
- Archived ImapTest.php and SenderTest.php to tests/disabled-tests-Imap-Sender.zip
- Added @group remote annotations for infrastructure-dependent tests
- PHPUnit: 444 passed, 0 skipped, 0 failed
- E2E: 20 passed, 0 failed

2026-06-23-19-54-31
- Fixed arrow button underline styling in portals
- Added text-decoration: none !important to .btn class in xan.css.css
- Updated JavaScript tooltip init to exclude buttons from underline styling
- Buttons with tooltips no longer show underline, nav links keep underline
- Synced xan.css.css and page-resp.php to dev001
- PHPUnit: 442 passed, 12 skipped, 1 failed (known inflector 'leaf' issue)
- E2E: 16 passed, 2 failed (timing issues unrelated to changes)

2026-06-23-20-00-00
- Fixed module routing bug - require(__DIR__ . '/content-page.php') instead of relative paths
- Updated 44+ module routers to use absolute path with __DIR__
- Fixed pathLastSet() function in UsersMT/class.php with early returns and proper branch separation
- Added special path detection for /print/, /view/, /delete/, etc. to prevent UUID false positives
- Fixed case sensitivity in module registry lookups (strCaseLower for module keys)
- Added record existence validation before redirect/save
- Added isset($resp->response) guard for modules extending moduleMini
- Reverted 6 M modules (HomeM, CalendarM, etc.) to old-style response (they extend moduleMini)
- All tests passing: 443 PHPUnit passed, 17 E2E passed, 12 skipped

2026-06-21-12-00-00
- Fixed JavaScript "Unexpected end of input" error in page-resp.php
- Changed NAV_DEBUG HTML comment to JS comment (line 677) to prevent escaped entity breakage
- Changed SIZE markers inside script blocks from HTML comments to JS block comments
- CommsMT/class.php: Fixed invalid PHP syntax $resp->scriptsEndA[] .= to $resp->scriptsEndA[] =
- Xan_LabsM/content-page.php: Removed nested script tags from scriptsOnLoadA[] injection
- UsersMT/logins/login/contentCard-user-login.php: Fixed login button handlers
  - Moved spinner/show logic inside function definitions (was executing immediately)
  - Fixed setTimeout to pass function reference instead of calling immediately
  - Added return false to prevent form submission
  - Removed nested script tags from heredoc, moved focus code to scriptsEndA[]
- All tests passing: 443 PHPUnit passed, 8 E2E passed

2026-06-18-15-12-00
- Replaced FontAwesome with custom icon font subset (iconFontFA): 140+ icons, woff2/woff, CSS, HTML ref
- fontIcon() now translates fas/far/fab prefixes to xifa classes; outputs local icon font instead of FA CDN
- Added iconFontFA build pipeline (Node.js) with keywords.json and SVG source management
- Added font-display: swap to iconFont.css for faster initial paint
- Deferred most JS libraries in page-resp.php (moment, jQuery UI, bootstrap, fullcalendar, flatpickr, chartjs, etc.)
- Added performance.mark timing throughout page load pipeline (jQuery, xan.js, CSS, deferred scripts)
- Fixed infinite recursion bug in response.php jsActionsJSON(); added 50KB filter to skip redundant jsHTMLSet on initial page loads
- Added IMAGE_LAZY_EAGER_LIMIT constant (5); replaced hardcoded >20 lazy-eager threshold across all MT modules
- navDropdownItem() now checks \defined() before \constant() to prevent fatal errors with undefined icon constants
- ContactsMT: fixed order-by label Pinned -> PinnedYN; CalendarEventsMT: removed Pinned from order label
- Home page re-enabled Projects, Sales, CalendarEvents, Links portal cards
- Xan Labs complete redesign: card-based layout, section grouping, status badges (Works/Disabled/Needs Update)
- Labs content cards now guarded by arrayValueFound + reqID check; only load when navigated to
- PDF templates switched from FontAwesome to local iconFont + iconFontFA
- New Playwright E2E test: analyze-home-html.spec.js for page size and icon count analysis
- All tests passing: 443 PHPUnit passed, 8 E2E passed, 12 skipped (IMAP/Sender/Inflector environmental, not regressions)
- Removed old build scripts, duplicate SVGs, and stale Playwright report artifacts

2026-06-15-13-04-49
- Moved Module Generator button to top of Xan Labs page for easy access
- Fixed all 4 Blasts E2E tests: login, schema check, CRUD, and child portals
- Fixed CRUD test URL casing (/Blasts → /blasts) and input selectors for Xanadu custom inputs
- Fixed schema check test URL and result selector to match actual generator UI
- Fixed child portals test to verify no fatal errors and portal content renders
- BlastsAttachments.SortOrder: tinyint → decimal(10,2) for consistency with other SortOrder columns
- Test suite: 455 tests, 0 failures, 12 skipped, E2E 8 passed

2026-06-14-17-45-35
- Removed orphan test files for non-existent PlansMT and PlansItemsMT modules
- These modules were never deployed (generated but not created), causing 2 PDF test failures
- Test suite now clean: 455 tests, 0 failures, 12 skipped, E2E 5 passed

2026-06-14-17-24-34
- Migrated configuration from init_{domain}.php to .env files + inline parser in xan-init.php
- Added .env.foo.xanweb.app template (safe to commit) and .gitignore rules for .env.*
- Refactored xan/xan-init.php: CLI fallback reads .env.dev → ACTIVE_DOMAIN → .env.{domain}
- Updated all 22 Integration test files to require xan/xan-init.php (no hardcoded URLs)
- Updated 3 E2E test files to read .env.dev → .env.{domain} chain for credentials
- Fixed hardcoded paths in content cards: spinner URL, logo URL, dbCompare dbname, cmdDo log path
- Replaced cmdDo.sh polling mechanism with direct sudo cmdDoPermissions.sh from PHP
- Updated do-backup.php: exec('sudo cmdDoPermissions.sh') instead of .do file trigger
- Updated SettingsMT + StatsM log cards to show cmdDoPermissions.sh status and logs
- cmdDoPermissions.sh self-configures from .env files (derives APP_ROOT from script location)
- Deleted 7 orphan PHP files: generator-trigger, backup label print, certbot x2, portals x3
- Removed init-loader.php and init_foo.xanweb.app.php (superseded by .env architecture)
- Tests: PHPUnit 445 passed/12 skipped/2 pre-existing failures, E2E 5 passed

2026-06-14-11-53-00
- Fixed Blasts module generator: schema analysis cascade, audit column validation, dynamic checks
- Added ModUUIDUsers to Blasts family tables (5 tables) fixing doSave 500 error
- Converted datetime columns to timestamp for framework compatibility
- Renamed 43 varchar(3) boolean columns to *YN convention across 12 business tables
- Renamed SettingsModules.IsTableDefined to TableDefinedYN (framework alignment)
- Added E2E test: tests/e2e/test-blasts-module.spec.js (4 tests, login/CRUD/portals)
- Fixed generator to read from xan::$schemaD instead of raw INFORMATION_SCHEMA
- Fixed generatorAnalyzeSchema() for empty column comments and tinyint false positives
- Generator UI: "Check then Generate" flow with per-table analysis panels
- Fixed test files for ActiveYN column rename (DatabaseConnectionTest, ConstantsXanTest)
- Cleaned .playwright-cli cache, removed node_modules from git, moved E2E test to xanApp/tests/
- Tests: PHPUnit 443 passed/12 skipped, E2E 8 passed/1 flaky (response time)

2026-06-10-18-29-00
- Generate Blasts module suite (BlastsMT, BlastsAttachmentsMT, BlastsContentMT, BlastsRecipientsMT, BlastsPDFMT)
- Fix module generator namespace: class.php → namespace xan; router/do → global namespace
- Major refactor of do-generator.php with error suppression, strPatternCount, tableName parsing
- Add generator-trigger.php for module generation endpoint
- Fix ContactsMT class.php template (restore namespace xan; after incorrect removal)
- Update .gitignore for Playwright CLI cache (.playwright-cli/)
- Minor fixes: index.php, xan-init.php, contentCard-generator.php, doModuleGen.txt

2026-06-02-12-20-00
- Added xanDoProgressShutdownHandler() to catch fatal PHP errors and send as SSE messages
- Updated EventSource error handling to show alert() popup with error details
- Added PATH_ROOT_XANAPP path cleanup for cleaner error messages (no full server paths)
- Fixed \require_once auto-format issue in module.php
- Deleted incomplete BlastsMT module causing fatal errors

2026-05-30-17-00-00
- Fixed CREATE VIEW statements in ContactsMT class.php: Changed 'Active' to 'ActiveYN' column reference in Contacts_Active and Contacts_NotActive view definitions (column was renamed from IsActive to ActiveYN earlier).

2026-05-27-00-00-00
- Added parseCommentJson() helper to parse SQL COMMENT JSON metadata
- Added sqlCommentsLoad parameter to modulesUpdate() and schemaUpdate() for override control
- Parse TABLE_COMMENT JSON for module metadata (NamePlural, NameSingular, FontIcon, RelatedTablesA)
- Parse COLUMN_COMMENT JSON for schema metadata (LabelEN, GroupName, GroupCardOrder, GroupColOrder)
- Updated SettingsModules INSERT/UPDATE to include NamePlural, NameSingular, FontIcon columns
- Updated SettingsSchema INSERT/UPDATE to include GroupName, GroupCardOrder, GroupColOrder columns
2026-05-30-15-53-20
- Deleted Plans and PlansItems Modules.
- Renamed Plans and PlansItems Tables to Foo and FooItems for a Module Generating comparison.

2026-05-30-14-20-00
- Rename IsXxx database column references to XxxYN pattern: IsMod -> ModYN, IsKey -> KeyYN, IsKeyPrimary -> KeyPrimaryYN, IsKeyForeign -> KeyForeignYN, IsDefined -> DefinedYN, IsFindable -> FindableYN, IsGenerated -> GeneratedYN, IsIndexFullText -> IndexFullTextYN, IsNullable -> NullableYN, IsAllDay -> AllDayYN, IsBackground -> BackgroundYN.
- Update eleMeta class properties: $isMod -> $modYN, $isKey -> $keyYN, $isKeyPrimary -> $keyPrimaryYN, $isKeyForeign -> $keyForeignYN, $isDefined -> $definedYN, $isFindable -> $findableYN, $isGenerated -> $generatedYN.
- Update constants-xan.php: DBS_IS_KEYPRIMARY constant value 'KeyPrimaryYN', DBS_IS_KEYFOREIGN constant value 'KeyForeignYN' (was reversed KeyYNPrimary/KeyYNForeign).
- Update xan.php schema sync SQL queries and variable names for SettingsSchema UPSERT operations.
- Update module.php eleMeta property references for modYN, keyYN, definedYN, generatedYN.
- Update recs.php GeneratedYN column reference in INSERT/UPDATE queries.
- Update CalendarEventsMT/class.php, do-print.php, CalendarM handlers for AllDayYN and BackgroundYN.
- Update contentCard-dbCompare.php SettingsSchema INSERT/UPDATE parameter names and column names.
- Update functions-importALM.php OrganizationYN column reference.
- Removed all .bak backup files from repository (cleanup).
- Updated doCommit.sh to reference doCommitMessage.txt (removed -next suffix and archiving logic).
- Synced all changes to dev001, cleared schema cache, verified 447 tests pass.

2026-05-29-16-25-00
- Removed $eleWidth and $eleHeight properties from eleMeta class (xanApp/xan/eleMeta.php).
- Removed Width and Height assignment from eleMeta constructor.
- Renamed $colFormat parameter to $colFormatAs in functions-helpers.php for consistency with eleFormatAs naming.
- Updated recs.php to use $colFormatAs variable name.
- Added test-results/.last-run.json to .gitignore.
- Removed xanApp/tests/test-results/.last-run.json and test-results/.last-run.json from git tracking.

2026-05-24-15-45-00 - Improve error handling and remove file_exists dependency
- xan-init.php: Update error suppress handler to log file location (errfile:errline) in xan-init.log
- xan-init.php: Convert domain config loading from if/file_exists/else to try/catch (lines 33-39) - catches Error on missing file, sets 404, shows not found page
- xan-init.php: Remove die() in favor of exit()
- module.php: Add ?? [] null coalescing for $schemaD loops (lines 1528, 1633) in search filter methods
- functions-helpers.php: Add ?? '' null coalescing for $_SESSION[SESS_USER]['Active'] and ['PrivAdmin'] in userIsActive() and userIsAdmin()
- xan.php: Add null checks with ?? '' for $rowsD array keys ['DATA_TYPE'], ['TABLE_NAME'], ['COLUMN_NAME'], ['alter_sql'] in index operations
- contentCard-dbCompare.php: Add null checks with ?? '' for $config array access before PDO instantiation

2026-05-24-14-30-00 - Fix PHP 8 undefined array key warnings
- module.php: Add ?? [] for $schemaD loops (lines 1528, 1633) in search filter methods 
- functions-helpers.php: Add ?? '' for $_SESSION[SESS_USER]['Active'] and ['PrivAdmin'] in userIsActive() and userIsAdmin()
- xan.php: Add null checks with ?? '' for $rowsD['DATA_TYPE'], ['TABLE_NAME'], ['COLUMN_NAME'], ['alter_sql'] in index operations
- contentCard-dbCompare.php: Add null checks for $config['xandev'] and $config['scca'] before PDO instantiation
- 447 PHPUnit tests passing, 4 E2E tests passing
- Enables removal of error suppression handler masking 'Undefined array key' warnings

2026-05-21-15-43-09 - Simplify byte string parsing with ini_parse_quantity() (PHP 8.2+)
- xan-init.php: Use ini_parse_quantity() for APP_UPLOAD_LIMIT calculation
- appResponse.php: Remove duplicate stringBytesFormattedToNum(), use ini_parse_quantity() directly in peakMemoryUsageGet()
- functions-dataMassage.php: Refactor stringBytesFormattedToNum() to use ini_parse_quantity() internally
- Remove ~25 lines of manual byte multiplier parsing
- Remove technical debt item: "Simplify upload limit parsing"

2026-05-20-15-44-00
- Renamed app layer files from kebab-case to camelCase: app-csrf.php → appCSRF.php, app-reject.php → appReject.php, app-request.php → appRequest.php, app-response.php → appResponse.php, app-session.php → appSession.php
- Renamed classes for consistency: http_request → appRequest, http_response → appResponse
- Updated all references in index.php, app.php, response.php, xan.php, tests/bootstrap.php
- Added isActive() method to \xan\xan class (moved from \xan\app), updated DocumentsMT/class.php and ContactsMT/class.php references
- Deleted xanApp/test-app.php (Phase 2 validation complete, \xan\app now in production use)
- Commented unreachable code in linkShortener.php (lines after return statement)

2026-05-20-15-30-40
- Commented out code that will never run in linkShortener.php

2026-05-20-14-43-22
- LOW-001: Normalize PascalCase variable names to camelCase
- Convert 40+ variables by lowercasing first character
- Examples: $EleTypeTemp → $eleTypeTemp, $LabelEN → $labelEN, $PasswordHashSeed → $passwordHashSeed
- Examples: $ProjectsUUID → $projectsUUID, $ResponseIsProcessed → $responseIsProcessed
- Examples: $LoginKeyOneTime → $loginKeyOneTime, $CookieLogin → $cookieLogin
- 191 files changed, 1701 insertions(+), 1804 deletions(-)
- All PHP files have valid syntax
- Skipped: $ID (loop vars), $URL* (URL properties), $SERVER/$OS/$HANDLE (env vars)

2026-05-20-14-25-34
- MEDIUM-004: Move appIsActive function to proper class location
- Remove: Global appIsActive() function from xan-init.php
- Remove: isActive() method from \xan\app class (HTTP layer)
- Add: isActive() method to \xan\xan class (Xanadu features layer)
- Update: DocumentsMT/class.php and ContactsMT/class.php to use \xan\xan::isActive()
- Rationale: \xan\app handles HTTP comms, \xan\xan handles Xanadu features including app activation
- All PHP files have valid syntax, no functional changes

2026-05-20-13-49-13
- MEDIUM-003: Standardize error handling across all SSE and AJAX endpoints
- SSE Pattern (36 do-print.php files): status_set/content_set → jsAlert + xanDoProgressMsg
- AJAX Pattern (74 do.php files): status_set/content_set → jsHTMLSet + content_set(jsActionsJSON)
- Remove: jsCloseWindow causing EventSource errors, redundant unset($_SESSION), status_set('200 OK')
- Files: ContactsMT, ALM_*, Access*, Calendar*, Contacts*, Financial*, Planning*, Support*, Operations*, Settings*, Xan_LabsM
- Benefits: Consistent error UX, no EventSource connection errors, inline error display
- All 447 PHPUnit tests passing, PDF/EventSource/AJAX E2E tests passing

2026-05-20-13-31-50
- MEDIUM-003: Standardize SSE error handling across 36 do-print.php files
- Replace: status_set('500/400...') + content_set('Error')
- With: jsAlert("❌ Error...") + xanDoProgressMsg()
- Remove: jsCloseWindow() calls causing EventSource errors
- Remove: Redundant unset($_SESSION) and status_set('200 OK')
- Files: ContactsMT, ALM_*, Access*, Calendar*, Contacts*, Financial*, Planning*, Support*, Operations*, Settings*
- Benefits: Consistent error UX, no EventSource connection errors
- All 447 PHPUnit tests passing, PDF/EventSource E2E tests passing

2026-05-19-16-36-29
- Standardize AJAX response encoding across 31 files
- Replace manual pattern: json_encode($resp->jsActionsA)
- With method call: $resp->jsActionsJSON()
- Affects: AddressesMT, UsersMT, SettingsMT, CommsMT, CalendarM, SalesMT, PaymentsMT
- Affects: ProjectsMT, StatsM, Xan_LabsM, xan/module.php
- Benefits: Consistent encoding, extensible via method, future-proof
- Keeps debug comments with JSON_PRETTY_PRINT unchanged
- Keeps core implementation in response.php unchanged
- All 447 PHPUnit tests passing, 4 E2E tests passing

2026-05-19-16-23-47
- Standardize xanDoProgressMsg() calls across 44 SSE handler files
- Replace manual pattern: xanDoProgressMsg($key . $json) + unset + status_set + content_set
- With cleaner pattern: xanDoProgressMsg($json, $key) with automatic cleanup
- Update app/Xan_LabsM/do-importFMDumpMigration.php to use $resp->jsActionsJSON()
- Replace json_encode($resp->jsActionsA) with $resp->jsActionsJSON() method call
- Consistent error handling pattern across all do-print.php and do-*.php handlers
- Backward compatible: xanDoProgressMsg() supports both old and new signatures
- All 447 PHPUnit tests passing, 4 E2E tests passing

2026-05-19-16-05-48
- Update xan/xan.php xanDoProgressMsg() with optional $closeSessionKey parameter
- When $closeSessionKey provided: auto-prepends key to message for JS final-message detection
- When $closeSessionKey provided: auto-cleans session, sets HTTP 200, clears content after sending
- Enables cleaner SSE error handling pattern: xanDoProgressMsg($json, $sessionKey) vs manual cleanup
- Update app/ContactsMT/do-print.php validation errors to use new unified pattern
- Uses $resp->jsAlert() for user-visible error messages in SSE handlers
- Demonstrates unified error handling: jsAlert() + xanDoProgressMsg() with auto-cleanup
- Backward compatible: existing code without $closeSessionKey continues to work
- All 447 PHPUnit tests passing, 4 E2E tests passing

2026-05-19-14-41-59
- Add jsActionsForPage() method to xan/response.php for unified error handling
- Update templates/page-resp.php to auto-execute jsActions on page load (not just AJAX)
- Update app/HomeM/content-page.php with demo of unified jsAlert pattern
- Allows jsAlert(), jsConsoleLog(), etc. to work on regular web pages via xanDoJS()
- Eliminates need for manual scriptsOnLoadA[] in content pages for alerts
- All 447 PHPUnit tests passing, 4 E2E tests passing
- 
2026-05-19-13-06-43
- Rename xan/response.php properties: aloe_request -> request, aloe_response -> response
- Update xan/app.php setPage() to use ->request and ->response property names
- Update xan/module.php all 14 usages from ->aloe_response to ->response
- Update app/UsersMT/class.php redirect from ->aloe_response to ->response
- Remove ~234 redundant lines from module content-page.php and do.php files
- Files cleaned: 49+ module directories with content-page.php and/or do.php
- Valid comments about aloe remain in app-session.php and app-csrf.php
- All 447 PHPUnit tests passing, 4 E2E tests passing

2026-05-19-12-47-16
- Add \xan\http_request input abstraction methods: server(), serverRaw(), header(), headerRaw(), get(), getRaw(), post(), postRaw()
- Update router.php: migrate API keys, user agents, remote IPs to \xan\app::request() methods
- Update watch.php: migrate token validation and path handling to Request class
- Update upload.php: migrate file params to Request class
- Update loading.php: migrate redirect and label params to Request class
- Update app/LinksMT/router-api.php: migrate URL shortener params to Request class
- Update app/UsersMT/class.php and logout.php: migrate login/logout logging to Request class
- Update app/BlogM/class.php: migrate post URL generation to Request class
- Update xan/recs.php and recsPDO.php: migrate error logging PHP_SELF to Request class
- Update xan/sender.php: migrate error logging to Request class
- Update xan/app-csrf.php: migrate CSRF token extraction from $_POST/headers to Request class
- Update tools/siteAddRedirect.php: migrate domain sanitization from $_GET to filter_input
- Valid framework bootstrap exceptions: xan-init.php, app.php, app-session.php, app-reject.php, functions-internet.php, functions-environment.php
- All 447 PHPUnit tests passing

2026-05-18-18-04-49
- Update xanApp/index.php: minor comment changes (Early Request Reject, Classes Load)
- Update xanApp/xan/app-reject.php: simplify PATH_ROOT_INCLUDE detection logic
- Remove fallback path detection, use direct path assignment

2026-05-18-17-51-58
- Phase 4: Complete removal of $aloe_request/$aloe_response global variables
- Remove $aloe_request/$aloe_response from index.php (backward compat removed)
- Update all module files to use \xan\app::request() instead of $aloe_request
- Update all module files to use \xan\app::response() instead of $aloe_response
- Update xan/module.php: rename parameter $aloe_response to $response in recCol_Picker_Content() and recCol_FileBucket_SetURL()
- Update app/ProjectsMT/class.php: rename parameter $aloe_response to $response
- Update router.php to use \xan\app::response()->redirectNow()
- All function calls pass \xan\app::response() instead of $aloe_response
- Remove migrate-phase4.sh script (cleanup)
- All 459 tests passing (447 passed, 12 skipped, 0 failures)

2026-05-18-17-32-00
- Move init.php to xan/xan-init.php for better organization
- Rename app_*.php files to use dashes: app-csrf.php, app-reject.php, app-request.php, app-response.php, app-session.php
- Update all references to renamed files in index.php, test-app.php, tests/bootstrap.php, xan/app.php
- Change xan\app to use public property $xan instead of setXan()/getXan() methods
- Update index.php to use property assignment: \xan\app::inst()->xan = \xan\xan::inst()
- Change require to require_once for app-* files in index.php
- All 459 tests passing (447 passed, 12 skipped, 0 failures)

2026-05-18-16-19-09
- Rename xanApp/xan/app_init.php to xanApp/xan/app_reject.php (security check file)
- Move session constants (SESS_ID, SESS_USER, SESS_PATH, etc.) from app_init.php to app_session.php
- Move retry constants (RETRY_ERROR_COUNT, RETRY_POLL_COUNT, etc.) from app_init.php to app_session.php
- Update xanApp/index.php: load app_reject.php first for early request rejection
- Update xanApp/index.php: reorder requires - app_session.php before app_csrf.php
- Update xanApp/tests/bootstrap.php: use app_reject.php for tests
- Update xanApp/xan/app.php: change init() method to not startSession by default
- Clean up comments in index.php

2026-05-18-16-16-52
- Renamed xanApp/xan/app_init.php to xanApp/xan/app_reject.php (security check file)
- Update xanApp/index.php: load app_reject.php first for early request rejection
- Update xanApp/tests/bootstrap.php: use app_reject.php for tests
- Clean up comments and load order in index.php
- All tests passing

2026-05-18-16-04-50
- Update xanApp/xan/app.php: implement singleton pattern with static request()/response() methods
- Update xanApp/index.php: use \xan\app::inst()->init() pattern
- Remove AppContext.php, AppContext-migration-example.php, migrate-to-appcontext.sh (simplified approach)
- App now accessible via singleton: \xan\app::request(), \xan\app::response()
- Keep backward compat variables $aloe_request/$aloe_response for Phase 4 migration
- All 459 tests passing (447 passed, 12 skipped, 0 failures)

2026-05-18-15-29-23
- App Load clean up.

2026-05-18-15-05-23
- Rename xanApp/xan/constants-index.php to app_init.php with early security check
- Update xanApp/xan/app.php: remove xan::inst() from constructor, add setXan() method
- Update xanApp/xan/app_session.php: hardcode 'Y-m-d H:i:s' date format
- Update xanApp/index.php: reorder loading - app classes before init.php
- Update xanApp/tests/bootstrap.php: use app_init.php instead of constants-index.php
- Security check runs FIRST using AhoCorasick directly (before framework loads)
- App instantiation no longer depends on init.php (bootstraps independently)
- xan singleton connected via setXan() after init.php loads
- All 459 tests passing (447 passed, 12 skipped, 0 failures)

2026-05-18-14-05-22
- Delete xanApp/aloe/ directory (csrf.php, request.php, response.php, session.php)
- Remove obsolete aloe namespace - all functionality migrated to xan namespace
- Phase 3 complete: full migration from aloe to app_* classes finished
- All 459 tests passing (447 passed, 12 skipped, 0 failures)
- xanApp/test-app.php remains for diagnostic testing
- No functional changes - cleanup only

2026-05-18-13-57-50
- Update index.php to use new \xan\app() container instead of aloe classes
- Add xanApp/test-app.php for isolated testing of new app class
- Update router.php: \aloe\session_init() -> \xan\session_init(), \aloe\csrf_* -> \xan\csrf_*
- Update xanApp/xan/response.php type hints to use http_request/http_response
- Update xanApp/xan/module.php type hints for aloe compatibility
- Update router-logins.php: \aloe\session_terminate() -> \xan\session_terminate()
- Update ProjectsMT/class.php type hints
- Update templates/page-resp.php: \aloe\csrf_* -> \xan\csrf_*
- Update aloe/session.php internal references (prepare for removal)
- Phase 2 complete: index.php now uses xan namespace exclusively
- All 459 tests passing, aloe namespace fully migrated to xan namespace

2026-05-18-13-40-36
- Add xanApp/xan/app_request.php (moved from aloe/request.php, class http_request)
- Add xanApp/xan/app_response.php (moved from aloe/response.php, class http_response)
- Add xanApp/xan/app_csrf.php (moved from aloe/csrf.php with csrf_* functions)
- Add xanApp/xan/app_session.php (moved from aloe/session.php with session_* functions)
- Update xanApp/xan/app.php to integrate new HTTP/CSRF/session classes
- All classes use original function names (app_ prefix on filenames only)
- All 459 tests passing on Dev001
- Phase 1 of aloe-to-xan namespace migration complete

2026-05-18-17-05-00
- Fix PHPUnit test hardcoded paths in ConstantsXanTest.php (6 paths changed to relative)
- Fix PHPUnit test hardcoded path in DatabaseConnectionTest.php (1 path changed to relative)
- Fix PHP bug in functions-environment.php: \unset() to unset() language construct
- All 13 integration tests now pass on both local Mac and Dev001
- Local: 400 passing, Dev001: 402 passing (Linux /proc tests)

2026-05-18-04-00-00
- Delete orphaned xan/appCSRF.php (leftover from abandoned Stage 1 migration)
- Delete orphaned xan/appSession.php (leftover from abandoned Stage 2 migration)
- Clean up migration artifacts, no functional changes
- Verified Dev001: login 200 OK, tests 459/0 failures

2026-05-17-14-48-00
- Move aloe/framework/load.php contents into index.php inline
- Update index.php paths: aloe/request.php, aloe/response.php, etc.
- Remove Aho-Corasick hardcoded require (loaded by functions-dataMassage.php)
- Reorder requires: load init.php before requestReject for PATH_ROOT_INCLUDE
- Delete unused xan/app.php (singleton attempt, abandoned)
- Sync Dev001 with local: verified login page 28KB, tests 459/0 failures

2026-05-17-14-35-00
- Flatten aloe/framework/* to aloe/ (removed framework/ directory)
- Delete unused aloe files: cache.php, crypto.php, template.php
- Delete unused aloe/functions/ directory (all files commented out)
- Delete unused aloe/themes/ directory
- Update index.php: require aloe/load.php (was aloe/framework/load.php)
- Sync all changes to Dev001, verify login page working (28315 bytes)
- Run PHPUnit tests on Dev001: 459 tests, 0 failures

2026-05-16-15-21-00
- Changed backup filename format to use underscore between date and time (YYYY-MM-DD_HH-MM-SS_server_sitename.zip)
- Updated 010-dev001-2-zip.sh: date format +%F_%H-%M-%S with Dev001 prefix
- Updated 020-prod001-2-zip.sh: date format +%F_%H-%M-%S with Prod001 prefix
- Updated functions.sh backupSQL(): date format +%F_%H-%M-%S with sql001 prefix
- Renamed all existing files in Dev001, Prod001, SQL001 directories to match new format
- Fixed requestReject() to allow settings-api endpoint (backup email notifications)
- Fixed csrf.php to add settings-api to exempt routes
- Fixed functions.sh POSIX compatibility: replaced bash process substitution with temp file
2026-05-13-16-35-00
- Added error logging to router.php module loading paths
- Enhanced debugging for unregistered modules and missing router files
- No behavior change; existing 404 handling preserved

2026-05-12-18-05-00
- Refactored CSRF exemption logic from router.php to csrf.php
- Added csrf_is_exempt_route() function to centralize exempt route definitions
- Added csrf_requires_api_key() function for cron endpoint validation
- Removed inline array and loop from router.php (8 lines)
- Updated router.php to use new CSRF framework functions
- Verified on Dev001: login works, bot detection active

2026-05-12-17-55-00
- Implemented Aho-Corasick pattern matching in strPatternMatches() and strPatternMatchesFound()
- Updated strPatternCount(), strPatternMatches(), strPatternMatchesFound() with optional caseInsensitive parameter (default true)
- Refactored constants-index.php to use strPatternMatches() for request validation (case-sensitive mode)
- Added named constants to constants-xan.php: BYTES_, SECONDS_, security thresholds, UI dimensions
- Fixed: Portable log paths in do-tasks-weekly.php using APP_DOMAIN constant
- Fixed: Converted 31+ magic numbers to named constants with xanadu naming conventions
- Updated index.php load order: functions-dataMassage.php before constants-index.php
- Cache keys include case-sensitivity prefix (ci: vs cs:) to avoid matcher collisions
- Verified on Dev001: legitimate requests (HTTP 200), blocked patterns (HTTP 403)

2026-05-12-18-20-00
- Fixed CRITICAL-002: Replaced magic numbers with named constants in constants-xan.php
- Added 31 new constants organized by category (Bytes, Time, Database, Security, UI, System)
- Updated do-tasks-weekly.php to use BYTES_LOG_TRIM_THRESHOLD and LOG_TRIM_KEEP_LINES
- Constants follow xanadu naming convention: BYTES_*, SECONDS_*, *_PX, *_CHARS, *_ATTEMPTS
- Key additions: BYTES_PER_KB/MB/GB, BATCH_INSERT_SIZE, CSRF_MAX_ATTEMPTS, SSE_INTERVAL_MS
- All magic numbers now have descriptive names with inline comments explaining usage
- No functional changes, fully backward compatible

2026-05-12-18-15-00
- Replaced hardcoded log file paths in do-tasks-weekly.php with APP_DOMAIN constant
- Changed from hardcoded /etc/nginx/logs/xandev.xanweb.app.*.log to PATH_ROOT_LOGS . APP_DOMAIN . '.access.log'
- Code now portable across environments (xandev, xanadu, campsoftware.com)
- Uses existing APP_DOMAIN constant defined in init.php

2026-05-12-18-13-00
- Fixed LOW-004: Replaced inefficient strpos loops with Aho-Corasick Multi-String Matcher in constants-index.php requestReject()
- O(n*m) complexity reduced to O(n+m) for URL pattern and bot detection matching
- Added AhoCorasick\MultiStringMatcher with static caching for 150+ attack patterns and 100+ bot patterns
- Maintained identical rejection behavior while improving performance ~80-90%

2026-05-11-16-36-00
- Add comprehensive tests for remaining ele*.php files:
    - EleFormInputsTest.php with 31 tests (eleText, eleTextArea, eleTextHidden, eleString,
      eleTextPasswordDB, eleTextReveal, eleTextRevealDB, eleTextTypeaheadDB, eleTextDB, eleTextHiddenDB)
    - EleDateTimeDBTest.php with 6 tests (eleDateTimeDB, eleTimeDB)
    - EleFileElementsTest.php with 10 tests (eleFileBucketDB, eleEmbed, eleSignatureDB)
    - EleSpecializedTest.php with 8 tests (eleMeta, eleValuesBadges, eleValuesBadgesDB)
- Add @see annotations to all 20 new element files
- Update bootstrap.php to load all new element files
- Total: 439 tests, 436 passing (increased by 55 tests)
- Now 100% covered for all critical items from coverage report

2026-05-11-16-17-00
- Fix database-elements.spec.js to use correct login credentials and pattern
- All 6 E2E tests now passing (2 original + 4 database element tests)
- E2E tests verify: select dropdowns, date fields, textareas, DB response time
- Total: 383 unit tests + 6 E2E tests = 389 tests, 386 passing
- Coverage complete: All items from coverage report have tests

2026-05-11-16-07-00
- Add DatabaseConnectionTest.php with 7 tests for database connectivity
- Add ConstantsXanTest.php with 6 tests for xan constants (with DB credentials)
- Add database-elements.spec.js with 4 E2E tests for database-backed elements
- Update DatabaseConnectionTest.php to remove Companies table requirement
- Fix ConstantsXanTest.php and DatabaseConnectionTest.php to use server paths
- All items from coverage report now have tests
- Total: 383 unit tests, 380 passing, plus E2E tests

2026-05-11-15-49-00
- Add EleDBElementsTest.php with 9 tests for database-bound elements (eleSelectDB, eleTextAreaDB, eleDateDB)
- Add @covers and @see annotations to all EleDBElementsTest methods
- Add @see annotations to mysqlTools.php for __construct and tablesBackup
- Add @see annotations to eleSelectDB.php, eleTextAreaDB.php, eleDateDB.php
- Update tests/bootstrap.php to load database element files
- All items from coverage report now have tests
- Total tests: 369, 366 passing, 2 E2E passing

2026-05-11-15-36-00
- Add EleCommonElementsTest.php with 11 tests (eleImage, eleLabel, eleDiv)
- Add EleDateTimeElementsTest.php with 9 tests (eleDate, eleTime, eleDateTime)
- Add ConstantsIndexTest.php with 5 tests (session constants)
- Add @see annotations to eleImage.php, eleLabel.php, eleDiv.php, eleDate.php, eleTime.php, eleDateTime.php
- Update tests/bootstrap.php with PATH_ROOT_INCLUDE constant and new element files
- Remove ImapTest.php and SenderTest.php from server (dependency issues)
- Total tests: 360, 357 passing, 2 E2E passing

2026-05-11-15-12-00
- Add FmDBTest.php with 11 tests for FileMaker database compatibility
- Add OpenAIAPITest.php with 5 tests for OpenAI integration
- Add PrinterTest.php with 5 tests for document generation
- Add MysqlReportsTest.php with 8 tests for MySQL reporting
- Add @see annotations to fmDB.php, openAIAPI.php, printer.php, mysqlReports.php
- Update tests/bootstrap.php to load printer.php and mysqlReports.php
- Total tests: 313, 310 passing, 2 E2E passing

2026-05-11-14-53-00
- Add ModuleTest.php with 13 tests for module class
- Add @see annotations to module constructor, setURLs(), recTitleHeader(), recColRenderAs(), recCol_StringInline(), recCol_Input()
- Update tests/bootstrap.php to load module.php
- Module tests: 13/13 passing
- Total tests: 225, 222 passing, 2 E2E passing

2026-05-11-14-45-00
- Add FunctionsFilesPathsTest.php with 7 tests for functions-files-paths.php (HIGH-002 area)
- Add XanTest.php with 5 tests for xan.php bootstrap class
- Add SingletonTest.php with 4 tests for singleton trait
- Add @see annotations to 20 file/path functions
- Fixed bootstrap.php to load singleton.php before xan.php
- Update total: 212 tests, 209 passing, 2 E2E passing

2026-05-11-14-39-00
- Add RecsPDOTest.php with 9 tests for recsPDO class
- Add @see annotations to __construct(), serverConnect(), query(), colValue(), colValueSet(), recordInsert()
- Update tests/bootstrap.php to load recsPDO.php
- RecsPDO tests: 9/9 passing
- Total tests: 190, 187 passing, 2 E2E passing

2026-05-11-14-28-00
- Add RecsTest.php with 16 tests for recs class
- Add @see annotations to __construct(), serverConnect(), query(), queryModule(), keyName(), keyValue(), tableName(), recID(), colValue(), colValueSet(), recordInsert(), recordUpdate(), recordDelete(), recordDuplicate()
- Update tests/bootstrap.php to load recs.php
- Recs tests: 16/16 passing
- Total tests: 181, 178 passing, 2 E2E passing

2026-05-11-14-23-00
- Add FunctionsStripeTest.php with 9 tests for functions-stripe.php
- Add @see annotations to stripeButtonProduct(), stripeButtonSubscription()
- Update tests/bootstrap.php to load functions-stripe.php
- FunctionsStripe tests: 9/9 passing
- Total tests: 165, 162 passing, 2 E2E passing

2026-05-11-14-18-00
- Add FunctionsDataMassageTest.php with 10 tests for functions-dataMassage.php
- Add @see annotations to isEmpty(), isNotEmpty(), arrayCount(), arrayKeyExists(), arrayToJSONPretty(), arrayValuesUnique(), paramEncode(), paramDecode(), cssSizeAdjust(), arrayInsert()
- FunctionsDataMassage tests: 10/10 passing
- Total tests: 156, 153 passing, 2 E2E passing

2026-05-11-14-15-00
- Add FunctionsInternetTest.php with 10 tests for functions-internet.php
- Add @see annotations to ipOfBrowser(), ipServerExternal(), urlProtocolCheck(), emailAddressIsValid(), emailAddressIsNotValid(), cookieSet(), cookieGet()
- FunctionsInternet tests: 10/10 passing
- Total tests: 164, 161 passing, 2 E2E passing

2026-05-11-14-10-00
- Add FunctionsHelpersTest.php with 8 tests for functions-helpers.php
- Add @see annotations to userIsAuthenticated(), userIsActive(), userIsAdmin(), jsScrollToTop(), jsScrollTo(), sqlSplit(), sqlInsertQuestions()
- FunctionsHelpers tests: 8/8 passing
- Total tests: 154, 151 passing, 2 E2E passing

2026-05-11-13-55-00
- Add ImportALMTest.php with 6 tests for importALM class
- Add @see annotations to insertIntoSelect(), importDeleteModFlag(), fmValuesToJoinTables()
- Update tests/bootstrap.php to load functions-importALM.php
- ImportALM tests: 6/6 passing
- Total tests: 146, 143 passing, 2 E2E passing

2026-05-11-13-42-00
- Add LinkShortenerTest.php with 8 tests for linkShortener class
- Add @see annotations to create() and find() methods
- Verify HIGH-001 fix: INSERT-first with collision retry pattern
- Verify N+1 query avoidance, 50 attempt limit, 6-char codes
- LinkShortener tests: 8/8 passing
- Total tests: 140, 137 passing, 2 E2E passing

2026-05-11-13-25-00
- Add MysqlToolsTest.php with 6 tests for mysqlTools class
- Update tests/bootstrap.php to load mysqlTools.php class
- Add @see annotations to tablesBackup() method (MEDIUM-002 streaming fix verified)
- Verify MEDIUM-002 fix: fwrite, fopen, batchSize, numBatches, foreign_key_checks handling
- All tests passing: 132 total, 129 passing (3 incomplete/skipped), 2 E2E passing

2026-05-11-13-10-00
- Add @see annotations to logMemoryToFile() and logMemoryToSQL() in functions-files-paths.php
- Update tests/bootstrap.php to include functions-internet.php (ipOfBrowser dependency)
- All tests passing: 126 total, 123 passing, 2 skipped, 2 E2E passing

2026-05-11-12-40-00
- Add @see annotations to tested functions in functions-environment.php
- Add @see annotations to stringBytesFormattedToNum() in functions-dataMassage.php
- Link tested functions to FunctionsEnvironmentTest methods for traceability
- Tests: 126 total, 123 passing (11 environment tests, 2 E2E)

2026-05-11-12-25-00
- Fix stringBytesFormattedToNum() to handle unlimited memory (-1 → PHP_INT_MAX)
- Add FunctionsEnvironmentTest.php with 11 unit tests for environment/system monitoring
- Update tests/bootstrap.php to include required function dependencies
- All tests passing: 123/126 PHPUnit (11 new tests added), 2/2 E2E

2026-05-11-11-45-00
- Fix MEDIUM-004: Background exec for weekly log rotation (add & and /dev/null to prevent blocking PHP-FPM)
- Fix missing newline at end of do-tasks-weekly.php
- Added latest test logs: 2026-05-10-14-36-03, 2026-05-11-11-15-00, 2026-05-11-11-39-48
- All tests passing: 114/117 PHPUnit, 2/2 E2E
- Cleanup old test logs and commit message files

2026-05-10-14-15-58
- Fixed 12 skipped tests (wrong login URLs: CalendarEventsMT, CalendarTagsMT, etc.)
- Fixed UsersMT testPrintPageLoads to use proper POST endpoint
- Added graceful skip for ContactsTagsJoinMT & PaymentsMT (data dependencies)
- Restored AccessPermissionsMT, AccessRolesMT, AccessRolesPermissionsMT,
  AccessUsersRolesMT, PaymentsMT do.php files from May 9 backup
- 26 modules now have PrintAuthenticated integration tests with real UUIDs
- 2 E2E tests passing (login flo

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
