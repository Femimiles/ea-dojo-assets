# Sensei guide: build plan

Status: proposed 2026-09-26, waiting for Miles's go.
Design: /mnt/project-files/design/sensei/ (mockup page, screenshot, pose SVGs), also in Femimiles/ea-dojo-assets under sensei/.
Mockup link: https://claude.ai/artifact/RkWNTf5Kgt5ScSF36fAu5Y

## What it is
One original 2D sensei, drawn for EA Dojo in the logo's style, who guides learners
everywhere the site already speaks as "Sensei" or gives advice. Four poses: welcome,
teach, think, bow, plus a round head avatar. Brand colours unchanged; the only new
colour is his skin tone.

## Phase 1: the character in the app
- New `src/components/Sensei.tsx`: `<Sensei pose="welcome|teach|think|bow" />` and
  `<SenseiAvatar size={36|56} />`, drawn as inline SVG (no image files, sharp at any size).
- Accessible text on every pose; the gentle breathing motion switches off for
  people who have reduced motion turned on.
- Settle his look and name first (decisions below).

## Phase 2: give the existing "Sensei's take" a face
Replace the 🥋 emoji with the avatar and a speech-bubble style note in:
- `src/components/exercises/DecisionPoint.tsx` (lesson decisions)
- `src/components/exercises/ScenarioDecisionPoint.tsx` (EA in Real Time)
- `src/components/exercises/StakeholderRoom.tsx` (stakeholder rooms)
- `src/pages/Capstone.tsx` ("Before you take it to the board")
No wording changes; the lines he says are already written.

## Phase 3: home page greeting
- `src/pages/landing/Hero.tsx`: the sensei stands beside the headline with a speech
  bubble and a "Try your first case with me" link to the free scenario.
- Warm light, faint shoji lattice and a tatami floor strip behind him, as in the mockup.
- Phones: smaller sensei, bubble above him, headline first.
- Signed-in learners: the bubble points to their next module instead, so the
  "Current session" progress card is folded into what he says.
- The "EA in Real Time" card that sits in the hero today (25 judgment calls,
  7 industries, industry chips, "Try one free") is kept, not dropped. It moves into
  its own strip straight after "The judgment gap" section, which ends on real
  scenarios, so it reads as the next step. Same content, same free-scenario link,
  wider layout with the chips beside the text. Code: lift it out of
  `src/pages/landing/Hero.tsx` into a new `src/pages/landing/RealTimeStrip.tsx`
  and place it in `src/pages/Landing.tsx` after `<JudgmentGap />`.

## Phase 4: the sensei everywhere else he belongs
- Workbench coach (`src/pages/workbench/Workbench.tsx`): the "Coach: why and how to
  fix" notes and wording tips come from the sensei (think pose avatar).
- Quizzes (`src/components/QuizBlock.tsx`): pass = bow, not yet = think, with the
  topics to revisit in his words.
- Module finished, `/complete` page and certificate: the bow.
- 404 page: the sensei pointing the way back.

## Later (optional)
- A belt per module on the curriculum page and certificate (existing colours only).
- The sensei on the social preview card (ea-dojo-assets/social).

## How it ships
Front end only: no database changes, no migrations. One PR against main, checked
with typecheck, build and screenshots at laptop (1366px) and phone width. It goes
live only when Miles says so (merge main into the production branch).

## Decisions for Miles
1. His look: the elder from the reference, or a Nigerian elder in the same robe
   (recommended, since the cases are Nigerian).
2. His name: "Sensei" (recommended for now) or a proper name.
3. Where the reference image came from. It is not used anywhere; this only matters
   if Miles wants that picture itself on the site.
