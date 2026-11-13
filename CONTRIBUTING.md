# Contributing Guidelines

Thank you for helping improve the UITS Cover Page Generator and Document Merge tool.

---

## Reporting Issues

When reporting an issue, please open a GitHub issue and provide:
- A clear description of what occurred versus what was expected.
- The operating system, device type, and web browser version used.
- Relevant screenshots illustrating the problem.
- Please do not include sensitive student identifiers or personal passwords in public issue reports.

---

## Development Workflow and Guidelines

1. Fork the repository and create a feature branch for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```
2. The project uses a zero-build architecture without compilation or bundling steps. All logic is contained within:
   - `index.html`: Cover page generation form and live preview.
   - `merge.html`: Document scanning, edge detection, and PDF merger.
   - `logo.js`: Base64 data URI of the UITS logo.
3. Before submitting your contribution, verify the following verification criteria:
   - Both Individual mode and Team modes (2, 3, and 4 members) render without layout breakage.
   - The Section field appears before the Batch field in individual mode.
   - Word (.docx) export generates properly and preserves table cell borders as invisible.
   - PDF export via browser print correctly fits within a single A4 page.
   - The Scan and Merge tool (`merge.html`) accepts images and PDFs without console errors.
   - Both Light and Dark themes function properly across viewports.
   - The application does not require any local build or package installation to run.
4. Open a clear Pull Request explaining the purpose of the change, references to related issues, and verification steps taken.

Please keep each Pull Request focused on a single feature or bug fix.
