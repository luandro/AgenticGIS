# AgenticGIS PR #4 release review

Base: `1e4f70b488824982a835c89c202454ec92dafae7`  
Reviewed follow-up head: `51c8a79706b534f1ee9b2a8b936f9b36e285c4bc`

Claude Code Opus 5.5 reviewed the original implementation and approved the follow-up. The permission card now tags each pending request, drops cancelled or stale answers, and clears queued prompts when leaving the chat. This preserves canonical English choice values and the wire payload. The follow-up also removes the translator when teardown fails, uses the positional QTranslator loader, and uses the QGIS number locale consistently.

- [QGIS 3.34.4 / Qt 5.15.13](review-qgis3.log): 19 offline tests passed.
- [QGIS 4.4.0 / Qt 6.8.2](review-qgis4.log): 19 offline tests passed in the official QGIS desktop image with network access disabled.
- [QGIS 4 desktop ZIP installation](review-qgis4-zip.log): Plugin Manager installed the archive into a clean profile, loaded the Portuguese metadata and dock, and removed the translator on unload.
- [QGIS 4 permission layout and keyboard checks](review-qgis4-permissions.log): all 16 combinations passed in English and Brazilian Portuguese at 320 and 420 px and font scales from 75% through 200%.
- PyQt 5 and PyQt 6 extraction agreed on 344 finished messages. The tracked catalog passed on both runtimes.

The current metadata already declares support through QGIS 4.x. QGIS 3.22 and live provider, CLI, and Earth Engine calls were outside the executed runtime matrix.

[QGIS 4 dock screenshot](qgis4-dock-pt_BR.png) · [QGIS 4 permission screenshot at 200%](qgis4-permission-pt_BR-200percent.png)

QGIS references: [official desktop image](https://github.com/qgis/qgis-docker) · [QGIS 4 plugin migration](https://plugins.qgis.org/docs/migrate-qgis4)
