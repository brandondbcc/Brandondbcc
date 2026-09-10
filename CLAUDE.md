# Styled by Inez — Claude Code Project Instructions

## Project mission

Build a polished, premium beauty-business website for **Styled by Inez**. The site should feel bespoke, feminine, elegant and high-end without becoming cluttered or overly flashy.

The website is inspired by the structure and presentation of https://www.enhancebycourtney.co.uk/ but must be an original design and implementation. Do **not** copy its text, imagery, branding, code, layout pixel-for-pixel, or other protected creative material.

The supplied Styled by Inez logo is the primary branding reference. The logo has a warm ivory/cream background, black elegant typography/monogram, and fine champagne-gold detailing. Use the social profiles supplied by the owner as the source of truth for the brand's real-world colour direction where they can be accessed.

Brand/social links:
- Facebook: https://www.facebook.com/Styledbyinez/
- Instagram: https://www.instagram.com/styledby_inez/
- TikTok: https://www.tiktok.com/@styledby_inez
- Current Timely booking page: https://bookings.gettimely.com/styledbyinez/book
- Contact email: enquiries@styledbyinez.co.uk

## Non-negotiable development workflow

1. Work directly in the existing repository.
2. Inspect the existing project before changing anything. Do not overwrite an existing app blindly.
3. Prefer a modern Next.js App Router + TypeScript + Tailwind CSS stack if the repository is empty or the existing stack does not provide a strong reason to use something else.
4. The production target is Vercel.
5. GitHub is the source of truth.
6. After each completed, coherent change set:
   - run lint/typecheck/tests/build where available;
   - inspect the diff;
   - fix errors before committing;
   - `git add` the intended files;
   - commit with a clear conventional-style message;
   - `git push origin main`.
7. Do not leave completed work uncommitted or unpushed unless a GitHub/Vercel/authentication problem genuinely prevents it. If push fails, explain exactly why and leave the working tree in a safe state.
8. Never commit `.env`, API keys, service-role keys, passwords, private client data, or other secrets.
9. Do not force-push or destroy existing history.
10. Keep commits focused and descriptive, e.g. `feat: add gallery and reviews`, `fix: improve mobile navigation`, `chore: add SEO metadata`.

## Product/UX direction

Create a premium, mobile-first site with the visual confidence of a boutique beauty studio.

### Overall aesthetic
- Warm ivory/cream base.
- Black/dark charcoal typography.
- Restrained champagne/gold accents inspired by the supplied logo.
- Editorial serif display typography paired with a clean modern sans-serif body font.
- Lots of breathing room.
- Fine borders and subtle rules rather than heavy cards.
- Soft rounded corners only where they improve usability.
- High-quality placeholder imagery until the owner supplies real images.
- Subtle animations only: fade, slide, hover and gentle image transitions.
- Respect `prefers-reduced-motion`.
- Avoid generic AI-looking gradients, neon colours, excessive glassmorphism, huge text everywhere, and generic stock-template styling.

### Logo
Use the supplied Styled by Inez logo as the visual reference. If the actual asset is not available inside the repository, create an obvious asset placeholder such as `/public/brand/logo-placeholder.svg` and structure the code so the real logo can be dropped in later without changing components.

Do not recreate the logo as a near-copy using a different typeface. Use the supplied asset when available.

### Inspiration site structure
The reference site demonstrates a useful structure:
- Home
- Services
- Gallery
- About
- Contact
- Book Online
- Legal pages

Use this as inspiration only. Styled by Inez must have its own visual identity, copy and information architecture.

## Website structure

Build these routes/pages:

