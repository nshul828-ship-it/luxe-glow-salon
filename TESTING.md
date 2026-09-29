# Verification record — 29 September 2026

## Passed
- Vite production build and JavaScript syntax validation.
- Real Chromium preview at desktop width 1363px; no horizontal overflow.
- Embedded responsive previews at frame widths 375px and 768px (content widths 360px and 753px after scrollbars); no document horizontal overflow. Mobile and desktop hero visually inspected.
- Mobile Menu control opens navigation.
- Colour service filter shows exactly two matching services.
- “Talk colour” selects Lived-in balayage in the appointment form.
- Empty contact configuration opens an honest setup dialog; no accidental telephone/WhatsApp destination.
- Completed form using fictional test details and an October 1 date shows unconnected delivery status; no external submission made.
- Comparison slider responds to ArrowRight, updates its accessible value from 50 to 51 percent.
- FAQ disclosure opens with its answer.
- All internal hash links resolve to actual IDs.
- Loaded image check found no broken images.
- Browser logs reviewed: no application errors observed; the browser's own extension emitted unrelated metadata errors.

## Not verified / launch gates
- Lighthouse score was not measured. 90+ remains a target, not a claim.
- Live Formspree acceptance/email receipt, configured phone/WhatsApp destination, and actual map location require owner configuration and end-to-end tests.
- Google Maps depends on third-party connectivity. The ordinary map link is provided as a fallback.
- Live GitHub push and Netlify/Vercel deployment are blocked by missing connected accounts.
- No physical iOS/Android, Safari, or assistive-technology testing was performed. Responsive frame inspection is not a substitute for those checks.
- Native HTML form constraints are present; a comprehensive validation/accessibility audit was not performed.

Local dev preview is not a public deployment. Sample testimonials and business details remain clearly labeled, and indexing is intentionally disabled until launch.
