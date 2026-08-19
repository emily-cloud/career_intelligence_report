# UnityWerk — Career Clarity Assessment (Builder Week Mini-MVP)

A single-file landing page (`index.html`) piloting a **Career Clarity Assessment for women returning to work after a career break**. No frameworks, no build step, no backend — open `index.html` in a browser and it works.

**Core hypothesis:** what has this woman actually done → what transferable skills may be hidden in that experience → what realistic career directions could fit her now → what should she do next?

The page therefore collects **evidence**, not just labels: what she did in her previous role, what her career-break activities actually involved, what people rely on her for, and any professional skills in her own words. Submissions are reviewed (with AI/manual help) to write each personalized roadmap, delivered by email within 24 hours.

## The flow (19 pages, one topic each, ~5 minutes)

1. Where are you based? (country + city)
2. Years of work experience
3. Career break length
4. Break reason (incl. Other + Prefer not to say)
5. Career-break activities **+ "Tell us briefly what this involved"** (free text, required)
6. Previous job title + industry **+ "What did you actually do in this role?"** (free text, required)
7. Highest education
8. Languages with levels (up to 4)
9. "What kinds of things have people relied on you for?" (behavioral strengths, up to 4)
10. Desired work format (up to 3)
11. What matters most (incl. work-life balance, getting back quickly; up to 3)
12. Interests (up to 3)
13. What would you like to do next? (goal)
14. Biggest challenges (incl. skills-relevance, explaining the break, language/qualifications; up to 2)
15. How would you prefer to solve this? (product validation; up to 2)
16. Transition readiness: how much change + ideal return timeline (one screen)
17. Three 1–5 confidence statements (one screen)
18. Reusable professional skills (optional free text)
19. Name + email + optional notes + GDPR consent → instant Career Profile preview

**After the report:** one product-research question — "What would be most valuable to you next?" — sent as a separate fire-and-forget submission.

## The instant report

Rendered from transparent rules, no AI at runtime: strengths are her own selected words; career paths come from a 27-role catalog scored on background keywords (job title/industry, weight 3), skills detected in her own free text (weight 2), behavioral strengths and interests (weight 1), plus goal/activity boosts; blockers combine her named challenges with low confidence scores. A note clarifies these are starting points, and the full roadmap explores beyond the list.

## Receiving submissions

Submissions post to the `FORM_ENDPOINT` (Formspree) configured near the top of the `<script>` block. If submission fails, the user still sees her report. Note the post-result question sends a **second** small submission per user.

## Privacy (GDPR)

Consent checkbox (unticked by default), on-page privacy notice (UnityWerk pilot; contact unitywerk@gmail.com; Formspree as processor; 30-day retention; data-subject rights), and a timestamped consent record in each submission. **Open item:** the notice names UnityWerk as a pilot project — confirm the formal controller name/address for a Berlin/Germany-based pilot before scaling beyond friendly testers.

Operator duties: fill roadmaps within 24h, delete submissions within 30 days, no mailing beyond the roadmap, honor access/deletion requests.

## Photos (optional)

One image slot is wired in: add a **`background.jpg`** next to `index.html` and it renders as a photographic backdrop behind a soft white veil across the whole page. Without the file, the textured gradient shows — nothing breaks.

Recommended: a calm, light photo (a bright workspace, soft morning light, plants) around 1600–2000px wide, compressed to under ~400KB (e.g. via squoosh.app) so the page stays fast. Free sources with safe licenses: unsplash.com and pexels.com.

## Deploying

GitHub Pages (Settings → Pages → deploy from `main`) or Netlify. A pre-Builder-Week snapshot is preserved on the `backup/pre-builder-week` branch.

## Measuring the test

Funnel: visits → Start clicked → email submitted → post-result answer. The free-text answers (`career_break_details`, `previous_role_tasks`, `reusable_skills`, `biggest_challenge`, `most_valuable_next`) are the core research data.