- `/` — Home
- `/services` — Services overview
- `/services/[slug]` — Individual service detail pages if useful
- `/about` — About Styled by Inez / practitioner
- `/gallery` — Gallery
- `/reviews` — Client reviews/testimonials
- `/book` — Timely booking experience
- `/contact` — Contact and enquiry options
- `/booking-policies` — Booking policies
- `/refund-policy` — Refund/cancellation policy
- `/privacy-policy` — Privacy notice
- `/cookie-policy` — Cookie policy
- `/terms-and-conditions` — Terms and conditions
- `/accessibility` — Accessibility statement
- `/sitemap.xml` — generated XML sitemap
- `/robots.txt` — generated robots file

If some routes are better combined for UX, keep the legal pages separate and directly accessible from the footer.

## Home page

Recommended sections:

1. **Announcement/header bar** — optional, only if useful.
2. **Navigation** — logo, Home, Services, About, Gallery, Contact, prominent `Book Now` CTA.
3. **Hero** — elegant headline, short supporting text, `Book an appointment` CTA and secondary `Explore services` CTA. Do not make unsupported claims.
4. **Featured services** — 3–6 real-service placeholders, clearly marked for later editing.
5. **About preview** — image placeholder + short introduction.
6. **Gallery preview** — 6–9 images with link to full gallery.
7. **Reviews preview** — only real client reviews entered by the owner. Never fabricate reviews.
8. **Booking CTA** — clear route into Timely.
9. **Contact section** — WhatsApp and email actions.
10. **Social links** — Facebook, Instagram, TikTok.
11. **Footer** — business details, contact details, legal links, social links and copyright.

## Services

Do not invent actual treatments/prices/claims. Use clearly labelled placeholders such as:
- `Service name`
- `Short description`
- `Duration`
- `Price`

The content model must make it easy to replace placeholders with the owner's real service data later.

If prices are displayed, make it clear whether they are starting prices, fixed prices, deposits, or otherwise. Never imply a price is current unless it has been supplied by the owner.

## Gallery system

Build a real gallery management system rather than a hard-coded image grid.

Preferred architecture:
- Supabase database for gallery metadata.
- Supabase Storage for images.
- Admin-only dashboard for adding/editing/removing gallery items.
- Fields should include at minimum:
  - `id`
  - `image_url`
  - `alt_text`
  - `title` (optional)
  - `description` (optional)
  - `category` (optional)
  - `sort_order`
  - `is_published`
  - `created_at`
  - `updated_at`
- Include sensible image optimisation and responsive sizing.
- Do not expose Supabase service-role credentials in browser code.
- Use Row Level Security.
- Only authenticated/authorised admin users may create, edit or delete gallery content.
- Public visitors can only read published gallery items.
- Add delete confirmation and safe error states.

### Gallery privacy/copyright rules

Never upload random internet images as if they belong to Styled by Inez.

For every real image, the owner must have appropriate rights/permission to use it. If a client is identifiable, the owner should have appropriate permission to publish the image. Store a simple internal record/field for consent where appropriate.

Use placeholder images during development and label them as placeholders. Replace them only with owner-supplied/licensed assets.

## Reviews system

Build a real review management system.

Preferred fields:
- `id`
- `client_name` (or initials/display name)
- `review_text`
- `rating` (optional)
- `source` (e.g. Google/Facebook/direct)
- `source_url` (optional)
- `consent_to_publish`
- `is_published`
- `sort_order`
- `created_at`
- `updated_at`

Rules:
- Never invent testimonials, ratings, review counts, client results, qualifications, awards or years of experience.
- Never alter a genuine review in a way that changes its meaning.
- If a review is supplied manually, retain its meaning and spelling unless the owner explicitly requests editing.
- Only publish reviews where Styled by Inez has the right/permission to publish them.
- Do not expose unnecessary personal information.
- Admin-only creation/editing/deletion.
- Public visitors only see approved/published reviews.

## Admin dashboard

Create a lightweight `/admin` area if Supabase is used.

Features:
- Login/logout.
- Gallery management.
- Review management.
- Optional service/content management if it materially simplifies future editing.
- Image upload with validation for type and size.
- Preview before publishing.
- Publish/unpublish toggles.
- Accessible forms.
- Clear success/error feedback.

