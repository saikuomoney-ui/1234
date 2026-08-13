# PTC Mask Transfer System

Control software repository for the PTC mask transfer system.

This repository is for source-controlled engineering deliverables only. Do not commit raw BOM files, quotations, customer documents, manuals, PDFs, CAD drawings, passwords, temporary exports, or generated build output.

## Repository Layout

```text
.
|- README.md
|- SPEC.md
|- CHANGELOG.md
|- docs/
|  |- requirements/
|  |- sequence/
|  |- io-list/
|  |- bom/
|  `- electrical/
|- plc/
|- hmi/
`- source/
```

## Working Rules

- Keep `main` stable.
- Use branches for implementation work.
- Review changes by pull request before merging.
- Store only sanitized text summaries for BOM, I/O, electrical notes, and requirements.
- Keep original vendor manuals, BOM spreadsheets, PDFs, CAD files, and confidential customer data outside Git.

