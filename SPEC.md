# KodNest Premium Build System - Design Specification

## 1. Design Philosophy
- **Calm** - No visual noise, serene interactions
- **Intentional** - Every element serves a purpose
- **Coherent** - Unified visual language across all components
- **Confident** - Bold typography, clear hierarchy, no hesitation

## 2. Design Anti-Patterns (Avoid)
- No gradients
- No glassmorphism
- No neon colors
- No animation noise
- No playful elements
- No hackathon-style aesthetics
- No decorative fonts
- No random spacing values

## 3. Color System

### Primary Colors
| Token | Hex | Usage |
|-------|-----|-------|
| `--color-bg` | #F7F6F3 | Page background, cards |
| `--color-text` | #111111 | Primary text, headings |
| `--color-accent` | #8B0000 | Primary buttons, links, emphasis |
| `--color-success` | #2D5A3D | Success states, confirmations |
| `--color-warning` | #8B7355 | Warning states |
| `--color-border` | #E5E4E0 | Borders, dividers |
| `--color-muted` | #6B6B6B | Secondary text, placeholders |

### Implementation
- Maximum 4 colors across entire system: Background, Text, Accent, Muted
- Success and Warning are derived/semantic colors for specific states

## 4. Typography

### Font Families
- **Headings**: "Cormorant Garamond", Georgia, serif
- **Body**: "DM Sans", -apple-system, sans-serif

### Type Scale
| Element | Size | Weight | Line Height | Max Width |
|---------|------|--------|-------------|-----------|
| H1 | 48px | 600 | 1.2 | 720px |
| H2 | 36px | 600 | 1.25 | 720px |
| H3 | 24px | 600 | 1.3 | 720px |
| Body | 17px | 400 | 1.7 | 720px |
| Small | 14px | 400 | 1.5 | none |
| Caption | 12px | 500 | 1.4 | none |

### Letter Spacing
- Headings: 0.02em (generous)
- Body: 0.01em (slight)

## 5. Spacing System

### Scale
| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | 8px | Tight spacing, icon gaps |
| `--space-sm` | 16px | Component internal padding |
| `--space-md` | 24px | Section spacing |
| `--space-lg` | 40px | Major section gaps |
| `--space-xl` | 64px | Page-level whitespace |

### Implementation Rules
- NEVER use random values like 13px, 27px, 31px
- Always use scale values
- Whitespace is a design element

## 6. Layout Structure

### Global Layout (Every Page)
```
┌─────────────────────────────────────────────────────────────┐
│ TOP BAR (56px height)                                       │
│ [Logo/Name] ─────────── [Progress: Step X / Y] ─── [Badge] │
├─────────────────────────────────────────────────────────────┤
│ CONTEXT HEADER                                              │
│ [H1 Headline]                                               │
│ [Subtext - single line, purposeful]                         │
├───────────────────────────────────┬─────────────────────────┤
│ PRIMARY WORKSPACE (70%)           │ SECONDARY PANEL (30%)  │
│                                   │                         │
│ [Main product interaction]        │ [Step explanation]      │
│ [Clean cards]                     │ [Copyable prompt]      │
│ [Predictable components]          │ [Action buttons]       │
│                                   │                         │
├───────────────────────────────────┴─────────────────────────┤
│ PROOF FOOTER (persistent)                                   │
│ [□ UI Built] [□ Logic Working] [□ Test Passed] [□ Deployed]│
└─────────────────────────────────────────────────────────────┘
```

## 7. Component Specifications

### Top Bar
- Height: 56px
- Background: #F7F6F3
- Border-bottom: 1px solid var(--color-border)
- Left: Project name (Cormorant Garamond, 20px, 600)
- Center: Progress "Step X / Y" (DM Sans, 14px, 500)
- Right: Status badge (pill shape, appropriate color)

### Status Badges
- Not Started: Muted background (#E5E4E0), muted text
- In Progress: Accent background (light), accent text
- Shipped: Success background (light), success text
- Border-radius: 100px
- Padding: 4px 12px

### Context Header
- Padding: 40px 0 40px 0
- H1: 48px, serif, 600 weight
- Subtext: 17px, sans-serif, muted color, max 600px width

### Primary Workspace
- Width: 70%
- Padding-right: 24px
- Contains: Cards, forms, interactive elements

### Secondary Panel
- Width: 30%
- Background: slightly different shade or bordered
- Contains:
  - Step explanation (small heading)
  - Short description (14px, muted)
  - Copyable prompt box (code block styling)
  - Action buttons

### Cards
- Background: #FFFFFF
- Border: 1px solid var(--color-border)
- Border-radius: 8px
- Padding: 24px
- No shadows (subtle only if absolutely necessary)

### Buttons

#### Primary Button
- Background: var(--color-accent) #8B0000
- Text: #FFFFFF
- Border: none
- Border-radius: 6px
- Padding: 12px 24px
- Font: DM Sans, 15px, 500
- Hover: Darken 10%
- Transition: 150ms ease-in-out

#### Secondary Button
- Background: transparent
- Text: var(--color-accent)
- Border: 1.5px solid var(--color-accent)
- Border-radius: 6px
- Padding: 12px 24px
- Font: DM Sans, 15px, 500
- Hover: Light accent background
- Transition: 150ms ease-in-out

#### Button Sizes
- Small: padding 8px 16px, font 14px
- Medium: padding 12px 24px, font 15px
- Large: padding 16px 32px, font 16px

### Inputs
- Border: 1.5px solid var(--color-border)
- Border-radius: 6px
- Padding: 12px 16px
- Font: DM Sans, 15px
- Background: #FFFFFF
- Focus: border-color var(--color-accent), outline none
- Placeholder: var(--color-muted)

### Copyable Prompt Box
- Background: #F7F6F3
- Border: 1px solid var(--color-border)
- Border-radius: 6px
- Padding: 16px
- Font: DM Sans Mono or monospace, 13px
- Max-height: 200px
- Overflow-y: auto

### Proof Footer Checklist
- Background: #FFFFFF
- Border-top: 1px solid var(--color-border)
- Padding: 16px 24px
- Display: flex, gap 32px
- Each item: Checkbox + label
- Checkbox: Custom styled, accent color when checked

## 8. Interaction Rules

### Transitions
- Duration: 150ms - 200ms
- Easing: ease-in-out
- No bounce
- No parallax
- No spring animations

### Hover States
- Buttons: Subtle darken/lighten
- Links: Underline or color shift
- Cards: Slight border color change (optional)

### Focus States
- Always visible focus indicator
- Accent color ring or border change
- Never remove focus outlines

## 9. Error & Empty States

### Error States
- Clear error message explaining what went wrong
- Provide actionable fix guidance
- Never blame user
- Use muted red styling

### Empty States
- Provide next action
- Never feel dead or abandoned
- Include primary action button

## 10. Responsive Breakpoints
- Desktop: 1200px+
- Tablet: 768px - 1199px
- Mobile: < 768px

## 11. Implementation Notes

### CSS Custom Properties
All values exposed as CSS custom properties for theming and maintenance.

### BEM Naming
Components use BEM naming convention for clarity.

### Accessibility
- Semantic HTML
- ARIA labels where needed
- Color contrast compliant
- Keyboard navigable
