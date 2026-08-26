# VUM Documentation Template

A LaTeX template for Vanderbilt University Motorsports documentation, built so
that a first-year who has never seen LaTeX can produce a document that looks
like every other document in the archive.

The idea is **evergreen documentation**: files that outlive the person who
wrote them. Every document carries a document ID, a revision history, an
owner, and a review-by date, so two years from now someone can tell at a
glance whether they are reading something current or something stale.

**Background.** The team has lost roughly two decades of accumulated
knowledge because it was never written down. Setups lived in one person's
head, results stayed behind in group chats, and more than one fix has been
rediscovered from scratch. This system exists to rebuild that knowledge. It
is new for everyone, with leads learning it at the same time as
first-years, and nothing here assumes prior familiarity.

**Where to start:**

- **Everyone.** Read `overleaf-intro.tex` (or its PDF) first. It assumes
  no prior knowledge of Overleaf or LaTeX and ends with a hands-on exercise
  of about twenty minutes. Keep `CHEATSHEET.md` open while writing.
- **Leads.** Do the same, then read sections 1, 4, and 5 of this file.
  Section 5 describes the lead-specific responsibilities.

---

## 1. Getting it into Overleaf

**One-time, by whichever lead owns documentation.** Pick one owner. Any
lead can do this, and it needs no more Overleaf knowledge than the intro
guide teaches.

1. Overleaf → **New Project** → **Upload Project** → pick `VUM-doc-template.zip`.
2. Rename the project to `VUM Documentation Template`.
3. Menu → **Copy Project** is how everyone else will use it. If your team has
   an Overleaf group subscription, Menu → **Manage Template** publishes it to
   the group template gallery instead, which is cleaner.

**New to Overleaf or LaTeX:** read `overleaf-intro.tex` before anything
else, either by compiling it or from the PDF in the documentation repo. It
assumes no prior knowledge and ends by walking you through your member
introduction, the first of the two onboarding tasks.

**Every time someone writes a new document:**

1. Open the template project → Menu → **Copy Project**.
2. Name the copy after the document: `VUM SUS-DR-004 Front Upright`.
3. Delete the starter files you are not using. Keep `overleaf-intro.tex`
   out of your working copy too, since it is reference material rather
   than a starter.
4. Rename the remaining starter to `main.tex`, right-click it →
   **Set as Main File**.
5. Fill in the `FILL THIS IN` block at the top and write.

Keep one Overleaf project per document, because several documents in one
project makes their revision histories difficult to separate.

**Class options** go on line 1, as in `\documentclass[designreport]{fsaedoc}`.
The options `designreport`, `testprocedure`, `testreport`, `guide`, and
`study` pick the document type. In addition, `nologo` drops the cover logo,
`noheadermark` drops the soft page-top watermark, and `a4paper` switches
the paper size.

---

## 2. Contents

```
fsaedoc.cls          The document class, not edited directly.
teaminfo.tex         Team name, car, season, logo, and colours. Edited yearly.
refs.bib             Shared bibliography. Add entries, never delete them.

overleaf-intro.tex   Read this first if you are new to Overleaf
                     (a finished guide, not a starter -- do not edit it)

member-intro.tex     Starter: your member introduction (onboarding task 1)
design-report.tex    Starter: subsystem design reports
test-procedure.tex   Starter: repeatable procedures
test-report.tex      Starter: results and conclusions from a test
how-to-guide.tex     Starter: onboarding and knowledge transfer

figures/             Images used by the documents.
  vum-logo.png                      team logo, cover page top left
  vum-watermark.png                 soft mark at the top of every page
  vanderbilt-lockup-horizontal.png  Vanderbilt lockup, cover top right
  vanderbilt-lockup-stacked.png     stacked alternative, unused by default
data/                CSV exports that get turned into tables

CHEATSHEET.md        Every template command on one page.
STYLE-GUIDE.md       The editorial rules every document follows.

MemberIntroductions-README.md
                     Not part of this template. A lead copies this into the
                     MemberIntroductions repo as its README.md, once.
```

---

## 3. Document IDs

The format is `SUB-TT-NNN`, meaning subsystem, type, and serial number.
The ID never changes once issued, even across a full rewrite. Only the
revision letter changes.

**Subsystem codes**

