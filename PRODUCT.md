# PRODUCT.md — DEV RAJ Thapa Portfolio

> Captured by `/impeccable init` · 2026-11-25

---

## 1. What this product is

A personal developer portfolio for **Dev Raj Thapa**, a Senior Backend Developer & Scalable Systems Architect based in India with 7+ years of experience. The portfolio is a single-page Experience/Persuade surface: it functions as a live CV and hiring pitch. The primary conversion action is a recruiter or technical lead reaching out via the contact form or LinkedIn — or downloading the resume.

---

## 2. The person it represents

| Field        | Value                                                                        |
| ------------ | ---------------------------------------------------------------------------- |
| Name         | Dev Raj Thapa                                                                |
| Handle       | DEV RAJ                                                                      |
| Role         | Senior Backend Developer & Scalable Systems Architect                        |
| Speciality   | Laravel, Node.js, Microservices, API Design, Redis, MongoDB, MySQL           |
| Years XP     | 7+                                                                           |
| Live systems | 15+                                                                          |
| LinkedIn     | [dev-raj-thapa-571645b5](https://www.linkedin.com/in/dev-raj-thapa-571645b5) |
| GitHub       | [dev1191](https://github.com/dev1191/)                                       |
| Resume       | Google Drive (linked in nav)                                                 |

---

## 3. Audience

**Primary:** Technical hiring managers, CTOs, and senior engineering leads at product companies and agencies looking for a backend specialist.

**Secondary:** Potential clients (agencies, startups) needing a freelance architect/developer.

Both audiences are technical. They skim fast, verify via GitHub and live project links, and expect precision. Generic or vague copy loses them immediately.

---

## 4. Mode

**Experience** (primary surface) — the portfolio itself is the artifact. The interface should recede; the work and identity lead.

The landing page also carries **Persuade** intent — it must earn attention and drive one of: resume download, LinkedIn click, or contact form submission.

---

## 5. Surface map

| Section    | ID          | Purpose                                                               |
| ---------- | ----------- | --------------------------------------------------------------------- |
| Navigation | —           | Sticky top bar; brand mark, section anchors, theme toggle, resume CTA |
| Hero       | `#home`     | First impression: name, role, overview blurb, avatar                  |
| Tech Stack | `#about`    | Skill grid + expertise copy + stat cells (7+ yrs, 15+ systems)        |
| Projects   | `#projects` | 6 featured projects with screenshots, tags, live links                |
| Experience | —           | Timeline of 4 roles + 1 education entry                               |
| Contact    | `#contact`  | LinkedIn/GitHub links + message form                                  |
| Footer     | —           | Closing mark                                                          |

---

## 6. Featured projects

| Project                          | Stack                                                    | Live                                                                              |
| -------------------------------- | -------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Ridein — Taxi Booking            | Laravel, Android, iOS, FilamentPHP, MySQL, Redis, Docker | [ridein.in](https://ridein.in/)                                                   |
| Shuttle Bus Portal               | Laravel, Android, Vue.js, Redis, MongoDB, Docker         | [shuttle.ridein.in](https://shuttle.ridein.in/)                                   |
| Affilspark — Affiliate Marketing | Laravel, MySQL, jQuery, Bootstrap                        | [affilspark.com](https://affilspark.com/)                                         |
| OuraRide — Taxi Booking          | Laravel, Android, Vue, MongoDB, Docker, Redis            | [admin.ouraride.sourcemonster.in](https://ouraride.sourcemonster.in/admin/login/) |
| Travel Membership Portal (CRM)   | CodeIgniter, PHP, jQuery, Bootstrap, MySQL               | [royalsclubinternational.com](https://royalsclubinternational.com/)               |
| School ERP System                | CodeIgniter, PHP, MySQL, jQuery, Bootstrap               | —                                                                                 |

---

## 7. Work history

| Period      | Role                     | Company                                |
| ----------- | ------------------------ | -------------------------------------- |
| 2023 — Now  | Senior Backend Developer | Source Monster                         |
| 2020 — 2023 | Senior Node.js Developer | Rigo Tech (India) Pvt Ltd              |
| 2019 — 2020 | Senior PHP Developer     | Milkyway Multidimensional              |
| 2017 — 2019 | PHP / Moodle Developer   | LDS Engineers Pvt Ltd                  |
| 2014 — 2017 | MCA (Masters)            | Indira Gandhi National Open University |

---

## 8. Tech platform

| Layer      | Choice                                  |
| ---------- | --------------------------------------- |
| Framework  | Vue 3 (Composition API)                 |
| Build tool | Vite                                    |
| Styling    | Tailwind CSS 4 (custom `@theme` config) |
| Animations | @vueuse/motion                          |
| Icons      | Lucide Vue Next                         |
| State      | Reactive composables (`useTheme`)       |
| Hosting    | Static (no SSR)                         |

---

## 9. Design system identifier

**"STITCHED"** — components are separated by 1 px gap on a background grid that creates a fine-line border effect. Each module highlights with a primary-color inset border on hover. The aesthetic references high-end technical interfaces: CAD, blueprint software, developer terminals.

Tokens and palette are defined in `src/style.css` and codified in DESIGN.md.

---

## 10. Constraints and content rules

- **No GitHub source** shown for client projects (private repos); live links take priority.
- **Resume is a Google Drive link** — not a local file.
- **Contact form** is currently front-end only (no backend handler wired); it renders but does not send.
- **Avatar image** is a provided photo; do not replace without permission.
- **All project copy is factual** — do not alter or embellish project descriptions without asking.
- **Dark mode is the design intent** — the dark theme (`#131313` background, `#75ff9e` primary) is the signature aesthetic; light mode is a viable alternative, not the primary.

---

## 11. Open gaps (noted, not auto-fixed)

- Contact form has no submission handler (no API, no mailto fallback).
- School ERP project has a placeholder `#` link.
- Mobile "DOWNLOAD RESUME" button in the nav overlay does not link to the resume URL.
- No `<meta>` SEO tags or `<title>` personalisation beyond the Vite default.
- No `404` page.
- No analytics.
