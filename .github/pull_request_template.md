# Pull Request

## What Changed
Describe the changes introduced in this pull request.

Include specific details such as:
- New files or features added
- Existing code that was modified
- Any files that were removed or refactored

Example:
- Added `.github/pull_request_template.md` to standardize pull request descriptions.
- Added `docs/pr-checklist.md` containing a personal self-review checklist.
- Updated `README.md` with a **How to run** section explaining how to set up and execute the project.

---

## Why
Explain the purpose of these changes.

This pull request improves repository collaboration and code review quality by introducing a structured pull request template and a personal pre-PR checklist.  
The template helps contributors clearly explain what was changed, why the change was needed, and how reviewers can verify the results.  
The checklist encourages authors to review their work before opening a PR, reducing errors and improving code quality.

---

## How to Test
Follow these steps to verify that the repository works correctly:

1. Clone the repository.
2. Navigate to the project directory.
3. Activate the virtual environment:
   - Windows: `source .venv/Scripts/activate`
   - Mac/Linux: `source .venv/bin/activate`
4. Install dependencies if required.
5. Run the project or tests according to the instructions in the `README.md`.
6. Confirm that the environment activates successfully and the commands run without errors.

---

## Checklist
Before submitting this pull request, I confirm that:

- [ ] The changes match the purpose described in this PR
- [ ] The code runs correctly in the local environment
- [ ] All tests pass successfully
- [ ] No debug code (print statements, breakpoints) remains
- [ ] Documentation has been updated where necessary
- [ ] The PR focuses on a single logical change
