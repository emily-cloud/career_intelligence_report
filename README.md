# Career Intelligence Report — Landing Page

A single-file landing page (`index.html`) to test the idea: **upload your CV, get a personalized career report within 24 hours.**

No frameworks, no build step. Open `index.html` in a browser and it works.

## The one job of this page

> "This page is not meant to impress investors. It's meant to convince one confused job seeker to upload their CV."

The headline promises exactly one thing: *in 24 hours you'll know which career path is realistic for you, what skills you're missing, and what to do next.* AI is deliberately never mentioned.

## Form fields

Upload CV → Name → Email → LinkedIn (optional) → Target job → Country → Current location → Years of experience → Biggest challenge → **Thank you!** ("We'll send your personalized report within 24 hours.")

## Making the form actually deliver submissions

The form currently runs in **demo mode**: it validates and shows the thank-you screen, but sends nothing anywhere. To receive real submissions:

1. Create a form on a service that accepts file uploads, e.g. [Formspree](https://formspree.io) (file uploads need a paid plan) or [Tally](https://tally.so) (free file uploads — but then embed their form instead).
2. Open `index.html` and set the endpoint near the bottom of the file:
   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/YOUR_FORM_ID";
   ```
3. Submissions (including the CV file) will arrive in your Formspree inbox / email.

## Deploying

Any static host works:

- **GitHub Pages**: repo Settings → Pages → deploy from branch, root folder.
- **Netlify / Vercel**: drag-and-drop the folder or connect the repo. (On Netlify you can also use [Netlify Forms](https://docs.netlify.com/forms/setup/) instead of Formspree.)

## Measuring the test

Suggested success signal: of the people who land on the page, how many upload a CV and submit? Add a free analytics snippet (e.g. [Plausible](https://plausible.io), [GoatCounter](https://www.goatcounter.com)) to count visits vs. submissions.
