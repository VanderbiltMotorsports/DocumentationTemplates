<!--
=============================================================================
  This file is NOT part of the documentation template.

  It is the README for the separate MemberIntroductions repository:
  https://github.com/VanderbiltMotorsports/MemberIntroductions

  A lead should copy this file into the root of that repo as README.md,
  once, and then delete this comment block. It is kept here so the text
  lives in version control somewhere rather than in one person's head.
=============================================================================
-->

# Member Introductions

One short document per member, describing who they are and what they want
to work on. The repository serves two purposes:

1. **Onboarding exercise.** Writing an introduction in Overleaf and pushing
   it here is how every new member learns the two tools the team runs on,
   using a task where mistakes have no consequences.
2. **A record of membership.** The team lost most of two decades of
   knowledge because nothing was written down, and this repository is the
   simplest possible start on correcting that. At minimum, it records who
   worked on what, and when.

## How to add yours

Both guides live in the documentation template and walk you through it with
no prior knowledge assumed:

| Guide | What it covers |
|---|---|
| `GEN-HG-002` Overleaf and LaTeX From Zero | Writing the document |
| `GEN-HG-001` GitHub for New Members | Pushing it here |

In outline, copy the Overleaf template project, keep `member-intro.tex`,
fill it in, download the PDF **and** the `.tex`, and commit both to the
folder for the year you joined.

## Layout

```
2017/
  lu-daiwei.tex
  lu-daiwei.pdf
2027/
  ...
```

- Folder is the **year you joined**, not the competition season.
- Files are `surname-firstname`, lowercase, hyphens, no spaces.
- Push **both** the `.tex` and the `.pdf`. The PDF is the readable copy,
  and the `.tex` is plain text, so a later edit shows a readable diff.

To update your introduction in a later year, drop your `.tex` back into a copy
of the Overleaf template as `main.tex`, edit, and push the new pair.

## What to write, and what not to

Pitch it the way you would introduce yourself at the first team meeting.

**Include:** your name, year and major, what you want to work on, what you
can already do (*"nothing yet"* is a normal and useful answer), what you
want to learn, something non-car about you, and your Vanderbilt email if
you want to be reachable.

**Do not include:** home address, phone number, student ID or VUnetID, date of
birth, GPA or grades, class schedule, health or financial information,
anything about another person who has not agreed to it, or any password or
licence key.

A photo is optional. Include one or not as you prefer.

> **Private here means private to the GitHub organisation.** Everyone in the
> organisation can read this repository, including members who have not joined
> yet, and git history is effectively permanent, since deleting a file in
> a later commit does not remove it from the history. Re-read your file before you
> commit.
>
> If something sensitive does get pushed, **tell a lead** rather than deleting
> it in a new commit. Scrubbing git history is a job for someone who has done
> it before.

## For leads

- Keep this repo **private**, and check that setting after any
  organisation change.
- Accepting the organisation invite is a prerequisite, and most reports
  of the repository being invisible trace back to an unaccepted
  invitation.
- When someone leaves the team, their introduction stays. Remove it only
  if the person asks.
- Confirm each new member's push as the sign-off for onboarding.
