# Momentum Agency - Design Guidelines

## Design Approach

**Reference-Based Strategy**: Drawing inspiration from modern digital agencies (Vercel, Linear) combined with creative studio aesthetics (Awwwards-winning agencies). Focus on professional credibility while showcasing creative capability.

**Core Principles**:
- Bold confidence through typography and generous whitespace
- Strategic visual moments rather than continuous decoration
- Professional polish with creative edge
- Trust-building through clarity and restraint

---

## Typography System

**Primary Font**: Inter (Google Fonts) - clean, professional, excellent readability
**Accent Font**: Space Grotesk (Google Fonts) - geometric, distinctive for headlines

**Hierarchy**:
- Hero Headlines: Space Grotesk, text-6xl to text-7xl, font-bold, tracking-tight
- Section Headers: Space Grotesk, text-4xl to text-5xl, font-bold
- Subheadings: Inter, text-xl to text-2xl, font-semibold
- Body Text: Inter, text-base to text-lg, font-normal, leading-relaxed
- Small Text/Captions: Inter, text-sm, font-medium

---

## Layout System

**Spacing Primitives**: Use Tailwind units of 4, 6, 8, 12, 16, 20, 24 for consistent rhythm
- Component padding: p-6, p-8, p-12
- Section spacing: py-16, py-20, py-24 (desktop), py-12, py-16 (mobile)
- Element gaps: gap-4, gap-6, gap-8

**Container Strategy**:
- Full-width sections with inner max-w-7xl
- Content sections: max-w-6xl
- Text blocks: max-w-3xl for readability

**Grid Patterns**:
- Services/Features: 3-column grid (lg:grid-cols-3, md:grid-cols-2, grid-cols-1)
- Portfolio/Case Studies: 2-column alternating layout
- Testimonials: 2-column cards

---

## Component Library

### Navigation
- Fixed/sticky header with logo left, navigation center/right
- Clean link styling with subtle underline animations
- Mobile: hamburger menu with full-screen overlay
- CTA button in navigation with distinct treatment

### Hero Section
- **Large hero image required**: Full-width, high-quality agency workspace or abstract creative visual
- Overlay with gradient for text readability
- Headline + supporting text + dual CTAs (primary + secondary)
- Height: min-h-screen on desktop, min-h-[70vh] on mobile
- Buttons on image backgrounds: backdrop-blur-md with semi-transparent backgrounds

### Services/Capabilities Grid
- Icon + Title + Description cards
- Use Heroicons (via CDN)
- Even spacing, subtle hover elevation
- 3-column layout collapsing to single column

### Case Studies/Portfolio
- Alternating image-text layout
- Large project images (use placeholder: "High-quality project showcase images")
- Project title, brief description, key metrics/results
- "View Case Study" links with arrow indicators

### Client Logos/Trust Section
- Grayscale logo grid showing "Trusted by" companies
- 4-6 logos in single row on desktop, 2-3 on mobile
- Subtle opacity hover effect

### Team Section (if applicable)
- Photo grid of team members
- Name + role below each photo
- 3-4 column layout
- Use placeholder: "Professional team headshot photos"

### Testimonials
- Card-based layout with quote, author name, company, role
- Author photo (small circular)
- 2-column on desktop, single column mobile
- Subtle card elevation

### Contact Form
- Full-width section with 2-column layout
- Left: Form (Name, Email, Message fields)
- Right: Contact info (address, phone, email) + office hours
- Form styling: clean borders, focus states with accent treatment
- Submit button with loading state support

### Footer
- 3-column layout: Company info, Quick links, Newsletter signup
- Social media icons (use Font Awesome via CDN)
- Copyright and legal links
- Generous padding (py-16)

---

## Interaction Patterns

**Minimal Animation Strategy**:
- Subtle fade-in on scroll for section reveals (use Intersection Observer)
- Smooth anchor scrolling for navigation
- Button hover: slight scale (scale-105) with transition
- Card hover: subtle elevation increase (shadow-lg)
- No complex animations or parallax effects

**Form Interactions**:
- Clear focus states (ring-2 with accent)
- Inline validation feedback
- Success/error states with appropriate messaging

---

## Images

**Required Images**:
1. **Hero Background**: Modern agency workspace or abstract creative composition (full-width, high-res)
2. **Case Study Images**: 3-4 project showcase images showing completed work
3. **Team Photos**: Professional headshots of team members (circular cropped)
4. **Client Logos**: 5-6 recognizable brand logos (grayscale treatment)

**Image Treatment**:
- Hero: Subtle gradient overlay for text contrast
- Case studies: Sharp, full-quality images with slight rounded corners (rounded-lg)
- Team: Circular crop (rounded-full), consistent sizing
- All images: Aspect ratios maintained, lazy loading enabled

---

## Accessibility Implementation

- Skip to main content link (visible on focus)
- Semantic HTML throughout (nav, main, section, article tags)
- ARIA labels for icon-only buttons
- Form labels properly associated
- Color contrast ratios meeting WCAG AA standards
- Focus indicators clearly visible
- Alt text for all images with meaningful descriptions

---

## Special Components

**Cookie Consent Banner**:
- Bottom-fixed position
- Clear messaging about analytics usage
- Accept/Decline buttons with equal visual weight
- Dismissible with localStorage persistence

**Analytics Wrapper**:
- Respects user consent
- No tracking before consent given
- Clear opt-out capability

This design creates a professional, trustworthy agency presence while allowing for creative expression through bold typography, strategic imagery, and clean modern aesthetics.