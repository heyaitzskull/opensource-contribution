# Contribution [1]: [Add display of current value to slider parameters]

**Contribution Number:** 1 
**Student:** Prativa Khatiwada
**Issue:** https://github.com/jscad/OpenJSCAD.org/issues/708
**Status:** Phase III In Progress

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

- **Commit showing reproduction:** N/A
- **Screenshots/logs:** <img width="2443" height="1783" alt="image" src="https://github.com/user-attachments/assets/0ebdf1b8-65bd-426c-8045-b87bf65adb2b" />

---

## Solution Approach

### Analysis

The root cause is simply that when the slider HTML element is created in parameterControls.js, nothing is added alongside it to display its value. The <input type="range"> element exists and works, but the code never creates a text element next to it, and never listens for changes to update one. It's not a bug in the traditional sense — the feature just was never built out.
### Proposed Solution

When the slider control is created, add a small text element right next to it that shows the current value. Then attach an event listener to the slider so that every time the user moves it, that text element updates in real time.

### Implementation Plan
Using UMPIRE framework (adapted):

**Understand**
The slider is rendered in parameterControls.js as an <input type="range">. Users are able to drag it but there is no number shown that makes it difficult to know the exact value of their parameter.

**Match**
Looking at the other input types in the same file (like number inputs or text inputs) are built, it will likely follow the same pattern of creating an element and wiring up an event listener. 
I should make sure that the number addition is in same style so it fits consistently. 

**Plan**
1. Open up packages/web/src/ui/views/parameterControls.js and find where the slider (input type="range") element is
2. After that element is created, create an additional text element (likely a <span>) and set its initial value to the slider's default value
3. Attach an input event listener to the slider that updates every time the slider moves
4. Make sure the span and slider are placed together in the DOM so they render side by side
5. Check the existing test files (*.test.js) to see if there are tests for parameter controls, and possibly add a test case that covers the value display updating on slider change
6. Run npm test inside packages/web to confirm everything passes before pushing

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
