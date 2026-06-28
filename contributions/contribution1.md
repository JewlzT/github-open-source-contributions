# Contribution 1: 🐛 Bug: Error when accessing elements on issue page

**Contribution Number:** 1  
**Student:** Julianne Tomlinson  
**Issue:** [https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/1443](https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/1443)  
**Status:** Phase II - Complete

---

## Why I Chose This Issue

I created [this issue](https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/1443), "Error when accessing elements on issue page", as I ran into a couple of bugs when trying to work on [the contribution I chose before this](https://github.com/JewlzT/github-open-source-contributions/blob/main/contributions/contribution2.md). I realized while attempting to run the previous iteration that the elements were no longer being recognized as GitHub changed their naming conventions since 2023. I plan to update these to unblock other issues. The issue was accepted by the maintainer and is currently accepting PRs.

I'm interested in this because:
1. It's frontend specific, which is my strong suit.
2. I wanted to learn about Google Chrome extentions and how to code them.
3. It's an issue I made and understand.

I created the issue and the maintainer agrees that it is necessary for the program. [Accepted]

---

## Understanding the Issue

### Problem Description

Currently, when the document is being parsed for a specific element, it cannot be found because the query doesn't match the attributes on the current Saved Replies button.

### Expected Behavior

When the correct attribute is accessed, we should be able to proceed with the program and search the user's replies to see if they have a global one for their repository (`.github/replies.yml`).

### Current Behavior

Currently, there is an error finding the element and the program exits early.

### Affected Components

[Which parts of the codebase are involved?]

The `content-script.ts` file is where the code errors out.

## Reproduction Process

### Environment Setup

Setting up the local development environment was easier than I first believed it to be. I just had to clone the repository and install the dependencies and recommended extensions. I found the file that would need to be altered fairly quickly as well. The interesting thing about Google extensions is that I can use the developer mode to upload the source code (after creating a build of the code) and I can use the extension locally.

### Steps to Reproduce

1. Create a console log in the function for finding the element on the screen
2. Activate the developer version of the extension
3. Go to the issue of your choice and open the console
5. Notice that the console log is displaying that the replies button cannot be found

### Reproduction Evidence

- **Screenshots/logs:** <img width="252" height="22" alt="image" src="https://github.com/user-attachments/assets/6bccff0a-2599-479c-af8b-c1d61d092ecd" />
- **My findings:** I get the screenshot above in the logs when the attribute related to the element cannot be found. This appeared although the Saved Replies button was on the screen which means that the attribute it's trying to use is no longer valid.

---

## Solution Approach

### Analysis

The `content-script.ts` file is where the code errors out. The `document.querySelector()` function searches for the element, but cannot find it. This stops the process before anything else can occur.

### Proposed Solution

My idea is to walk my way through the code using console logs to make sure that the necessary elements are being accessed and that the user flow works as intended.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The problem is that the element that needs to be accessed (the Saved replies button) cannot be found due to attribute matching error.

**Match:** The maintainer claimed that this usually happens often, due to GitHub updating and changing. [This issue](https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/161) also had to revamp some aspects because the content needs to be updated when GitHub does any drastic updates.

**Plan:** [Step-by-step implementation plan]
1. Modify  `content-script.ts` file to locate the correct element and stop halting the process prematurely.
2. Continue through the user flow (check `fetchSettings.ts` and `fetchRepliesConfiguration.ts` to make sure that the fetch APIs are getting any repo level replies.
3. Run and update tests to match these changes

**Implement:** [My branch](https://github.com/JewlzT/refined-saved-replies)

**Review:** This issue and my UMPIRE plan follows the repository's [code of conduct](https://github.com/JewlzT/refined-saved-replies/blob/main/.github/CODE_OF_CONDUCT.md) and the [contributing docs](https://github.com/JewlzT/refined-saved-replies/blob/main/.github/CONTRIBUTING.md).

**Evaluate:** I will verify it works through console logging when I create it and making tests so that the process will return an error to future developers in the case that GitHub makes updates that breaks the flow.

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