Do not build a full CMS unnecessarily. Keep it simple enough for a small beauty business owner to use.

## Timely booking integration

Use Styled by Inez's Timely booking page:
`https://bookings.gettimely.com/styledbyinez/book`

Timely supports booking links/buttons/widgets. Prefer the official Timely widget/snippet supplied by the owner's Timely account rather than inventing an iframe implementation.

Timely documentation confirms that a booking widget can allow clients to complete booking without leaving the site, and that Timely provides the required embed/link code from its booking-button settings.

Implementation requirements:
- `/book` must have a clear booking experience.
- Add a prominent `Book Now` CTA in the header and throughout the site.
- If the actual Timely widget snippet is available, encapsulate it in a dedicated `TimelyBooking` component.
- Keep a fallback `Book securely through Timely` link to the supplied booking URL.
- The booking experience must remain usable on mobile.
- Give the embed an accessible title/label.
- Clearly identify Timely as a third-party service.
- Do not collect duplicate booking data on the Styled by Inez site unless necessary.
- Do not try to recreate Timely's booking system.
- Do not expose Timely credentials.

Important privacy/cookie behaviour:
- Treat Timely as a third-party service.
- Do not load optional third-party tracking/embedding technology before the user has the appropriate consent unless the particular technology is genuinely exempt/strictly necessary.
- If the Timely widget cannot be safely gated, provide an explicit user action such as `Load booking widget` with clear third-party disclosure, plus the direct booking link fallback.
- Review the exact Timely embed code supplied by the account owner before production because third-party scripts can change their storage/cookie behaviour.

## Contact / enquiry system

The site must provide two simple ways to contact Styled by Inez:

### WhatsApp
Create a form that can prepare a WhatsApp message containing:
- Name
- What the enquiry is about
- Message/question

Example generated message structure:
`Hi Styled by Inez, my name is [Name]. I'm enquiring about [Topic]. [Message]`

Do not hard-code a fake WhatsApp number. Create a configuration value such as:
`NEXT_PUBLIC_WHATSAPP_NUMBER`

The owner must supply the real number before production.

Use `https://wa.me/<number>?text=<encoded-message>` when the number is available.

### Email
Create a similarly useful email option addressed to:
`enquiries@styledbyinez.co.uk`

Use a safe `mailto:` fallback and, if a real server-side email provider is later configured, use that rather than exposing credentials in the browser.

Do not require unnecessary information. Name, email/contact method, enquiry topic and message should normally be sufficient unless the owner has a legitimate reason for additional fields.

### Form consent
Include a required acknowledgement such as:
`I have read the Privacy Policy and understand how my information will be used to respond to my enquiry.`

Do not bundle optional marketing consent into the required enquiry consent. If marketing consent is ever added, make it a separate unticked optional checkbox with clear wording.

## Legal and compliance requirements

This is a UK-facing small-business website. Build the site with UK GDPR/Data Protection Act 2018/PECR/consumer-law considerations in mind, while clearly treating the legal copy as a practical website template rather than a substitute for professional legal advice.

The website must include:
- Privacy Policy / Privacy Notice
- Cookie Policy
- Terms & Conditions
- Booking Policies
- Refund/Cancellation Policy
- Accessibility Statement

### Privacy notice

The privacy notice must explain, in plain English:
- who the business/data controller is;
- contact details for privacy enquiries;
- what personal data is collected;
- why it is collected;
- the lawful basis for each relevant purpose;
- where data comes from;
- who it is shared with, including relevant processors/third parties;
- international transfers where applicable;
- retention periods or clear retention criteria;
- security approach;
- individual rights;
- how consent can be withdrawn where consent is used;
- how to complain to the ICO;
- whether automated decision-making/profiling is used (normally state that none is used if true);
- third-party services such as Timely, Supabase, Vercel, email providers, analytics, social platforms and any other services actually used.

