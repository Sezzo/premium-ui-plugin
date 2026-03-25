# Prompt 03: Token Architecture — E-Commerce Platform

## Prompt

```
Define a complete token architecture for a premium e-commerce platform.

Brand: Minimalist luxury fashion retailer. Think Acne Studios or COS — clean, restrained, confident. No loud colors, no playful elements. The brand communicates through whitespace, typography, and subtle material quality.

Requirements: Light and dark theme support, responsive (mobile-first), must support product photography as the primary visual element.
```

## Expected Output Should Include

- **Color tokens**: Primitives + semantic tokens with light/dark values
- **Typography tokens**: Full type scale with sizes, weights, line heights, tracking
- **Spacing tokens**: Consistent scale (4px/8px base)
- **Border radius tokens**: Likely minimal/restrained for luxury brand
- **Shadow tokens**: Subtle, refined (no heavy drop shadows)
- **Motion tokens**: Duration + easing values
- **Z-index tokens**: Layering system
- **Naming convention**: Documented pattern with examples
- **Brand alignment**: Tokens should reflect minimalist luxury — restrained palette, generous whitespace tokens, refined typography

## Red Flags (Plugin Not Working If...)

- Bright, saturated color palette (contradicts luxury minimalism)
- Large border radius values (playful, not luxury)
- No dark theme values
- Missing token categories (e.g., no motion or z-index)
- Raw hex values used instead of semantic naming
