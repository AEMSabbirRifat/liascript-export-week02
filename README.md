# One-Click Course Export: LiaScript → PDF + SCORM (Week 02 lesson)

[![LiaScript Export](https://github.com/AEMSabbirRifat/automation-test-1/actions/workflows/automate-liascript.yml/badge.svg)](https://github.com/AEMSabbirRifat/automation-test-1/actions/workflows/automate-liascript.yml)
[![Open the course](https://img.shields.io/badge/Open_the_course-LiaScript-0A66C2)](https://liascript.github.io/course/?https://raw.githubusercontent.com/AEMSabbirRifat/automation-test-1/main/week02_.md)

**Write a lesson once in Markdown. Get a printable handout and an LMS-ready package automatically.**

Teachers often maintain the same lesson in several places: slides, a PDF for students, and a package for the university's learning platform. This repository automates that. A **GitHub Actions** workflow takes a [LiaScript](https://liascript.github.io/) lesson and produces:

- 📄 a **PDF handout**, rendered exactly as students see the course
- 📦 a **SCORM 1.2 package** that can be uploaded to **Moodle, ILIAS or OPAL**

Both files are attached to a versioned **GitHub Release**, so every semester's version stays archived and downloadable.

## 📘 The lesson

[`week02_.md`](week02_.md): **Quantitative Research Questions, Literature Review & Hypothesis Formulation**, week 2 of the Quantitative Research Methods course at Otto von Guericke University Magdeburg. It includes quizzes on question types and variables, embedded videos, and three in-class tasks. → [**Open it interactively**](https://liascript.github.io/course/?https://raw.githubusercontent.com/AEMSabbirRifat/automation-test-1/main/week02_.md)

## ⚙️ How it works

```text
week02_.md ──► GitHub Actions (manual trigger with version tag)
                 │  npm install  (official @liascript/exporter)
                 │  npm run generate-pdf
                 ├─► dist/week02-research-questions-hypotheses.pdf
                 └─► dist/week02-research-questions-hypotheses-scorm.zip
                          │
                          ▼
                 GitHub Release v1.x.x  (both files attached)
```

| File | Purpose |
|---|---|
| [`.github/workflows/automate-liascript.yml`](.github/workflows/automate-liascript.yml) | The CI workflow: Node 20, install, export, publish the release |
| [`scripts/generate-pdf.js`](scripts/generate-pdf.js) | Calls the LiaScript exporter for PDF and SCORM |
| [`package.json`](package.json) | Names the lesson file and output name in one place |

**Run it:** *Actions* → *LiaScript Export* → *Run workflow* → enter a version such as `v1.1.0`.
**Run locally:** `npm install && npm run generate-pdf` (add `-- --pdf-only` to skip SCORM).

## 🔧 2026 update

The first version opened the raw `.md` file in a headless browser, so the "PDF" showed Markdown source instead of the course. The pipeline now uses the **official LiaScript exporter**, which renders the course properly, and it also produces a SCORM package. I also set up a shared config in `package.json`, added a `.gitignore`, and moved to Node 20.

## 🧰 Skills demonstrated

`CI/CD with GitHub Actions` · `Node.js automation` · `Docs-as-code` · `E-learning standards (SCORM)` · `Instructional design` · `Quantitative research methods`

> Same pipeline, different lessons: [automation-test-2](https://github.com/AEMSabbirRifat/automation-test-2) (Week 03, Research Design & Sampling) and [Practice-Course](https://github.com/AEMSabbirRifat/Practice-Course) (minimal template).

---

### 📬 About me

I'm **Sabbir Rifat**, an analyst and quantitative researcher who automates repetitive work: reporting, data flows and, here, course publishing.
Need an automation like this for your team, or hiring for analytics? **[a.e.m.sabbirrifat@gmail.com](mailto:a.e.m.sabbirrifat@gmail.com)** · [LinkedIn](https://www.linkedin.com/in/aemsabbirrifat) · [Portfolio](https://scaleupwithsabbir.github.io/)