Do not state that a service is used if it is not actually configured.

The privacy notice must be updated when the actual technology stack changes.

### Data minimisation

Only collect information that is genuinely necessary for the stated purpose. Do not create unnecessary accounts, tracking identifiers or client profiles.

Do not collect sensitive/special-category data through the general contact form. If the business genuinely needs health/allergy/medical information for a particular treatment, that must be handled through an appropriate process and privacy notice wording rather than casually added to the website form.

### Cookies and tracking

Default position: no non-essential analytics/tracking.

Implement a consent system that:
- does not load non-essential cookies/tracking before consent;
- has clear `Accept`, `Reject`/`Decline`, and `Manage preferences` options where applicable;
- does not use pre-ticked optional consent;
- allows users to change/withdraw non-essential cookie consent later;
- explains categories and purposes in plain language;
- records consent in an appropriate way.

Strictly necessary functionality can operate without consent where legally exempt, but document why it is necessary.

If analytics are added later, integrate them behind consent and document the provider, purposes, cookies/storage, retention and any international transfer implications.

### Third-party embeds

Audit every third-party embed/script before production, including:
- Timely
- social media embeds
- maps
- analytics
- fonts/CDNs if applicable
- video embeds
- contact/email services
- Supabase
- Vercel services

Prefer self-hosted assets where practical. Simple external links to social platforms do not require embedding their tracking code.

Do not automatically embed Instagram/TikTok/Facebook feeds just because links are provided. A clean social-link section is preferable unless there is a clear business reason to embed content.

### Booking/refund/cancellation terms

Do not invent the owner's cancellation window, deposit amount, refund rules, lateness rules, no-show fees, rescheduling rules, patch-test requirements or other operational policies.

Create a clear policy template with obvious placeholders for the owner to confirm, for example:
- booking/deposit amount;
- cancellation notice period;
- rescheduling rules;
- late arrival rules;
- no-show rules;
- refunds;
- deposits;
- treatment suitability/patch tests if relevant;
- illness/contagious condition rules if relevant;
- exceptional circumstances;
- complaints process.

The terms must not attempt to remove statutory consumer rights or use unfair terms. Avoid blanket `no refunds under any circumstances` wording.

For online/distance contracts, account for applicable consumer cancellation information and exceptions rather than assuming a blanket policy overrides statutory rights. Where the service is requested to start within a statutory cancellation period, make sure the booking flow and terms handle the customer's rights appropriately.

### Business details

Do not invent:
- legal business name;
- registered address;
- studio address;
- company number;
- VAT number;
- phone number;
- insurance details;
- professional memberships;
- qualifications;
- awards;
- treatment claims.

Create a clearly documented configuration/TODO list for these details. The site should not publish fake details.

## Accessibility

Target WCAG 2.2 AA as the engineering standard, even though this is not a public-sector website.

Requirements:
- semantic HTML;
- correct heading hierarchy;
- keyboard navigation for every interactive feature;
- visible focus states;
- skip-to-content link;
- sufficient colour contrast;
- no colour-only communication;
- labelled form controls;
- clear validation and error messages;
- accessible modal/dialog behaviour;
- accessible mobile menu;
- accessible carousel/lightbox if used;
- reduced-motion support;
- logical tab order;
- minimum comfortable touch targets;
- alt text for meaningful images;
- decorative images use empty alt attributes;
- no text baked into images when HTML text is practical;
- buttons have clear labels (`Book an appointment`, `Send enquiry`, `Open gallery`, etc.).

Test keyboard-only navigation and basic screen-reader semantics before release.

## SEO

Implement:
- unique page titles;
- useful meta descriptions;
- canonical URLs where appropriate;
- Open Graph metadata;
- Twitter/X metadata where useful;
- semantic HTML;
- sitemap.xml;
- robots.txt;
- favicon/site icon;
- structured data where justified (e.g. LocalBusiness/BeautySalon only when the required details are real and verified);
- image alt text;
- clean URLs;
- noindex for admin/private pages;
- no accidental indexing of draft/test content.

