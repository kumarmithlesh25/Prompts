# Analysis Prompts

## Data Summarization
Summarize large datasets or documents into key insights and takeaways.

```
Analyze the following data/document and provide:
1. Executive summary (2-3 sentences)
2. Key findings (bullet points)
3. Notable patterns or anomalies
4. Actionable recommendations

Data/Document:
[INSERT CONTENT]
```

## Comparative Analysis
Compare multiple items, options, or approaches across defined criteria.

```
Compare the following items across these dimensions: [CRITERIA]

Items to compare:
[ITEM 1]
[ITEM 2]
[ITEM 3]

Provide a structured comparison table followed by a recommendation with reasoning.
```

## Root Cause Analysis
Identify underlying causes of problems or issues.

```
Analyze the following problem and perform a root cause analysis:

Problem: [DESCRIBE PROBLEM]
Context: [RELEVANT BACKGROUND]

Provide:
1. Immediate cause
2. Contributing factors
3. Root cause(s)
4. Evidence supporting your analysis
5. Recommended corrective actions
```

## Screenshot Analysis
Perform detailed, pixel-perfect analysis of screenshots for UI/UX review, bug identification, or design verification.

```
Analyze this screenshot with pixel-level precision:

[INSERT SCREENSHOT]

Context: [PURPOSE - e.g., UI review, bug report, design verification, accessibility audit]

Provide a comprehensive analysis covering:

1. **Visual Inventory**
   - All UI elements present (buttons, text, icons, images, forms)
   - Layout structure and hierarchy
   - Color values and typography observed

2. **Pixel-Perfect Details**
   - Alignment issues (misaligned elements, inconsistent spacing)
   - Spacing measurements (padding, margins, gaps)
   - Border styles, shadows, and visual effects
   - Text rendering (font sizes, weights, line heights)

3. **Visual Inconsistencies**
   - Color mismatches or unexpected values
   - Truncated or overlapping content
   - Rendering artifacts or glitches
   - Broken or missing assets

4. **Interaction States** (if applicable)
   - Current state of interactive elements
   - Hover/focus/active indicators visible
   - Disabled or loading states

5. **Accessibility Observations**
   - Color contrast concerns
   - Text legibility issues
   - Touch target sizes
   - Missing visual indicators

6. **Specific Findings**
   - List each issue with exact location (coordinates or element reference)
   - Severity rating (critical/major/minor/cosmetic)
   - Suggested fix if apparent

Additional focus areas: [SPECIFIC ASPECTS TO EXAMINE - e.g., header alignment, form validation states, responsive breakpoint issues]
```

## Mobile App Analysis
Comprehensive analysis of a mobile app's UI/UX, functionality, and design quality from screenshots or App Store listing.

```
Analyze this mobile app based on the provided materials:

[INSERT APP STORE LINK OR SCREENSHOTS]

App Context: [APP NAME, CATEGORY, TARGET AUDIENCE]

Provide a comprehensive analysis covering:

1. **App Store Presence** (if link provided)
   - App description clarity and effectiveness
   - Rating and review sentiment summary
   - Common user complaints and praises
   - Update frequency and developer responsiveness

2. **Visual Design Assessment**
   - Design system consistency (colors, typography, iconography)
   - Brand identity and visual appeal
   - Use of whitespace and visual hierarchy
   - Platform design guidelines adherence (iOS HIG / Material Design)

3. **UX Patterns & Navigation**
   - Navigation structure (tab bar, drawer, stack)
   - Information architecture clarity
   - User flow logic between screens
   - Gesture and interaction patterns used

4. **Screen-by-Screen Breakdown**
   For each screenshot provided:
   - Screen purpose and functionality
   - UI elements and their arrangement
   - Content density and readability
   - Call-to-action clarity
   - Potential usability issues

5. **Accessibility Evaluation**
   - Text sizes and readability
   - Color contrast adequacy
   - Touch target sizes (minimum 44x44pt iOS / 48x48dp Android)
   - Support for system accessibility features (visible indicators)

6. **Competitive Positioning**
   - Strengths compared to typical apps in category
   - Areas needing improvement
   - Unique differentiators observed

7. **Recommendations**
   - Critical issues to address (priority order)
   - Quick wins for improvement
   - Feature or design suggestions

Analysis focus: [SPECIFIC ASPECTS - e.g., onboarding flow, checkout experience, settings screen, dark mode implementation]
```
