Generate a concise, conventional commit message based on the staged changes (or all changes if nothing is staged). Then commit with that message and push to the current branch.

Steps:
1. Check for staged changes with `git diff --cached`
2. If nothing staged, stage all changes with `git add -A`
3. Analyze the diff and generate a conventional commit message (feat:, fix:, docs:, etc.)
4. Commit with the generated message
5. Push to origin
