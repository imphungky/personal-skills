---
name: setup-repository
description: Set up a new project directory and public GitHub repository from a named project idea. Use only when the user directly invokes this skill or explicitly asks to set up/bootstrap a repository.
---

# Setup Repository

## Trigger

Use only for a direct request such as `setup-repository for <project idea>` or an explicit request to set up/bootstrap a new repository. Do not activate for general project brainstorming or vague mentions of a project.

## Inputs

- Require a project name or idea. Ask if it is missing.
- Use the user-provided location when specified; otherwise use `C:\Users\PC\Projects\<project-slug>`.
- Derive a lowercase, hyphen-separated slug unless the user specifies one.

## Workflow

1. Check whether the target directory already exists. If it is non-empty, stop and ask before changing it.
2. Check Git and GitHub CLI availability and authentication. If GitHub authentication is unavailable, explain what is needed and do not create a partial public-repository setup.
3. Create the project directory.
4. Create only `README.md` before the first commit. Its initial content must be a single Markdown title using the project’s display name, for example:
   ```md
   # Pi Whiteboard
   ```
5. Initialize Git with `main` as the initial branch.
6. Stage only `README.md` and create the initial commit.
7. Create a public GitHub repository using the authenticated account, add it as `origin`, and push `main`.
8. Verify the clean working tree, current branch, initial commit contents, remote URL, and public repository URL.

## Safety and Completion

- Never delete, overwrite, or reuse an existing directory or remote without explicit confirmation.
- Do not add `.gitignore`, licenses, source files, or other scaffolding before the initial commit unless the user explicitly requests it.
- If a remote repository with the target name already exists, stop and ask whether to use it; do not silently alter it.
- Report the local path, repository URL, branch, commit, and initial file list when complete.
