---
name: sign-in-forms
description: Best practices for building accessible, secure, mobile-friendly sign-in, sign-up, and password reset forms. Trigger on any task involving login/signup/password/authentication UI, credential inputs, or password manager integration.
---

# Sign-in Form Best Practices

## Structure

- Wrap credential inputs in a real `<form>`, not a `<div>`. Password managers key off `<form>` + submit button.
- Every input gets a `<label for="…">` above it. Never use `placeholder` as a label.
- Use `<button type="submit">` — never a styled `<div>`. Copy says the action: **Sign in**, **Create account**.
- One field per purpose. Do not double up email or password confirmation inputs.
- Give `id` and `name` **stable** values (not randomized per build/render). Autofill breaks without them.

## Input Attributes

Email/username input:
```html
<input type="email" id="email" name="email" autocomplete="username" required>
```
(Use `autocomplete="username"` even for email — that's the token password managers recognize.)

Sign-in password:
```html
<input type="password" id="current-password" name="password"
       autocomplete="current-password" required>
```

Sign-up / new password / password reset:
```html
<input type="password" id="new-password" name="new-password"
       autocomplete="new-password" required>
```

Change-password forms: old password gets `current-password`, new password gets `new-password`.

Phone: `type="tel"`. Numeric PIN: `inputmode="numeric"`.

Rely on the `required` attribute for missing-field validation before adding JS.

## Password UX

- Add a **Show password** toggle that flips `type` between `password` and `text`. The toggle button needs `aria-label` warning that the password will be visible on screen.
- Include a **Forgot password** link near the password input.
- Describe password rules with a sibling element referenced by `aria-describedby` on the input.

## Submission

- On success: navigate to a new page, or `history.pushState()`/`replaceState()` and remove the form from the DOM. This is how password managers detect success and offer to save.
- Disable the submit button *after* the first click to prevent double-submit. Do **not** disable it before the user has filled things in — show a validation message instead.
- Two-step sign-in (email page → password page): still use one `<form>`, or on the second page include a hidden `<input>` carrying the email value so password managers store the right credential.

## Mobile & Touch

- Inputs and buttons need ≥48×48 CSS px hit area. Add ~15 px padding on mobile, ~10 px on desktop.
- Input font-size ≥16 px on desktop, ~20 px on mobile. Sub-16 px input font on iOS triggers zoom.
- Give inputs a visible border (`#ccc` or darker on white) — the browser default is nearly invisible on Android.
- Keep email, password, and submit button at the top of the viewport so the on-screen keyboard doesn't cover the submit button.

## Validation

- Use built-in HTML validation (`type="email"`, `required`, `pattern`) first. It sets focus and shows a prompt with zero JS.
- Style invalid inputs with `input:not(:placeholder-shown):invalid` — the `:not(:placeholder-shown)` prevents empty fields from flashing red before the user has typed.
- For richer real-time validation use the Constraint Validation API (`setCustomValidity`, `checkValidity`).

## Accessibility

- Labels above inputs, not beside — better on mobile and scans faster.
- `aria-describedby` for rules/hints, `aria-label` on icon-only buttons (Show password, etc.).
- Errors must be announced: put error text in a live region or reference it via `aria-describedby` when invalid.

## Do Not

- Do not use `placeholder` as the only label.
- Do not randomize `id`/`name` between renders — kills autofill.
- Do not require email or password re-entry ("confirm password").
- Do not disable submit until the form is valid without telling the user why.
- Do not use `autocomplete="off"` on password fields — modern browsers ignore it and it breaks managers.
