# Career Clarity Assessment — Landing Page

A single-file landing page (`index.html`) to test the idea: **a 5-minute Career Clarity Assessment for people returning to work after a career break, ending in a personalized career roadmap.**

No frameworks, no build step. Open `index.html` in a browser and it works.

## The flow

**Hero:** "Ready to return to work, but not sure where to start?" → **[Start Assessment]** — deliberately not "Upload your CV", and no mention of AI anywhere.

**Assessment (6 steps, with progress bar):**

1. **Background** — age (optional), country, current location, years of experience, career break duration, reason for break (Parenthood / Caregiving / Illness / Relocation / Other)
2. **Previous experience** — job title, industry, education, languages, soft skills, other technical skills
3. **Goals** — desired work format (full-time / part-time / remote / hybrid / flexible), what matters most (pick up to 2)
4. **Confidence** — four 1–5 statements ("I know what type of job I want", "I know which skills I should learn", "I feel confident applying for jobs", "I know where to find suitable jobs") → these identify blockers
5. **Skills** — a simple "which of these are you comfortable with?" checklist (Marketing, Sales, Excel, Project Management, Python, SQL, Customer Support, Teaching, Design, …) — no real skill assessment yet
6. **Name + email** — the conversion moment: "Tell us where to send your full roadmap"

**Report ("Your Career Profile"):** rendered instantly from transparent rules — no fake AI:

- **Your biggest strengths** — the soft skills they selected
- **Potential career paths** — top 3 of 9 predefined roles (Customer Success, Project Coordinator, Operations Specialist, Data Analyst, Digital Marketing Specialist, Account Manager, Corporate Trainer/L&D, HR Coordinator, Content Specialist), scored by overlap with their selected skills (weight 2) and soft skills (weight 1), each with a one-line "why this fits"
- **Current blockers** — every confidence statement scored 3 or below, mapped to plain language ("Lack of confidence when applying", "Limited knowledge of today's job market", …)
- Ends with: your full roadmap arrives by email within 24 hours.

## Receiving submissions

The page runs in **demo mode** by default: the report renders, but answers go nowhere. To receive each completed assessment (all answers + email) by email:

1. Create a free form on [Formspree](https://formspree.io) (no file uploads needed anymore, so the free plan works).
2. In `index.html`, set the endpoint near the top of the `<script>` block:
   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/YOUR_FORM_ID";
   ```

If submission fails, the user still sees their report — you lose the lead, they don't lose the experience.

## GDPR

The page ships with the on-page half of GDPR compliance built in:

- A **required consent checkbox** at the email step (unticked by default), naming the exact purpose: answers are used to create the roadmap, delivered by email, withdrawable at any time.
- A **plain-language privacy notice** on the page (linked from the checkbox and the footer): who processes the data, what is collected and why, that Formspree (EU–U.S. Data Privacy Framework participant) delivers submissions, a 30-day retention promise, and the person's rights including complaint to the Dutch Autoriteit Persoonsgegevens.
- A **consent record** (statement + ISO timestamp) included in every submission, for accountability.

Before going live, complete the other half yourself:

1. **Fill in the placeholders** in the privacy notice in `index.html`: replace `[YOUR NAME / COMPANY NAME]` and `[YOUR CONTACT EMAIL]` with your real identity and a monitored address.
2. **Honor the notice**: send only the roadmap (no newsletter without a separate opt-in), delete submissions from Formspree and your inbox within the promised 30 days, and act on any access/deletion request promptly.
3. **In Formspree**: delete submissions after fulfilling each report; if you upgrade to a paid plan, accept their Data Processing Agreement in the workspace settings.
4. Collect nothing extra — the form already practices data minimization (age is optional); keep it that way.

## Deploying

Any static host works:

- **GitHub Pages**: repo Settings → Pages → deploy from branch, root folder.
- **Netlify / Vercel**: drag-and-drop the folder or connect the repo.

## Measuring the test

The funnel to watch: visitors → started assessment → completed step 4 (blockers revealed) → submitted email. Add a free analytics snippet (e.g. [Plausible](https://plausible.io), [GoatCounter](https://www.goatcounter.com)) to count these. Email submission rate is the signal that the value proposition lands.
