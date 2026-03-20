# AI-Usage

This repository is used to collect reusable AI prompt templates.

## Directory Structure

- `prompts/pr-review.prompt.md`: Used to guide AI in performing structured code reviews for any GitHub pull request.

## How to Use `pr-review.prompt.md`

### 1. Select the Prompt

Copy the content of `prompts/pr-review.prompt.md` into your AI assistant (such as Copilot Chat, a custom agent, or any tool that supports system prompts).

### 2. Provide a PR URL

Provide the target PR URL in your prompt, for example:

```text
Please review this PR: https://github.com/octocat/hello-world/pull/123
```

The prompt supports the following URL formats:

- `https://github.com/{owner}/{repo}/pull/{number}`
- `https://github.com/{owner}/{repo}/pull/{number}/files`
- `https://github.com/{owner}/{repo}/pull/{number}/commits`

### 3. Environment Setup

This prompt depends on GitHub CLI:

```bash
gh --version
gh auth status
```

If you are not logged in, run:

```bash
gh auth login
```

### 4. Expected Output

Based on the prompt design, the AI will provide:

- A summary of PR metadata (title, author, branches, status, description)
- Diff analysis and key risk points
- Audit of existing reviews (already covered vs. potentially missed)
- Multi-dimensional review results: correctness, security, performance, maintainability, testing, and nits
- Final recommendation: `Approve` / `Approve with nits` / `Request changes` / `Block`

### 5. Notes

- This prompt performs review analysis by default and does not automatically submit a review to GitHub.
- If you ask the AI to submit a review, it is recommended to generate the review content first and confirm it manually before submitting.
- The prompt requires `gh` commands to be prefixed with `GH_PAGER=cat` to prevent interactive pagers from blocking output.