# Survey Design System

A reusable design system for KoboToolbox surveys developed as part of the research project on the video game industry in Central America.

This repository centralizes the visual identity, reusable HTML components, graphical assets, and documentation used to build consistent, professional, and accessible surveys across the project.

---

## Objectives

- Provide a consistent visual identity for all project surveys.
- Reuse HTML components across multiple KoboToolbox forms.
- Maintain a centralized collection of logos, icons, and illustrations.
- Simplify the maintenance of survey interfaces.
- Prototype interfaces before implementing them in KoboToolbox.

---

## Repository Structure

```
survey-design-system/
│
├── assets/          # Logos, icons and illustrations
├── branding/        # Color palette and visual guidelines
├── components/      # Reusable HTML blocks
├── playground/      # HTML prototypes for testing layouts
└── styles/          # Global stylesheet
```

---

## Components

The design system is organized into reusable interface components.

| Component | Description |
|-----------|-------------|
| Header | Institutional logos and survey title |
| Hero | Welcome section |
| Cards | Summary information cards |
| Project | Institutional information |
| Footer | Closing section |

---

## Design Principles

The interface follows a simple set of principles:

- Clear visual hierarchy
- Clean and modern appearance
- Institutional and academic style
- Mobile-friendly layouts
- Accessible color palette
- Reusable components
- Minimal visual noise

---

## Color Palette

| Role | Color |
|------|-------|
| Primary | `#5B3FB5` |
| Green | `#45C04B` |
| Pink | `#F03E93` |
| Blue | `#2C82E8` |
| Text | `#444444` |
| Background | `#FFFFFF` |
| Surface | `#FAFAFA` |
| Border | `#E7E7E7` |

---

## Icons

This project uses **Tabler Icons**.

https://tabler.io/icons

All icons are stored as SVG files inside:

```
assets/icons/
```

---

## Hero Illustration

The landing page uses a custom vector illustration stored in:

```
assets/hero/
```

The illustration should remain simple, modern, and consistent with the overall visual identity.

---

## Development Workflow

1. Design and test layouts in `playground/`.
2. Extract reusable sections into `components/`.
3. Adapt the HTML for KoboToolbox / Enketo.
4. Copy the final HTML into the corresponding XLSForm notes.

---

## Target Platforms

- KoboToolbox
- Enketo
- XLSForm

---

## License

MIT — see [LICENSE](LICENSE).
