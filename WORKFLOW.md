# WORKFLOW.md — Inquiry Form Generation & Branch Review

## Context

Two inquiry forms were generated from scratch into separate branches:

- **`vague-inquiry-form`** — the first form: plain HTML only, no CSS, no JS. A generic
  contact form with name, email, phone, company, subject, and message fields. Submitted via
  an empty `action=""` with `method="post"` and relies on the browser's native validation only.
- **`precise-inquiry-form`** — the second form: a single `index.html` with embedded CSS and
  JS, purpose-built for a portfolio website (feedback / about-me / FAQ-suggestion / hire
  subjects). Adds age, gender, urgency, explicit per-field `required` flags, a JS submit
  handler with email-format validation, success/error banners, and a reset button.

The two branches diverge structurally: each contains only its own form file, so a
`git diff` between them reads as "one file added, the other deleted." The meaningful
comparison is the HTML inside each `index.html`.

## Correctness

The **vague** form's `action=""` is a non-functional placeholder — submitting reloads the
page and drops the data, with no backend or client handler. Its only guardrail is the native
`required` attribute. The **precise** form is internally correct: JS validates all required
fields, regex-checks the email, prevents the default submit (`e.preventDefault()`), shows a
success banner, and clears the form. It has no backend either, but it fails predictably and
gracefully. Neither persists data — accurate for a "client-side only" scope, but
honest-in-the-docs.

## Accessibility

Both forms use real `<label for="id">` pairs on every field — the single most important
accessibility baseline, and it holds here. The **precise** form also adds `placeholder`
text, an explicit `<h1>`, a subtitle explaining the required-mark convention, and structured
markup a screen reader can navigate. Neither form, however, includes `aria-required`,
`aria-invalid`, or `role="status"`/`aria-live` on the message banner — the **precise** form
announces errors visually only, so screen-reader users miss them. Color contrast on the
secondary button and hint text is adequate but not WCAG-verified. The **vague** form is more
accessible-by-accident (it does less) but also less usable.

## Edge cases

The **vague** form handles extras poorly: `action=""` lets users submit into a void, and
trimming/empty-string edge cases are left to the browser. The **precise** form covers more:
`.trim()` on text inputs, an email regex that rejects `@.`-less strings, an age input with
`min="0" max="120"`, a "Prefer not to say" gender option, and a disabled-first-option pattern
on every `<select>` so users can't silently submit the placeholder. Gaps remain: no max-length
on the message, no duplicate-submit prevention (a fast double-click can fire the handler twice),
and the email regex is permissive — it passes `a@b.c`.

## Review effort

The **vague** form is trivial to review (~47 lines): one pass confirms the labels and that
`action` is empty. The **precise** form (~253 lines) needs a real review — three concerns to
check separately: the CSS for overflow at narrow widths, the JS for the double-submit gap,
and the markup for the missing `aria-live` on the banner. A 15-minute focused review is
enough; a fast skim would miss the JS regressions.
