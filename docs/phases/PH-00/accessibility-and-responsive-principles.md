# NetaMonitor PH-00 — Accessibility and Responsive Principles

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-500` to `PH-00-UX-599`

> Principles and acceptance expectations for later phases. This file contains no CSS, tokens, component code or visual design. Final breakpoints, type scale, colour and spacing tokens are defined in PH-02. Breakpoint values below are **design anchors**, not implementation.

## 1. Accessibility

| ID | Requirement |
|---|---|
| PH-00-UX-500 | Target conformance is **WCAG 2.2 Level AA** for every public, account and admin screen. |
| PH-00-UX-501 | Use semantic landmarks and a logical heading order. Each page has one main heading. |
| PH-00-UX-502 | Every control has a visible, programmatically associated label. |
| PH-00-UX-503 | Every interactive element is reachable and operable by keyboard alone, with a visible focus indicator that is not hidden by other content. |
| PH-00-UX-504 | Focus order follows visual and reading order. A skip link is the first focusable item. |
| PH-00-UX-505 | Colour is never the only way to convey meaning. Status uses text plus shape or icon. This applies to evaluation options and evidence status. |
| PH-00-UX-506 | Text and interface component contrast meets AA in light and dark themes, with equal compliance. |
| PH-00-UX-507 | Pointer targets meet the WCAG 2.2 target size minimum, and the design aims for the larger 44 by 44 CSS pixel size, with spacing between targets. |
| PH-00-UX-508 | Every chart has a text or table alternative. Every map-like view has a list alternative. Every informative icon has a text equivalent. |
| PH-00-UX-509 | Dynamic changes (receipt, status change, errors) are announced through live regions. After a submit, focus moves to the confirmation or the error summary. |
| PH-00-UX-510 | Form errors identify the field, state the problem and suggest a fix. An error summary precedes the form. |
| PH-00-UX-511 | Authentication and verification avoid cognitive-test-only steps. Paste into fields is allowed, and help is consistently located (accessible authentication, consistent help, redundant entry avoided). |
| PH-00-UX-512 | Time limits (sessions, codes) are stated, extendable where possible, and never silently discard a draft. |
| PH-00-UX-513 | Motion is minimal, short, and off under a reduced-motion preference. There is no celebratory motion on evaluation. |
| PH-00-UX-514 | Text can be enlarged to 200 percent and reflowed at narrow width without loss of content or function. |
| PH-00-UX-515 | Screen-reader users get the same trust cues as sighted users: provenance, dates, sample sizes and status are text, not image-only. |
| PH-00-UX-516 | The product publishes an accessibility statement and a route to report barriers. |

### 1.1 Verification and assisted use
| ID | Requirement |
|---|---|
| PH-00-UX-520 | The verification flow can be completed without a camera or file upload through the assisted or in-person route. |
| PH-00-UX-521 | Assisted use never lets a helper select the user's evaluation. The evaluation screen is completed by the account holder. |
| PH-00-UX-522 | Plain-language and icon-plus-text support is part of acceptance for the verification wizard and the evaluation module. |

## 2. Responsive principles

Design anchors (to be finalised in PH-02): **XS** 320–479, **SM** 480–767, **MD** 768–1023, **LG** 1024 and above (CSS pixels).

| ID | Requirement |
|---|---|
| PH-00-UX-530 | Mobile first. Every journey completes at 320 CSS pixels with no horizontal scrolling. Data tables are the only exception, and then only with a visible scroll cue and a card alternative. |
| PH-00-UX-531 | Narrow screens use compact navigation of at most five items with search always available. Wider screens add a top bar. A side navigation appears only inside Admin and long profile pages on wide screens. |
| PH-00-UX-532 | Profile sections become a scrollable segmented control on narrow screens with a clear current state, and a sticky tab bar on wide screens. |
| PH-00-UX-533 | Provenance cues collapse to an icon that opens a sheet on narrow screens. The full information stays one interaction away. |
| PH-00-UX-534 | Module A and Module B stack vertically on XS and SM, and sit side by side on LG with equal visual weight and separate headings. They never overlap and are not combined into tabs by default. |
| PH-00-UX-535 | Compare shows one metric group at a time with a pager for up to three people on narrow screens, and a table on wide screens. Row headers persist. A non-comparable row states why. |
| PH-00-UX-536 | Primary actions are reachable by thumb on narrow screens and are not placed where a sticky element hides them. |
| PH-00-UX-537 | Admin is desktop first but usable on tablet. Queues show master/detail on wide screens and drill-in on narrow ones. Admin tables offer column priority and a density choice. |
| PH-00-UX-538 | Orientation is not locked. Content reflows without loss. |
| PH-00-UX-539 | The impersonation banner and the election-period notice stay visible and unobscured at every breakpoint. |
| PH-00-UX-540 | The same content and the same trust cues are available at every breakpoint. Narrow screens re-arrange, they do not remove. |

## 3. Multilingual requirements

| ID | Requirement |
|---|---|
| PH-00-UX-550 | English, Hindi and Marathi are designed from the start for all public tasks and the verification route. |
| PH-00-UX-551 | The language of each piece of content is shown. Original source text is never replaced by a translation. A translation is labelled with its source language and who translated it. |
| PH-00-UX-552 | Switching language preserves the user's place and any unsaved input. |
| PH-00-UX-553 | Labels and buttons accommodate text expansion of at least 40 percent and Devanagari line height. No critical label is truncated and no button has a fixed width that clips text. |
| PH-00-UX-554 | Dates, numbers and currency follow locale. Rupee amounts state the unit (lakh, crore) explicitly. |
| PH-00-UX-555 | Search works across scripts and common spelling variants of names. Result cards show a disambiguating fact. |
| PH-00-UX-556 | Missing translations fall back visibly (labelled) rather than silently showing another language. |
| PH-00-UX-557 | Plain-language checks happen per language, not only in English. |

## 4. Offline, low-data and shared-device boundaries

| ID | Requirement |
|---|---|
| PH-00-UX-560 | Offline access is **public, read-only**. Only previously opened public content may appear, labelled "As of {date and time}", with a stale warning after a threshold (`PH-00-UX-Q06` owner decision; detailed in PH-24). |
| PH-00-UX-561 | Sign-in, verification, evaluation, evidence submission and every admin action are not offered offline and are never queued or shown as sent. |
| PH-00-UX-562 | Identity evidence, admin data, private records and a person's evaluations are never available from a cache. |
| PH-00-UX-563 | Low-data mode: text first, images optional and deferred, no required large downloads for core tasks. |
| PH-00-UX-564 | Shared-device safety: sign-out clears private screen state. The receipt and account screens carry a notice that whoever uses the signed-in session can see them. |
| PH-00-UX-565 | Reconnection after offline never auto-submits anything. Any pending user draft is resubmitted only by an explicit user action. |

## 5. Loading, empty, error and permission principles

| ID | Requirement |
|---|---|
| PH-00-UX-570 | Loading states are shown per module so a slow area does not block the page. |
| PH-00-UX-571 | An empty state explains why (not yet due, not published, not covered) and what the person can do. It never uses warning treatment for absent data. |
| PH-00-UX-572 | Error messages are plain, never expose technical detail, hidden admin areas or another person's data. |
| PH-00-UX-573 | Permission states explain the reason and next step. The only exception is a forbidden admin area, which shows the neutral "not available" page identical to a missing page. |
| PH-00-UX-574 | Rate-limit messages are neutral and non-accusatory. |
| PH-00-UX-575 | Edit conflicts show a difference view and keep the draft. |

## 6. Quality gates for later phases

| ID | Requirement |
|---|---|
| PH-00-UX-580 | Each later phase's design includes an accessibility annotation set: landmarks, headings, labels, focus order, live regions and text alternatives. |
| PH-00-UX-581 | Automated checks (the project's chosen accessibility tooling) are necessary but not sufficient. Manual keyboard and screen-reader passes are part of the independent QA scope. The tooling choice follows the AGENTS.md baseline and is a Development decision. |
| PH-00-UX-582 | A test pass at 320, 768 and 1280 CSS pixels, at 200 percent zoom, is required for each public journey. |
| PH-00-UX-583 | Language checks cover English, Hindi and Marathi for every public journey. |

## 7. Assumptions
- A-13: The target device is a mid-range Android phone on an unreliable connection.
- A-14: Hindi and Marathi translators are available for the pilot (`PH-00-UX-Q05`).

## 8. Dependencies
- PH-02 design system to define tokens and components meeting these principles.
- PH-20 localisation and PH-24 offline detail phases.

## 9. Open questions
`PH-00-UX-Q05`, `Q06`, `Q07` in `ui-design-handoff.md` §6.