| Code  | Subsystem                     |
|-------|-------------------------------|
| `CHS` | Chassis and frame             |
| `SUS` | Suspension                    |
| `BRK` | Brakes                        |
| `PWR` | Powertrain                    |
| `DRV` | Drivetrain                    |
| `ELE` | Electrical and wiring         |
| `CTL` | Controls and data acquisition |
| `AER` | Aerodynamics                  |
| `ERG` | Ergonomics and driver controls|
| `MFG` | Manufacturing                 |
| `BUS` | Business, cost, presentation  |
| `GEN` | Team-wide / general           |

**Type codes**

| Code  | Document type   | Starter file          |
|-------|-----------------|-----------------------|
| `DR`  | Design report   | `design-report.tex`   |
| `TP`  | Test procedure  | `test-procedure.tex`  |
| `TR`  | Test report     | `test-report.tex`     |
| `HG`  | How-to guide    | `how-to-guide.tex`    |
| `SA`  | Study/analysis  | `design-report.tex` with `[study]` |
| `SP`  | Specification   | `design-report.tex`   |
| `MI`  | Member introduction | `member-intro.tex` |

Under this scheme, `BRK-TP-002` is the second brake test procedure issued.

**Member introductions are the one exception.** They use
`MI-<year joined>-<SURNAME>`, as in `MI-2026-LU`, because they are the first
document a new member writes and should not require claiming a number from
anyone, and a name is already unique. Add a first initial if a cohort has
two members with the same surname.

"Subsystem" here means the **area of the car or team the document is
about**, not a formal team structure. People on a small team work across
several areas, so a code does not need a dedicated group behind it. It
only needs to be the right category to file the document under.

Keep a single master list of issued IDs in the documentation repo (a plain
`ids.md` works fine). Claim the number *before* you start writing.

---

## 4. Revisions and status

Add a `\revision{}{}{}{}` line **every time you change a released document.**
The last line automatically becomes the current revision on the cover, so
the revision letter is never typed twice.

```latex
\revision{A}{2026-06-14}{P. Raghavan}{Initial draft for concept review.}
\revision{B}{2026-08-10}{P. Raghavan}{Re-ran FEA with corrected bolt preload.}
```

`\docstatus{}` controls the watermark:

| Status       | What it means                                | Watermark    |
|--------------|----------------------------------------------|--------------|
| `Draft`      | Being written. Do not build parts from it.   | DRAFT        |
| `In Review`  | Complete, waiting on approvers.              | IN REVIEW    |
| `Released`   | Approved. This is the one you work from.     | none         |
| `Superseded` | A newer document replaced this.              | SUPERSEDED   |

When you supersede a document, set the old one to `Superseded`, re-export it,
and put `\supersedes{OLD-ID}` in the new one.

`\reviewby{YYYY-MM-DD}` is the date by which someone must re-read the
document and either re-approve it or retire it. A document past its review
date may no longer be accurate.

The field is optional. If a document never sets it, the date defaults to
**14 days after the PDF was compiled** and is marked "(auto)" on the
cover, which suits drafts working through review. The window is set
team-wide with `\reviewwindow{14}` in `teaminfo.tex`. Two consequences
follow:

- The auto date is stamped at compile time, so it moves whenever the PDF
  is rebuilt. This is acceptable for drafts, since the archived PDF keeps
  the date it was built with, but not for released documents.
- **Released documents should set an explicit `\reviewby`**, typically
  about a year out, so that the commitment is recorded in the source rather
  than implied by when the PDF happened to be built.

---

## 5. Lead responsibilities

The system depends on leads running it, and every lead is learning it at
the same time as the members, and no existing group has prior experience
with it. The responsibilities divide into five areas.

**Onboarding.** A new member completes two tasks in order, which together
cover the whole toolchain on a document where mistakes have no
consequences:

1. **Write a member introduction** in Overleaf, from `member-intro.tex`.
   Covered by `GEN-HG-002`.
