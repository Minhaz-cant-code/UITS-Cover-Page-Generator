# UITS Assignment & Lab Report Cover Page Generator

A client-side web utility designed for students of the University of Information Technology and Sciences (UITS) to generate standardized academic cover pages and merge them with scanned assignment documents into a single submission-ready PDF.

The project runs completely within the web browser without requiring compilation, package managers, or server infrastructure.

---

## Table of Contents

- [Overview](#overview)
- [Key Capabilities](#key-capabilities)
  - [1. Standard Cover Page Generation](#1-standard-cover-page-generation)
  - [2. Individual and Multi-Student Team Submission](#2-individual-and-multi-student-team-submission)
  - [3. Document Scanning and PDF Merging](#3-document-scanning-and-pdf-merging)
- [Usage Instructions](#usage-instructions)
  - [Generating an Assignment or Lab Report Cover](#generating-an-assignment-or-lab-report-cover)
  - [Scanning and Merging Documents with a Cover Page](#scanning-and-merging-documents-with-a-cover-page)
- [Repository File Layout](#repository-file-layout)
- [Local Execution and Testing](#local-execution-and-testing)
- [Security and Client-Side Privacy](#security-and-client-side-privacy)
- [Browser Compatibility and Considerations](#browser-compatibility-and-considerations)
- [Third-Party Dependencies](#third-party-dependencies)
- [Licensing and Intellectual Property](#licensing-and-intellectual-property)
- [Attribution and Acknowledgements](#attribution-and-acknowledgements)

---

## Overview

Academic coursework at UITS requires strict formatting for assignment and laboratory report submissions. Different departments and courses mandate specific cover details, including course codes, teacher designations, and submission metadata. Group projects require presenting two, three, or four students in parallel side-by-side columns. In addition, online submissions frequently require students to scan handwritten assignment pages and combine them with the generated cover page into one cohesive PDF.

This project addresses these needs through two integrated modules:
1. **Cover Page Generator (`index.html`)**: Interactive form providing an instant A4 paper preview, local persistence of student information, and direct export to Microsoft Word (.docx) and PDF.
2. **Scan and Merge Engine (`merge.html`)**: In-browser document scanner with automatic paper border detection, camera perspective correction, contrast enhancement, and PDF concatenation.

---

## Key Capabilities

### 1. Standard Cover Page Generation
- **Flexible Document Classification**: Supports preset options ("Assignment", "Lab Report", "Project Proposal", "Project Report", "Term Paper", "Internship Report", "Thesis Report") as well as arbitrary custom text typed by the user, with optional document numbering.
- **Course Metadata**: Input fields for Course Title, Course Code, and optional Experiment Number.
- **Optional Topic / Title Formatting**: When an optional topic is entered, renders in the standard academic hierarchy (`[Document Type] \n on \n [Topic]`, e.g., **Assignment 1** on Adder and Subtractor). If omitted, displays the standard single document type header.
- **Faculty / Instructor Options (1 or 2 Teachers)**:
  - Supports laboratory courses or theory sessions conducted by either a single instructor or two instructors (e.g., lab course teacher and lab co-instructor).
  - Displays instructors side-by-side in balanced columns under "Submitted to:".
  - Auto-fills Teacher 2's department from Teacher 1 if left empty.
  - Fully integrated into live preview, Microsoft Word export, and PDF generation.
- **Accurate A4 Preview**: Fixed-ratio preview box matching standard A4 dimensions (794 x 1123 px at 96 DPI / 210 x 297 mm) with responsive auto-scaling for mobile and desktop screens.
- **Export Formats**:
  - **Microsoft Word (.docx)**: Generates a structured `.docx` document adhering to the visual template, including exact tab-stops and borderless grid tables for multi-member layouts.
  - **Print / PDF Export**: Built-in print CSS (`@media print`) pre-configured for borderless A4 paper output using the browser's native print engine.

### 2. Individual and Multi-Student Team Submission
- **Individual Submission**:
  - Designed for solo coursework.
  - Fields: Name, Student ID, Semester, Section, Batch, Department, and Date of Submission.
  - Arranged so that Section appears directly before Batch to match departmental submission standards.
- **Team Submission (2, 3, or 4 Members)**:
  - Designed for laboratory groups and joint term papers.
  - Allows selecting 2, 3, or 4 team members.
  - Formats team members in balanced side-by-side columns:
    - Name
    - Student ID
    - Department
    - Section
  - Includes responsive font scaling (15pt for 2 members, 13.5pt for 3 members, 12pt for 4 members) to prevent long student names or 16-digit IDs from wrapping.
  - Two-way data synchronization: Member 1 fields automatically mirror your saved personal information.
  - Smart Department and Section auto-fill: Entering Member 1's department or section automatically populates teammates' fields if blank, while still permitting individual differences.

### 3. Document Scanning and PDF Merging
- **Input Formats**: Accepts camera photos (JPG, PNG, WEBP, and Apple iPhone HEIC), existing PDF documents, and Word (.docx) files.
- **Automated Edge Detection (Auto-crop)**: Uses client-side image processing algorithms (Otsu thresholding and quadrilateral contour detection) to detect document edges on desks and apply bilinear perspective homography to flatten photos into upright A4 pages.
- **Interactive Manual Crop**: Dedicated modal editor allowing manual repositioning of the four corner pins if automatic detection requires correction.
- **Image Enhancement Presets**:
  - **Magic colour**: Whitens uneven backgrounds, normalizes room lighting, and boosts ink contrast.
  - **Grayscale**: Removes colored paper artifacts and provides clean monochrome scans.
  - **Black & white**: High-contrast binary filter for printed text and line art.
  - **Original**: Keeps unprocessed image data.
- **Cover Page Prepending**: Checkbox to automatically render and prepend the UITS cover page as Page 1 of the generated PDF.
- **Page Organization**: Reorder individual pages up or down, remove unwanted pages, and inspect rendered pages in a full-resolution previewer.

---

## Usage Instructions

### Generating an Assignment or Lab Report Cover
1. Open `index.html` in your web browser.
2. Select the document type and specify the assignment or lab number.
3. Provide course details and select either 1 or 2 instructors using the instructor checkboxes.
4. Under "Submitted By", select the number of students (1 for individual, or 2, 3, 4 for a team) using the student checkboxes.
5. Fill in student details. For team submissions, input each teammate's name and ID.
6. Verify the live preview on the right panel.
7. Click "Download Word (.docx)" to obtain an editable Word document, or click "Download PDF / Print" to save as a PDF.

### Scanning and Merging Documents with a Cover Page
1. Complete your cover page fields on `index.html`.
2. Click "Merge with scanned pages (next page) ->".
3. The merge interface will open, automatically loading your cover page data with "Add my cover page first" checked.
4. Drag and drop photographs of your handwritten work or existing PDF files into the upload box.
5. Review the page order and adjust cropping or enhancement filters as necessary.
6. Specify your desired file name and click "Create merged PDF".
7. The compiled document will download directly to your computer.

---

## Repository File Layout

```text
UITS-Cover-Page-Generator/
├── index.html         # Cover page generator form and live preview interface
├── merge.html         # Document scanner, image processor, and PDF merger
├── logo.js            # Base64 data URI of the official UITS logo
├── uits-logo.png      # Source image asset for the UITS logo
├── CONTRIBUTING.md    # Development and contribution guidelines
├── LICENSE            # MIT open source license
└── README.md          # Project documentation
```

---

## Local Execution and Testing

The repository does not require Node.js, npm packages, or build tools. You can run it directly using any standard web browser.

### Direct Execution
Open `index.html` directly from your file manager, or run the corresponding terminal command:

```bash
# On Linux
xdg-open index.html

# On macOS
open index.html

# On Windows
start index.html
```

### Local HTTP Server
If you prefer testing through a local web server:

```bash
# Using Python 3
python3 -m http.server 8000

# Using Node.js
npx serve .
```

Once running, navigate to `http://localhost:8000` in your browser.

---

## Security and Client-Side Privacy

- **Zero Server Uploads**: All image processing, perspective transformations, document parsing, and file compilations are executed purely in client-side memory. No files or student credentials are sent to remote servers.
- **Local Persistence**: Student information is saved strictly in your browser's `localStorage` key (`uits-cover-personal`). You can permanently delete stored information at any time by clicking "Clear saved info".
- **Offline Reliability**: After the third-party CDN libraries are cached on initial page load, the application functions offline without active internet connectivity.

---

## Browser Compatibility and Considerations

- **Recommended Browsers**: Google Chrome, Mozilla Firefox, Microsoft Edge, and Apple Safari.
- **In-App Browser Warning**: Web views embedded inside mobile social media applications (such as Facebook Messenger, Instagram, or Telegram) frequently restrict blob-based file downloads. If accessing the site from a mobile application, use the menu option to "Open in external browser" (such as Chrome or Safari).
- **Word Export CDN**: Generating `.docx` files relies on the `docx` library loaded from a CDN (`unpkg.com`). An active internet connection is needed for the first load to retrieve the script.

---

## Third-Party Dependencies

The application utilizes the following libraries via CDN:
- **docx (v8.5.0)**: Programmatic generation of Microsoft Word (.docx) files.
- **jsPDF (v2.5.1)**: Creation of vectorized PDF documents and page merging.
- **pdf.js (v3.11.174)**: Rendering and extracting pages from existing PDF files.
- **mammoth.js (v1.6.0)**: Converting uploaded Word documents into HTML for visual conversion.
- **html2canvas (v1.4.1)**: Rasterizing HTML blocks to canvas for document extraction.
- **heic2any (v0.0.4)**: In-browser conversion of Apple iPhone HEIC images to standard JPEG.

---

## Licensing and Intellectual Property

- **Source Code**: All underlying code, algorithms, and styling are distributed under the [MIT License](LICENSE).
- **University Trademark and Name**: The name "University of Information Technology & Sciences", the acronym "UITS", and the institution logo (`uits-logo.png` and embedded data in `logo.js`) are the intellectual property of the University of Information Technology & Sciences. These assets are included strictly for legitimate academic coursework by enrolled students and are excluded from the MIT License. If adapting this project for another university, replace these assets with your own institution's identifiers.

---

## Attribution and Acknowledgements

- Architectural layout and workflow inspired by the [BRAC University Assignment Cover Page Generator](https://sayadmahabubmredul.github.io/BRACU-Assignment-Cover-Page-Generator/).
- Word export capabilities powered by the open-source [`docx`](https://github.com/dolanmiu/docx) JavaScript library.
- Built for the student community of the Department of Computer Science and Engineering at UITS.
