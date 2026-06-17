# Contribution [1]: [Add display of current value to slider parameters]

**Contribution Number:** 1 
**Student:** Prativa Khatiwada
**Issue:** https://github.com/jscad/OpenJSCAD.org/issues/708
**Status:** Phase II In Progress

---

## Why I Chose This Issue
---

I picked this issue because I enjoy working with JavaScript and the idea behind OpenJSCAD genuinely interests me. I think the open source project itself is a really cool concept, being able to easily produces a 3D printable object. I enjoy working with javascript as well and it would be interesting as well as a learning curve to explore this unfamilar codebase in order to provide a satisfying UX fix. Right now users can drag sliders to change model parameters but there's no number shown, so you're kind of just guessing. Adding a live value display makes the whole experience feel more intuitive, and that type of small improvement that makes something noticeably better. 

## Understanding the Issue

### Problem Description

When a user loads a design with slider parameters (like the "All Parameter Types" example), they can drag the slider to change values but there is no number shown anywhere. You have no way of knowing what value you've actually set the parameter to.
### Expected Behavior

As the user moves a slider, the current numeric value should be displayed next to it and update in real time as the slider is dragged.
### Current Behavior

The slider renders and can be moved, but value is not shown on load, while dragging, or after releasing.
### Affected Components

The main file to look at is packages/web/src/ui/views/parameterControls.js — this is where the web UI builds the HTML controls for each parameter type, including sliders. The fix will likely involve adding a <span> or similar element next to the <input type="range"> and wiring up an input event listener to update it as the slider moves.

---

## Reproduction Process

### Environment Setup

Clone the repo, navigate to packages/web, and copy the examples folder across. Then spin up a local web server in that directory (a simple npx serve . or python -m http.server works). No build step is needed to view the UI locally.

### Steps to Reproduce

1. Open the web UI in a browser and load the "All Parameter Types" example from the examples dropdown
2. Find the slider control in the parameter panel on the left
3. Click and drag the slider, notice that no numeric value appears anywhere near it

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
