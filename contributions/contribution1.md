# Contribution 1: 🐛 Bug: Error when accessing elements on issue page

**Contribution Number:** 1  
**Student:** Julianne Tomlinson  
**Issue:** [https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/1443](https://github.com/JoshuaKGoldberg/refined-saved-replies/issues/1443)  
**Status:** Phase III - Completed

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

We should be able to proceed with the program, search the repository to see if they have a global file for their specific repository replies (`.github/replies.yml`), and display the repository replies in the saved replies pop up.

### Current Behavior

Currently, there is an error finding the element and the program exits early. The program exits in the first few lines of the main function file (`content-script.ts`) due to the fact that the attribute name that is used no longer follows GitHub's UI naming convention. This causes the program to quit as the element cannot be found on the page.

### Affected Components

[Which parts of the codebase are involved?]

The `content-script.ts` file is where the code errors out.

## Reproduction Process

### Environment Setup

Setting up the local development environment was easier than I first believed it to be. I just had to clone the repository, install the dependencies and recommended extensions, go to my Google extensions and switch it to development mode, and upload the code that I cloned to run the extension on a site. As I make changes, all I need to do is create a new build and refresh the extension to see the changes locally.

I found the file that would need to be altered fairly quickly as well. The interesting thing about Google extensions is that I can use the developer mode to upload the source code (after creating a build of the code) and I can use the extension locally.

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

**Implement:** [My branch](https://github.com/JewlzT/refined-saved-replies/tree/bugfix/update-element-queries)

**Review:** This issue and my UMPIRE plan follows the repository's [code of conduct](https://github.com/JewlzT/refined-saved-replies/blob/main/.github/CODE_OF_CONDUCT.md) and the [contributing docs](https://github.com/JewlzT/refined-saved-replies/blob/main/.github/CONTRIBUTING.md).

**Evaluate:** I will verify it works through console logging when I create it and making tests so that the process will return an error to future developers in the case that GitHub makes updates that breaks the flow.

---

## Testing Strategy

### Unit Tests
- [x] Test case 1 [Manual]: Console log through user flow and make sure everything is working as expected (deleted before final push)
- [x] Test case 2 [Unit Test]: Update tests to include the new object shape in `fetchSettings.ts` (The tests were failing due to the fact that the returned object looked different than what was expected in the tests. This was expected as I altered the return when implementing the fix)
- [x] Test case 3 [Unit Test]: Create new unit tests for the added itemDetails in `fetchSettings.ts`

I plan to write some to avoid this bug in the future.
Update: These test cases require e2e testing that does not currently exist within the workings of this application. I'm going to have a discussion with the maintainer about this and see if this is something I could implement as an additional PR because it requires a bit of research.

Extra: Check for valid replies button query (use both issue link and PR link to make sure that the attribute is still valid)
Extra: Check for valid comment section query (use both issue link and PR link to make sure that the attribute is still valid)

### Manual Testing

I added console logs throughout while testing attributes I could use in the query to make sure I was accessing the proper elements. By using the logs, I better understand the flow of the application and I was able to break down the updates needed in steps. I am trying to make my commits as atomic as possible as well.

---

## Implementation Notes

### Week 5 Progress

I updated the queries and created logs to check the flow. Now we successfully access the button, the comment field, and the repository replies that we plan to add in the Saved Replies dropdown. Here is the [commit](https://github.com/JewlzT/refined-saved-replies/commit/d0f3846eec30e79c7c182872c0cb0e730286d635) showing this progress.

### Week 6 Progress

I have successfully fixed the issue for both pull requests and issues. There is a visual bug when using the saved replies feature for the issues page due to GitHub's UI update (the repository reply is squished and illegible). I plan to fix this during this upcoming week. Here is my weekly [commit](https://github.com/JewlzT/refined-saved-replies/commit/4c460f1180db26943be108200dbd405d1ac427c4).

### Week 7 Progress

I have figured out what the visual bug is. Unfortunately, it's very dependent on the way that GitHub has altered their UI. There is quite a significant difference between the saved replies for the issues and for the PRs. This means that almost the entirety of the `content-script.ts` file will have to be written for issues alone and for PRs alone so that the display is legible and works correctly. My commit this week was my attempt at creating a reusable function. Unfortunately, I'll have to scrape this idea because their are so many additional elements that having variable classnames is not enough. I'll have to split the code into two branches, one for the PR page and one for the issues page. Here is my weekly [commit](https://github.com/JewlzT/refined-saved-replies/commit/eefe81f2c1d31ad2375199d834b61890cb75ddb0).

### Week 8 Progress

I fixed the visual issues and have created a working prototype! There is a bug when it comes to filtering the new repository replies when searching, which I am currently fixing. Other than that, everything is working as expected. I'm going to be cleaning code and creating test cases this week. Here is my weekly [commit](https://github.com/JewlzT/refined-saved-replies/commit/dabe7048acc8e1b9b3d6ebc432c0f24d719c05a2).

### Week 9 Progress

The bug exists in both sections which is out of the scope of this issue, so I will create an issue in the future for it so I don't scope creep. I've cleaned the code, fixed the broken tests, and created new ones for my implementation. I am finished with Phase 3 and will be submitting the PR soon. Here are my weekly commits:[fixed ui and cleaned code](https://github.com/JewlzT/refined-saved-replies/commit/ae371c4f425f218883c7f4dae455b37db811f4d9) and [updated testing suite](https://github.com/JewlzT/refined-saved-replies/commit/94b6b5fc16f9c1d7600a98511bcc5167f5528c3d)

### Code Changes

- **Files modified:** `content-script.ts`, `fetchSettings.ts`, `fetchSettings.test.ts`, `validations.ts`, `types.ts`
- **Key commits:** [Week 5 commit](https://github.com/JewlzT/refined-saved-replies/commit/d0f3846eec30e79c7c182872c0cb0e730286d635), [Week 6 commit](https://github.com/JewlzT/refined-saved-replies/commit/4c460f1180db26943be108200dbd405d1ac427c4), [Week 8 commit](https://github.com/JewlzT/refined-saved-replies/commit/dabe7048acc8e1b9b3d6ebc432c0f24d719c05a2), [Week 9 commit 1](https://github.com/JewlzT/refined-saved-replies/commit/ae371c4f425f218883c7f4dae455b37db811f4d9), [Week 9 commit 2](https://github.com/JewlzT/refined-saved-replies/commit/94b6b5fc16f9c1d7600a98511bcc5167f5528c3d)
- **Approach decisions:** I have decided to split the code into two large sections: one for pull requests and one for issues. Depending on which one you are commenting on, the elements that are being accessed and the UI is completely difference. I believe this separation will be clearer for future developers to update rather than the current layout which assumes the UI is the same for both issues and PRs.

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