2. **Push it** to the
   [MemberIntroductions](https://github.com/VanderbiltMotorsports/MemberIntroductions)
   repo, both the `.pdf` and the `.tex`. Covered by `GEN-HG-001`.

Share the template project with the new member, add them to the GitHub
organisation, and treat the completed push as the sign-off. After that,
assign a real document, keeping the first one small, such as a test
report or a one-page how-to rather than a design report.

Keep the introductions repo private, and skim each new file for anything
that should not be visible to the whole organisation before counting the
task done. The privacy rules are stated in the starter file's header
comment, in both guides, and in that repo's own README, since this is the
document type most likely to attract oversharing.

**Reviewing.** For a document with status `In Review`, check the substance
first and then the frame. The `FILL THIS IN` block should be complete,
there should be a `\revision` line for the change, figures and numbers
should state their sources, and open items should have owners and dates.
Leave comments through Overleaf's Review feature rather than editing
silently.

**Releasing.** When a document passes review, the author sets
`\docstatus{Released}`, recompiles, and downloads the PDF named in the form
`SUS-DR-004_RevB_Front-Upright.pdf`. That PDF goes into the documentation
repo, attached to a GitHub release or committed under `released/`, rather
than remaining only in Overleaf, because the team reads released documents
from the repo. Sign the approval row when printing or re-exporting.

**Sweeping.** Once a year, before recruitment, walk the archive and
re-review anything past its review-by date. If a document is still
accurate, add a revision line and a fresh `\reviewby`. If it is not, fix
it or mark it `Superseded`.

**Seeding the archive.** The fastest way to rebuild the lost knowledge is
to record whatever currently exists in only one person's head. Anything
only one person knows how to do, such as running the sim, using the mill,
packing for competition, or passing tech inspection, should become a
`GEN-HG` document this semester, with an owner and a deadline assigned
like any other task.

Two conventions apply to everyone and are worth enforcing early:

- **Use `\openitem{}{}{}` instead of a TODO comment.** Open items are
  collected into a visible table at the end of the document, whereas a TODO
  buried in the source is easily overlooked and forgotten.
- **Every figure and number needs a source.** A claim of "we measured it"
  without a date and a file path cannot be verified later.

---

## 6. Marks and branding

The cover logo and the soft page-top watermark both come from the VUM logo in
`figures/`. Colours in `teaminfo.tex` are the official Vanderbilt values:
Black `#1C1C1C`, Vanderbilt Gold `#CFAE70`, and Oak `#946E24` for gold
text that needs to meet contrast requirements. Gold is used for rules and
fills only, because it does not pass contrast standards as body text on
white.

**Marks on the cover.** Top left is the VUM team logo, and top right is
the official Vanderbilt lockup. Both approved lockups ship in `figures/`:

| File | Use |
|---|---|
| `vanderbilt-lockup-horizontal.png` | default, with the V beside the wordmark |
| `vanderbilt-lockup-stacked.png` | V above the wordmark, for narrow layouts |

Swap between them with `\secondmark{}` in `teaminfo.tex`, and adjust the box
they are fitted into with `\secondmarksize{width}{height}`. The mark is scaled
to fit inside that box with its aspect ratio preserved, so it is never
stretched.

**Keep the marks unmodified.** Vanderbilt's guidelines for registered student
organizations say RSOs may not build their own logos out of University marks,
and official marks may not be altered. In practice, do not recolour,
crop, redraw, rotate, or add anything on top of the lockups, and do not
combine them with the VUM logo into a single new mark. Placing them
separately on a cover is fine. Questions go to the Office of Brand Engagement via
StudentAffairsCommunications@vanderbilt.edu.

---

## 7. Troubleshooting

**"Undefined control sequence".** A command was typed that does not
exist. Check the spelling against `CHEATSHEET.md`. Overleaf highlights the
line.

**A figure does not show up.** The file must be in `figures/`, and the
name is written **without the extension**, so `\fsfig{upright-fea}{caption}`
refers to `figures/upright-fea.png`.

**"Missing $ inserted".** A maths symbol like `_` or `^` was used outside
maths mode. Wrap it in dollar signs, as in `$F_z$`.

**A table fails to build.** Count the `&` separators. Every row needs the
same number of columns as the layout string, and every row ends with `\\`.

**Cross-references show `??`.** Recompile, because LaTeX needs two passes.
Overleaf usually does this automatically.

**The References section is missing.** It only appears if the document
actually uses `\cite{}` and `refs.bib` exists.

**"Can be used only in preamble".** A `\doctitle`, `\docauthor`,
`\revision`, or similar line ended up below `\begin{document}`. Move it
up into the `FILL THIS IN` block.

**"Not in outer par mode".** A figure or table macro was placed inside a
callout box. Move it outside the box.

**Something is broken with no obvious cause.** Remove the most recent
change and recompile. If the error clears, the removed text contained it.
If the problem persists after ten minutes, ask in the team chat, since
these errors are usually familiar to someone.

---

*Owned by whichever lead owns documentation. If something in this file is
wrong, fix it and commit the change.*