Do not add fake star ratings or fake review structured data.

Use the real production domain only once it is confirmed. Do not invent a domain.

## Security

- Validate and sanitise all form input.
- Never trust client-side validation alone.
- Protect admin routes.
- Use Supabase RLS if Supabase is used.
- Never expose service-role keys in client bundles.
- Restrict image upload types and file sizes.
- Prevent unrestricted public writes to storage/database.
- Add reasonable rate limiting/anti-spam protection to server-side contact endpoints if one is created.
- Avoid collecting unnecessary personal data.
- Add security headers where appropriate.
- Do not add dangerous `dangerouslySetInnerHTML` unless there is a clear, sanitised reason.

## Content integrity rules

This is especially important:

**Never fabricate business claims.**

Do not invent:
- client reviews;
- qualifications;
- certificates;
- awards;
- years of experience;
- number of clients;
- treatment outcomes;
- before/after claims;
- medical/aesthetic claims;
- availability;
- prices;
- business address;
- phone/WhatsApp number;
- opening hours.

Use placeholders until the owner supplies the information.

Do not use another business's photographs. Placeholder imagery must either be generated/local development placeholders or properly licensed assets.

## Design details to preserve

The supplied logo suggests:
- elegant black calligraphic/serif monogram;
- refined champagne-gold thin-line circular detail;
- warm cream/ivory background;
- luxury/editorial beauty aesthetic.

Suggested starting tokens — treat these as editable, not absolute:

```css
--background: #F7F1E8;
--surface: #FBF8F3;
--foreground: #171514;
--muted-foreground: #6F6961;
--gold: #B7A06A;
--gold-soft: #D8C9A5;
--border: #DED5C7;
```

Do not blindly use these if the actual Facebook/Instagram brand visuals indicate a better palette. Keep the palette restrained and test contrast.

## Suggested technical stack

Unless an existing stack makes this inappropriate:
- Next.js latest stable compatible with Vercel
- TypeScript
- Tailwind CSS
- shadcn/ui only where it improves accessible primitives
- Supabase for gallery/reviews/admin data and image storage
- Vercel for deployment
- ESLint
- Prettier if already used / useful

Keep dependencies minimal. Do not add a library for something that can be implemented cleanly with native platform APIs.

## Environment variables

Create `.env.example` only. Never commit real values.

Potential variables:

```env
NEXT_PUBLIC_SITE_URL=
NEXT_PUBLIC_WHATSAPP_NUMBER=
NEXT_PUBLIC_TIMELY_BOOKING_URL=https://bookings.gettimely.com/styledbyinez/book
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
```

Only include variables actually used by the implementation.

## Owner configuration / TODO

Before calling the site production-ready, make it obvious that the owner needs to confirm:

- [ ] Real production domain
- [ ] Legal business/trading name
- [ ] Business/studio address if it should be public
- [ ] Real WhatsApp number
- [ ] Opening hours
- [ ] Real service list
- [ ] Real prices/durations
- [ ] About/practitioner biography
- [ ] Booking/deposit/cancellation policy
- [ ] Refund policy
- [ ] Any patch-test/treatment-specific policies
- [ ] Real gallery images and image permissions
- [ ] Permission to publish identifiable client images
- [ ] Real client reviews and permission/source
- [ ] Privacy retention periods
- [ ] Actual third-party processors/services
- [ ] Whether analytics will be used
- [ ] Cookie categories actually used
- [ ] Any business/company/VAT information that must legally be displayed

Do not silently turn these TODOs into fabricated facts.

## QA checklist before every production push

