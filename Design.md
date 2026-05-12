---
name: Midnight Copper Luxury
colors:
  surface: '#121416'
  surface-dim: '#121416'
  surface-bright: '#38393c'
  surface-container-lowest: '#0c0e10'
  surface-container-low: '#1a1c1e'
  surface-container: '#1e2022'
  surface-container-high: '#282a2c'
  surface-container-highest: '#333537'
  on-surface: '#e2e2e5'
  on-surface-variant: '#d8c3b4'
  inverse-surface: '#e2e2e5'
  inverse-on-surface: '#2f3133'
  outline: '#a08d80'
  outline-variant: '#524439'
  surface-tint: '#ffb77b'
  primary: '#ffb77b'
  on-primary: '#4d2700'
  primary-container: '#c8803f'
  on-primary-container: '#432100'
  inverse-primary: '#8c4f10'
  secondary: '#c2c7cc'
  on-secondary: '#2c3135'
  secondary-container: '#42474c'
  on-secondary-container: '#b1b6ba'
  tertiary: '#ffb87b'
  on-tertiary: '#4c2700'
  tertiary-container: '#c2834b'
  on-tertiary-container: '#422100'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#ffdcc2'
  primary-fixed-dim: '#ffb77b'
  on-primary-fixed: '#2e1500'
  on-primary-fixed-variant: '#6d3a00'
  secondary-fixed: '#dfe3e8'
  secondary-fixed-dim: '#c2c7cc'
  on-secondary-fixed: '#171c20'
  on-secondary-fixed-variant: '#42474c'
  tertiary-fixed: '#ffdcc2'
  tertiary-fixed-dim: '#ffb87b'
  on-tertiary-fixed: '#2e1500'
  on-tertiary-fixed-variant: '#6b3b07'
  background: '#121416'
  on-background: '#e2e2e5'
  surface-variant: '#333537'
typography:
  display-lg:
    fontFamily: Playfair Display
    fontSize: 64px
    fontWeight: '700'
    lineHeight: '1.1'
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Playfair Display
    fontSize: 40px
    fontWeight: '600'
    lineHeight: '1.2'
  headline-md:
    fontFamily: Playfair Display
    fontSize: 32px
    fontWeight: '500'
    lineHeight: '1.3'
  body-lg:
    fontFamily: Manrope
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
  body-md:
    fontFamily: Manrope
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.6'
  label-md:
    fontFamily: Manrope
    fontSize: 12px
    fontWeight: '600'
    lineHeight: '1.0'
    letterSpacing: 0.1em
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  base: 8px
  container-max: 1280px
  gutter: 24px
  margin: 48px
  section-gap: 120px
---

## Brand & Style

This design system evokes an atmosphere of nocturnal refinement and industrial elegance. The brand personality is rooted in high-end editorial aesthetics, targeting an audience that appreciates artisanal quality and quiet prestige. By moving away from traditional gold toward a deep, burnished copper, the visual narrative shifts from "ornate" to "sophisticatedly raw."

The design style is a hybrid of **Minimalism** and **Tonal Layering**. It prioritizes expansive negative space and sharp typographic hierarchy, using subtle texture and light-catchers rather than heavy ornamentation. The emotional response is one of calm, exclusivity, and enduring substance.

## Colors

The palette is anchored by a "Cool Charcoal" base (#121416), providing a more modern and expansive depth than pure black. The primary accent is a **Sophisticated Copper** (#B87333), utilized for key calls to action and critical highlights.

- **Primary:** Deep Copper (#B87333) used for interactive states and brand flourishes.
- **Secondary:** Charcoal Grey (#2C3135) used for component surfaces and borders.
- **Surface:** The midnight charcoal base (#121416) occupies the majority of the screen real estate.
- **Typography:** Headlines utilize an Off-White (#F4F4F4) to reduce eye strain, while secondary text uses a muted Slate (#8A9196).
- **Accents:** A lighter, brushed copper (#D9975D) is reserved for hover states and delicate iconography.

## Typography

The typography strategy relies on the high-contrast tension between the classical, romantic curves of **Playfair Display** and the technical, clean precision of **Manrope**.

Headlines should be treated as design elements themselves, often utilizing tight letter spacing in larger formats to create a "locked-in" editorial feel. Body text is set in Manrope to ensure maximum legibility against the dark charcoal background, with a generous line height to prevent the "vibration" often felt with light-on-dark text. Labels and metadata should always be uppercase with increased tracking to emphasize the structured, premium nature of the design system.

## Layout & Spacing

This design system employs a **Fixed Grid** model for desktop, centered within a 1280px container to maintain a sense of controlled luxury. The layout relies on an 8px rhythmic scale, with significant "breathing room" between major sections (120px+) to denote importance and exclusivity.

Margins and gutters are generous, preventing the UI from feeling cluttered or "app-like." Elements should often be offset from the standard grid to create a more dynamic, magazine-style flow, particularly when pairing imagery with Playfair Display headlines.

## Elevation & Depth

Depth in this design system is achieved through **Tonal Layering** and **Subtle Inner Glows** rather than traditional drop shadows. 

1.  **Base Layer:** The deepest Charcoal (#121416).
2.  **Mid Layer:** Cards and containers use a slightly lighter tint (#1A1D1F) with a 1px border in a muted copper-tinted grey.
3.  **Top Layer:** Modals and tooltips utilize a soft backdrop blur (20px) with a semi-transparent Charcoal fill to maintain context while suggesting physical elevation.

To simulate the reflective quality of copper, high-elevation components may feature a very subtle 1px top-edge highlight (inner shadow) in a low-opacity Copper hue.

## Shapes

The shape language is "Soft" (0.25rem), providing just enough rounding to feel modern and accessible without losing the architectural rigor of a luxury brand. Larger components like cards or hero images may scale up to a "rounded-lg" (0.5rem) to soften the overall composition, but interactive elements like buttons should remain crisp and precise.

## Components

- **Buttons:** Primary buttons feature a solid Copper (#B87333) fill with white text. Secondary buttons use a transparent background with a 1px Copper border.
- **Input Fields:** These should be "Underlined" style rather than fully boxed, emphasizing the editorial feel. The focus state transitions the underline from Charcoal to Copper.
- **Cards:** Use the "Mid Layer" color (#1A1D1F). Avoid heavy shadows; instead, use a 1px border that slightly brightens on hover.
- **Chips/Tags:** Minimalist design—small caps Manrope text with a subtle Copper dot prefix, rather than a heavy background fill.
- **Checkboxes & Radios:** When active, these should glow with a soft Copper outer halo (2px blur) to simulate a light-emitting diode.
- **Dividers:** Use extremely thin (0.5px), low-opacity lines in the secondary Charcoal color to separate content without creating visual noise.
---
name: Midnight Creole Luxury
colors:
  background: '#0B0B0B'
  primary: '#C5A059'     # Or créole
  secondary: '#B35A38'   # Terre cuite
  surface: '#1C1C1C'
  on-background: '#F9F5F0'
typography:
  display-lg:
    fontFamily: Playfair Display
  body-lg:
    fontFamily: Hanken Grotesk
---
## Midnight Creole Style
Une ambiance plus organique et nocturne pour l'expérience de dégustation. 
L'accent est mis sur l'or et les tons terreux sur un fond noir pur.