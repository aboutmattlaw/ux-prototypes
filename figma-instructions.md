# **FIGMA IMPLEMENTATION: MANDATORY RULES**

## **CRITICAL WORKFLOW - DO NOT SKIP**
1. **Run `get_design_context`** for exact node(s)
2. **If truncated**: Run `get_metadata` for node map, then re-fetch specific nodes
3. **Run `get_screenshot`** for visual reference
4. Only after you have both get_design_context and get_screenshot, download any assets needed and start implementation.
5. **Download ALL assets** before starting implementation
6. **Translate to project conventions** - reuse project tokens, components, typography
7. **Validate 1:1** against Figma before marking complete

---

## **TECH STACK**
- React + TypeScript
- Tailwind CSS + Styled Components
- Design tokens: `/tokens/ios-tokens-json.txt`
- Assets: `/assets/fonts`, `/assets/stores`, `/assets/logos`

---

## **NON-NEGOTIABLE RULES**

### **Assets**
- **NEVER start without all assets downloaded and organized**
- **NO placeholders, Lorem Picsum, or temporary graphics**
- Export directly from Figma, organize by type (`/images/`, `/icons/`, `/fonts/`)
- Use asset constants file for paths

### **Design Tokens**
- **ALWAYS use tokens when they exist**
- **Document ALL non-token values** with comments explaining why
- **Flag repeated non-token values** (3+ uses) for design system addition

### **Non-Token Value Decision Tree**
1. **Close match exists?** (<2px difference) → Use token with comment
2. **One-time use?** → Use exact value, document reason
3. **Repeated use?** → Create constant, flag for design system
4. **When unclear** → Use `AskUserQuestion`

**Never:**
- Round without documenting
- Ignore significant differences (3+px)
- Add repeated values without flagging

### **Pixel-Perfect Requirements**
**Match exactly:**
- Colors (use color picker)
- Spacing (margins, padding, gaps)
- Typography (font, size, weight, line-height)
- Border radius, borders, shadows
- Icon size and color

**Test all states:**
- Hover, active, disabled, focus, loading

**Test all breakpoints:**
- Mobile-first approach
- No horizontal scroll on mobile
- Touch targets ≥44x44px

### **Quality Standards**
- **Pixel-perfect** unless explicitly discussed
- **Type-safe** props and state
- **Accessible** (semantic HTML, ARIA, keyboard nav)
- **Component names** match Figma exactly (convert to PascalCase)
- **No over-engineering** - only build what's requested

---

## **IMPLEMENTATION CHECKLIST**

### **Before Starting**
- [ ] All assets downloaded, organized, and verified
- [ ] Design tokens extracted
- [ ] Non-token values identified and clarified
- [ ] All design references available locally

### **Before Marking Complete**
- [ ] Tokens used where they exist
- [ ] Non-token values documented with reasoning
- [ ] Assets properly imported with correct paths
- [ ] Matches Figma at all breakpoints
- [ ] All variants and states implemented
- [ ] TypeScript types defined
- [ ] Accessibility requirements met
- [ ] Visual QA passed
- [ ] Repeated non-token values flagged

---

## **COMMON VIOLATIONS (DON'T DO THIS)**
1. Starting without assets downloaded
2. Using placeholder graphics or Lorem Ipsum
3. Hardcoding values without comments
4. Rounding non-token values silently
5. Ignoring hover/focus states
6. Skipping accessibility
7. Desktop-first design (must be mobile-first)
8. Missing responsive testing
9. Forgetting edge cases (empty states, long text, missing images)
10. Adding repeated non-token values without flagging

---

## **CODE PATTERNS**

### **Component Structure**
```typescript
interface Props {
  variant: 'primary' | 'secondary';
  size: 'small' | 'medium' | 'large';
  children: React.ReactNode;
}

export const Component: React.FC<Props> = ({ variant, size, children }) => {
  // Implementation
};
```

### **Asset Constants**
```typescript
// src/constants/assets.ts
export const IMAGES = {
  hero: '/images/hero/homepage.jpg',
} as const;
```

### **Non-Token Documentation**
```typescript
// One-off value
padding-top: 72px; /* Specific hero spacing, not in design system */

// Pending token
font-size: 13px; /* TODO: Add to typography scale */

// Intentional deviation
border-radius: 6px; /* Uses 6px not 8px token per marketing requirements */
```

### **Responsive Layout**
```tsx
// Mobile-first approach
<div className="
  flex flex-col gap-4          // Mobile: stack vertically
  md:flex-row md:gap-6         // Tablet: horizontal
  lg:gap-8                     // Desktop: more spacing
">
```

---

**Remember: Measure twice, code once. Every pixel matters.**
