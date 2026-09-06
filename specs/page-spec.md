PROJECT: Rob's Technical Leader landing page

WHAT IT IS:
A single-page landing site introducing Rob to potential clients as a
fractional CTO consultant. One self-contained HTML file, no build step,
no external network requests.


==============================================================
DESIGN TOKENS (single source of truth)
==============================================================
All values below are authoritative. Component sections reference these
names instead of repeating raw values.

COLOR
- color-bg            #ffffff   page background
- color-text          #1a1a1a   headline, logo, primary text
- color-text-muted    #4a5568   bio paragraph (softer reading)
- color-text-subtle   #718096   footer
- color-accent        #3b82f6   CTA button background
- color-accent-hover  #2563eb   CTA button background on hover/focus
- color-on-accent     #ffffff   CTA button label
- color-focus-ring    #1a1a1a   keyboard focus outline

TYPE
- font-family    Arial, Helvetica, sans-serif
- size-headline  32px  (24px at <=768px)
- size-bio       16px
- size-cta       18px
- size-logo      18px
- size-footer    13px
- weight-bold    700

SPACING / SHAPE
- content-max-width   500px
- radius-button       8px
- gap-headline-bio    16px   (margin below headline)
- gap-bio-cta         32px   (margin below bio)
- cta-padding         16px 32px  (16px 24px at <=768px, full-width)

MOTION
- transition          background-color 0.2s ease, transform 0.2s ease
- hover-scale         1.05
- Disable all transition + transform under
  @media (prefers-reduced-motion: reduce)


==============================================================
PAGE STRUCTURE
==============================================================
Document
- <!DOCTYPE html>, <html lang="en">
- <meta charset="UTF-8">
- <meta name="viewport" content="width=device-width, initial-scale=1.0">
- <title>Rob Molchon — Fractional CTO</title>
- <meta name="description" content="Rob is a fractional CTO helping
  companies build and scale technical teams and products.">
- Favicon: inline data-URI or emoji favicon (no external file request)
- All CSS inline in a single <style> block

Layout
- Vertical flex column, min-height 100vh: header / main / footer
- Header: site logo only ("Rob Molchon"), left-aligned, 24px padding
- Main: flex-centered, holds the hero; max width content-max-width,
  text left-aligned; padding 48px 24px 64px
  (32px 20px 48px and top-aligned at <=768px)
- Footer: copyright line, size-footer, color-text-subtle

1. HEADLINE
   - Element: <h1> (one per page)
   - Text: "Hi, I'm Rob Molchon — a Fractional CTO"
   - Font size: size-headline
   - Font weight: weight-bold
   - Color: color-text
   - Line height: 1.25
   - Margin bottom: gap-headline-bio

2. BIO PARAGRAPH
   - Element: <p>
   - Text: "I help founders and growing teams make sound technical
     decisions without the cost of a full-time executive hire —
     covering architecture, engineering leadership, hiring, and product
     strategy so you can build with confidence."
   - Max width: content-max-width
   - Font size: size-bio
   - Line height: 1.6
   - Color: color-text-muted
   - Margin bottom: gap-bio-cta

3. CONTACT BUTTON
   - Element: <a class="cta-button">
   - Text: "Book a Free Consultation"
   - aria-label: "Book a free consultation with Rob by email"
   - Background: color-accent
   - Text color: color-on-accent
   - Font size: size-cta, weight-bold
   - Padding: cta-padding
   - Border radius: radius-button
   - Hover AND focus-visible: background color-accent-hover,
     transform scale(hover-scale)
   - Focus-visible: also 3px solid color-focus-ring outline,
     outline-offset 3px
   - Href: mailto:robmolchon@gmail.com?subject=Free%20Consultation%20Inquiry


==============================================================
RESPONSIVE
==============================================================
- Breakpoint at max-width: 768px
- Headline drops to 24px
- Main switches to top-aligned, reduced padding
- CTA button becomes full-width, centered text, cta-padding 16px 24px
- No horizontal scroll at 320px width


==============================================================
SUCCESS CRITERIA (testable)
==============================================================
LAYOUT
- Renders correctly at 320px, 768px, and 1280px viewport widths
- No horizontal scrollbar at any of those widths
- Hero content never exceeds content-max-width

CONTRAST (WCAG 2.1 AA)
- color-text on color-bg: >= 4.5:1  (actual ~17:1)
- color-text-muted on color-bg: >= 4.5:1  (actual ~7.5:1)
- color-text-subtle on color-bg: >= 4.5:1  (actual ~4.6:1)
- color-on-accent on color-accent: button label is large text
  (>=18px bold), so >= 3:1 required (actual ~3.7:1); verify with a
  contrast checker before shipping. Hover state (~5.2:1) passes AA
  normal text.

ACCESSIBILITY
- Single <h1>; logical heading order
- Button reachable and operable by keyboard (Tab + Enter)
- Visible focus ring on the button (focus-visible styles above)
- Animations suppressed under prefers-reduced-motion
- Passes automated axe / Lighthouse a11y checks with no violations

PERFORMANCE
- Single HTML file, CSS inline, zero external requests (no web fonts,
  no images loaded from network, no analytics)
- Total file size < 50KB
- Lighthouse Performance score >= 95 on desktop; First Contentful
  Paint < 1s on a fast 3G throttle

FUNCTIONAL
- Clicking / activating the button opens the user's mail client with
  To: robmolchon@gmail.com and Subject: "Free Consultation Inquiry"
