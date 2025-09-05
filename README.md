# AI Resume Analyzer

A lightweight, Vite + React + TypeScript frontend for uploading and analyzing resumes (PDFs). It renders previews, computes ATS compatibility and scoring, and produces short summaries to help job seekers optimize their resumes.

<!-- Badges -->
![TypeScript](https://img.shields.io/badge/language-TypeScript-blue.svg)
![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Build Status](https://img.shields.io/github/actions/workflow/status/<OWNER>/<REPO>/ci.yml?branch=main)

## Table of Contents
- [About](#about)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Technologies / Stack](#technologies--stack)
- [API / Endpoints](#api--endpoints)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Credits / References](#credits--references)

## About

AI Resume Analyzer is a client-focused app that lets users upload PDF resumes, preview pages, run ATS-style compatibility checks, compute resume scores, and generate concise summaries and suggestions — all with a fast, accessible UI.

## Installation

Prerequisites

- Node.js 18+ (LTS recommended)
- npm (or pnpm / yarn)

Clone and install

PowerShell (copy-paste ready)
```powershell
git clone https://github.com/<OWNER>/<REPO>.git
cd ai-resume-analyer
npm install
```

Using pnpm
```powershell
pnpm install
```

Notes

- This project uses Vite. Scripts referenced below are defined in `package.json`.
- If you prefer yarn, replace `npm` with `yarn` in the commands above.

## Usage

Run the app in development mode

PowerShell
```powershell
npm run dev
```

Open the URL Vite prints (typically `http://localhost:5173`).

Build for production

```powershell
npm run build
```

Preview the production build locally

```powershell
npm run preview
```

Typical npm scripts (check your `package.json`):

- `dev` — start Vite dev server
- `build` — production build
- `preview` — preview production build locally

How to use the app

1. Open the app in your browser.
2. Drag & drop or select a PDF resume using the uploader.
3. View page previews and analysis results (ATS score, numeric score, short summary).
4. Review suggestions and export or download results if supported.

## Features

- PDF upload and per-page preview rendering (client-side using pdf.js)
- ATS-style compatibility checks and keyword extraction
- Resume scoring (formatting, readability, keywords)
- AI-generated short summary and recommendations
- Responsive, accessible UI with reusable components (`app/components/*`)
- Client-first processing with optional backend integration

## Technologies / Stack

- Frontend: React + TypeScript
- Bundler: Vite
- PDF rendering: Mozilla pdf.js (worker included in `public/`)
- Styling: CSS (Tailwind may be present if configured)
- Utilities: custom helpers in `app/lib/` (`pdf2img.ts`, `puter.ts`, `utils.ts`)

Developer tools: VS Code / WebStorm, Node.js, npm/pnpm

## API / Endpoints

> This repository is primarily a frontend app. The following endpoints are example contracts you can implement if you add a backend.

POST /api/upload
- Description: upload a resume PDF and return analysis
- Request: multipart/form-data, field `file` (PDF)
- Response (200 JSON):

```json
{
  "id": "string",
  "filename": "resume.pdf",
  "pages": 3,
  "previewUrls": ["https://.../page1.png"],
  "atsScore": 82,
  "score": 7.4,
  "summary": "Short summary text",
  "keywords": ["react","typescript","node"]
}
```

GET /api/resume/:id
- Description: retrieve analysis by id

DELETE /api/resume/:id
- Description: delete stored resume/analysis

Example curl upload

```bash
curl -X POST "https://your-api.example.com/api/upload" \
  -H "Authorization: Bearer <token>" \
  -F "file=@/path/to/resume.pdf"
```

Notes

- The app works fully client-side for previewing and basic analysis. Use these endpoints only if you want server-side processing or persistence.

## Screenshots

Use these images from the `public/images` folder for documentation or README preview:

![Resume preview](public/images/resume_01.png)
![Score card](public/images/resume_02.png)
![Animated scan](public/images/resume-scan.gif)

If images do not render on GitHub, verify paths or move them to the repository `assets` folder.

## Contributing

We welcome contributions.

1. Fork the repository.
2. Create a branch: `git checkout -b feat/your-feature`.
3. Install dependencies and run the dev server.
4. Add tests and documentation for your changes.
5. Open a Pull Request describing your change.

Guidelines

- Follow existing TypeScript types and project conventions.
- Keep changes small and focused.
- Run `npm run build` before opening a PR to ensure the build succeeds.

Code map

- UI: `app/components/`
- Routes: `app/routes/`
- Utilities: `app/lib/`

## License

This project is licensed under the MIT License — see the `LICENSE` file for details.

If a `LICENSE` file is not present, add one with the following content and replace placeholders:

```
MIT License

Copyright (c) <YEAR> <OWNER>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Credits / References

- Built with Vite — https://vitejs.dev
- pdf.js (Mozilla) for PDF rendering
- Icons and images are stored in `public/icons` and `public/images` — verify attribution for third-party assets

---

If you want, I can also add a `LICENSE` file, a simple GitHub Actions workflow for the build badge, or replace badge placeholders with real repo details.
