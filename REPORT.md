# AgenticGIS Brazilian Portuguese verification

Base `1e4f70b488824982a835c89c202454ec92dafae7`  
Feature `f0c552ae1d328a56dfb2adb9a8941fbbbffd18ff`

## Runtime results

QGIS 3.34.4 / Qt 5.15.13 on Linux. Each locale smoke row used its own process, isolated settings and the stated OS locale. The smoke checked the Settings button and the first saved default session name.

| QGIS override | OS locale | Observed |
|---|---|---|
| `pt_BR` | `en_US` | Portuguese |
| Disabled | `pt_BR` | Portuguese |
| `en_US` | `pt_BR` | English |
| Disabled | `en_US` | English |
| `fr_FR` | `en_US` | English |
| `pt_PT` | `pt_BR` | English |

The [test log](unittest.log) records 16 passing tests covering catalog completeness, locale precedence, missing/corrupt catalogs, translator lifecycle, session snapshots, result widgets, save filters, Markdown/CSV exports and MCP protocol frames. The MCP test sends initialize, tools/list and a stubbed tools/call through the stdio loop and compares the responses byte for byte in both languages.

Permission cases sent the original raw `Allow once`, `Always allow`, `Deny` and `Allow all GEE tools for this session` choices through the Qt card into the toolkit. The tests check one-time and persisted approval, denial, cancellation, raw model-authored options and rejection of a translated choice used as a raw authorization value. GEE approval survives selecting the same chat, clears on a chat change and cannot be granted by a late reply from the old chat.

The [dock checks](visual.log) and [permission checks](permission-layout.log) passed at 75%, 100%, 150% and 200% in both languages. The dock held 320 px throughout. Permission checks also used 420 px and verified tab focus through the options and cancellation. The permission card scrolls vertically to show all text at larger scales. Settings smoke covered the three connection tabs, external agents, appearance, and stubbed auth states.

The [archive listing](zip-contents.log) contains the tracked TS and QM. The [Plugin Manager log](zip-install.log) records successful ZIP installation, plugin start, translated UI and metadata, and translator removal on unload in a clean profile.

## Source and catalog inventory

Both PyQt 5 and PyQt 6 extracted the same 344 context/source/plural entries. All 344 are finished and zero extracted entries are missing. The tracked Qt 5-generated QM and a Qt 6-generated QM both loaded on Qt 6.4.2 and returned translated text and plurals. The catalog is the literal-by-literal inventory, with each message linked to its source location by the TS format. [Changed files](changed-files.txt)

| Area | Examples |
|---|---|
| Dock and sessions | Settings, ready status, keyboard hints, irreversible deletion warning, and relative time |
| Settings and local diagnostics | Connection tabs, connection/test failure wrappers, CLI scan/login feedback, credential hints and MCP notice |
| Permissions | First-party questions, access reasons and option captions with separate canonical values |
| Activity and result cards | Tool captions, progress, failed/done, counts, chart titles, stats and empty states |
| Save and export | Dialog titles, type filter captions and missing-file messages |
| QGIS Plugin Manager | Localized description and about fields |

Intentional exemptions fall into seven categories: brands and product identifiers, user and model content, provider and terminal diagnostics, machine-facing tool results and logs, protocol names and schemas, model prompts and command arguments, and previously saved user data. These categories include dynamic values and are not counted as catalog entries. Existing schemas, prompts and CLI argument construction remain in English and the plugin adds no runtime dependencies.

## Screenshots

| Flow | English | Brazilian Portuguese |
|---|---|---|
| Dock | [English](dock-en_US.png) | [Portuguese](dock-pt_BR.png) |
| Settings · API | [English](settings-en_US-api.png) | [Portuguese](settings-pt_BR-api.png) |
| Settings · Custom | [English](settings-en_US-custom.png) | [Portuguese](settings-pt_BR-custom.png) |
| Settings · CLI | [English](settings-en_US-cli.png) | [Portuguese](settings-pt_BR-cli.png) |
| Settings · MCP | [English](settings-en_US-mcp.png) | [Portuguese](settings-pt_BR-mcp.png) |
| Settings · Appearance | [English](settings-en_US-appearance.png) | [Portuguese](settings-pt_BR-appearance.png) |
| New session | [English](session-en_US.png) | [Portuguese](session-pt_BR.png) |
| Stats result | [English](result-en_US.png) | [Portuguese](result-pt_BR.png) |
| Permission | [English](permission-en_US-320px-100percent.png) | [Portuguese](permission-pt_BR-320px-100percent.png) |
| Permission · 200% | [English](permission-en_US-320px-200percent-scrolled.png) | [Portuguese](permission-pt_BR-320px-200percent-scrolled.png) |

## Coverage limits

QGIS 4 and QGIS 3.22 were unavailable for runtime testing. QGIS 3.22 exposes the settings API and the patch uses the QGIS PyQt wrappers. PyQt 6 extraction and loading checks cover the catalog only. Live provider, CLI, Earth Engine and processing calls were outside the offline smoke runs. [QGIS 3.22 settings API](https://api.qgis.org/api/3.22/classQgsSettings.html)
