# Follow-up Tasks

## Typo Fix
- **Issue**: The error message shown when GLB loading fails over `file://` includes an extra period inside the URI (`file://.`), which is a typographical error and could confuse users about the correct scheme to use. (See `index.html`, line 103.)
- **Task**: Remove the stray period so the message reads `file://` before the sentence-ending punctuation.

## Bug Fix
- **Issue**: The legacy `setStatus` helper composes the class string using a malformed template literal, yielding values like `${'status'} ok` that prevent status styling from working if the helper is ever called. (See `index.html`, lines 42-45.)
- **Task**: Rewrite the helper (or replace its callers) so it produces `status ok`-style class names.

## Documentation Comment Correction
- **Issue**: The comment `// Fix className (template literal escaped above for safety)` implies the `setStatus` helper is safe, but the helper directly above it is still incorrect, so the comment is misleading. (See `index.html`, lines 44-46.)
- **Task**: Update or remove the comment so it accurately reflects the current behavior (e.g., explain why `setState` exists or remove the unused helper).

## Test Improvement
- **Issue**: There is no automated coverage ensuring the viewer loads the GLB and updates the status text/classes when the reset button is used, leaving regressions undetected. (See `index.html`, lines 42-122.)
- **Task**: Add an automated browser test (e.g., using Playwright) that loads `index.html`, waits for the `Model loaded` status, and verifies the reset button updates the status message and camera state.