### Functional
- [ ] Navigation works on desktop/mobile
- [ ] All CTA buttons work
- [ ] Timely booking link/widget works
- [ ] WhatsApp link creates a correctly encoded message
- [ ] Email link works
- [ ] Contact form validation works
- [ ] Gallery loads published images only
- [ ] Admin authentication works
- [ ] Admin cannot modify content without authorisation
- [ ] Reviews publish/unpublish correctly
- [ ] Legal pages are reachable from the footer

### Accessibility
- [ ] Keyboard navigation works
- [ ] Focus states are visible
- [ ] Forms have labels
- [ ] Error states are understandable
- [ ] Contrast checked
- [ ] Images have correct alt text
- [ ] Decorative images are ignored by screen readers
- [ ] Reduced motion is respected

### Privacy/security
- [ ] No secrets committed
- [ ] No unnecessary personal data collected
- [ ] Privacy notice matches actual data flows
- [ ] Cookie behaviour matches actual cookies/storage
- [ ] Non-essential tracking is consent-gated
- [ ] Third-party embeds are documented
- [ ] Supabase RLS is enabled if used
- [ ] Admin routes are protected

### SEO
- [ ] Sitemap generated
- [ ] Robots generated
- [ ] Titles/descriptions present
- [ ] Canonicals appropriate
- [ ] Open Graph metadata present
- [ ] No fake structured-data reviews
- [ ] Admin/draft pages excluded from indexing

### Content/legal
- [ ] No fake reviews
- [ ] No unsupported claims
- [ ] No copyrighted/unauthorised placeholder photography
- [ ] Real business details inserted where required
- [ ] Booking/refund policies confirmed by owner
- [ ] Privacy/cookie/terms wording reflects actual implementation
- [ ] Consumer rights are not purportedly excluded

### Build/deployment
- [ ] `npm run lint` passes if available
- [ ] `npm run typecheck` or equivalent passes if available
- [ ] `npm run build` passes
- [ ] Production build tested at mobile and desktop widths
- [ ] Git diff reviewed
- [ ] Commit created
- [ ] Pushed to `origin main`

## Legal reference material for implementation decisions

Use current official guidance when checking the implementation. Do not treat these as a substitute for legal advice:

- ICO cookies and similar technologies: https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/cookies-and-similar-technologies/
- ICO privacy notices: https://ico.org.uk/for-organisations/advice-for-small-organisations/privacy-notices-and-cookies/cookies-and-privacy-notices-in-detail/
- ICO data minimisation: https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-protection-principles/a-guide-to-the-data-protection-principles/data-minimisation/
- ICO privacy information requirements: https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/the-right-to-be-informed/what-privacy-information-should-we-provide/
- GOV.UK online selling: https://www.gov.uk/online-and-distance-selling-for-businesses/online-selling
- GOV.UK distance selling: https://www.gov.uk/online-and-distance-selling-for-businesses
- GOV.UK Consumer Rights Act guidance: https://www.gov.uk/government/publications/consumer-rights-act-2015/consumer-rights-act-2015
- GOV.UK unfair consumer terms: https://www.gov.uk/unfair-terms-in-sales-contracts/unfair-consumer-contracts
- Timely website booking integration: https://help.gettimely.com/hc/en-gb/articles/33972391414039-Introduction-Connecting-Timely-Online-Booking-to-Your-Website
- Timely booking widget: https://help.gettimely.com/hc/en-gb/articles/33978904306967-How-to-add-a-booking-widget

When legal requirements or third-party behaviour may have changed, check the current official source before implementing or asserting compliance.

## Final instruction to Claude Code

Build the website to a genuinely production-quality standard, not as a generic template. Keep Styled by Inez's branding central, use the supplied logo as the visual anchor, make booking extremely easy, make future gallery/review management simple, and be conservative about claims and personal-data collection.

When information is missing, use an explicit placeholder/configuration value and continue building rather than inventing facts. Before the final push, perform the full QA checklist above, review the generated legal pages against the actual implementation, then commit and push all completed changes to GitHub.
