# Contribution 1: 🚀 Feature: Indicate errors to the user, if possible

**Contribution Number:** 1  
**Student:** Julianne Tomlinson  
**Issue:** https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/2  
**Status:** Phase I - Complete  

---

## Why I Chose This Issue

I chose [this issue](https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/2), "Indicate errors to the user, if possible", because it aligns with my current TypeScript and JavaScript experience. I wanted to become familiar with the repository and the contributing experience before challenging myself with unfamiliar coding languages and frameworks. The issue is labeled "good for new contributors", is currently accepting PRs, and has clear acceptance criteria in the description. The onboarding process doesn't seem too complex either.

I'm interested in this because:
1. It's frontend specific, which is my strong suit.
2. I wanted to learn about Google Chrome extentions and how to code them.
3. The maintainer seems supportive and kind.

From reading the issue description, I understand the current problem is that users aren't getting clear feedback on the UI regarding unsuccessful loading of the replies.yml files in their chosen repository. There should be an indication of this on screen in the Saved Replies dropdown to show that there might be replies missing. If the dropdown isn't on screen at the time of the error, there should be a console error.

I left a comment on the issue introducing myself, asking if the issue was still unsolved and open [Waiting for response]

---

## Understanding the Issue

### Problem Description

Currently, when the replies.yml file cannot be accessed in the repository, there is no visual indication to the user for this. At the moment, there is only a log within the console itself.

### Expected Behavior

When the necessary file cannot be read, then there should be an error that displays in the saved replies dropdown indicating this.

### Current Behavior

Currently, the error is logged in the console which is not clear to the users.

### Affected Components

[Which parts of the codebase are involved?]

The `fetchRepliesConfiguration.ts` file is where the error code exists. If the frontend api fails to fetch the replies from the current repository, the error response is only located in the console. There is no UI that indicates the error or possible resolution of the error to the user.

## Reproduction Process

### Environment Setup

Setting up the local development environment was easier than I first believed it to be. I just had to clone the repository and install the dependencies and recommended extensions. I found the file that would need to be altered fairly quickly as well. The interesting thing about Google extensions is that I can use the developer mode to upload the source code (after creating a build of the code) and I can use the extension locally.

A problem that I have run into this week is that I cannot reproduce the issue as the Saved replies feature doesn't seem to be functioning as expected. I'm going to look into it more this upcoming week and see if it is a user error or an issue with the repository I've chosen.

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

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
