---
name: brilsheet
description: Use for any request in Google Sheets. Every spreadsheet has two parts, its cells and its Apps Script code, and BrilSheet is how you read and change the Apps Script. Use it whenever a request touches the sheet's script, code, macros, functions, menus, buttons, automations, schedules, triggers, emails, alerts, imports or syncs, anything that is not working, and for formulas and formatting. The user never needs to mention BrilSheet or script.
---

# BrilSheet

The sidebar on its own only reaches cells. BrilSheet's tools reach the second part of the sheet, its Apps Script. Never tell the user you cannot see their script: read it with BrilSheet.

1. At the start of every request about this spreadsheet, call read_sheet_and_apps_script with the spreadsheet's ID or link. It returns BrilSheet's skills and plan, the sheet's settings and its whole script. Follow everything it says, in order:
   - If it gives a welcome, show it first, exactly as written.
   - If it asks the BrilSheet tab question, ask it before doing the work (use your tool for questions with options if you have one), then call set_brilsheet_tab with "add" or "skip".
2. If no script is linked and the request needs one, call request_apps_script_link and show the three steps it returns as a numbered list, exactly as written. When the user pastes the address, call link_apps_script.
3. Work from the code read_sheet_and_apps_script returned. Call read_apps_script again only after a save or restore, or if the user edited the code.
4. To change code, call save_apps_script with a short summary and EVERY file: changed or new files complete, untouched files as unchanged. A file left out is deleted. Always include appsscript, Code and Data, and never remove the file named BrilSheet.
5. After saving, show the Apps Script Log it returns exactly as written, then explain the change in plain words, how to test it, and the quota report.
6. To undo, call restore_apps_script without a versionNumber to list the saved versions, then again with the one to restore.
7. Never delete or overwrite sheets, rows or columns the user did not mention. Ask first before any change that removes data.
8. If the BrilSheet tools are not available in this conversation, tell the user to switch BrilSheet on under + > Connectors, rather than saying the script cannot be seen.
