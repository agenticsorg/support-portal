Generate a concise, conventional commit message based on the staged changes (or all changes if nothing is staged). Then commit with that message and push to the current branch.

## Steps

1. Check for staged changes with `git diff --cached`
2. If nothing staged, stage all changes with `git add -A`
3. Analyze the diff and generate a conventional commit message using the conventional commits format:
   - `feat:` for new features
   - `fix:` for bug fixes
   - `docs:` for documentation changes
   - `style:` for formatting, missing semicolons, etc.
   - `refactor:` for code refactoring
   - `test:` for adding tests
   - `chore:` for maintenance tasks
4. Commit with the generated message, including the standard footer:
   ```
   Signed-off-by: @yousecjoe
   ```
5. Push to origin on the current branch

## Important

- Keep commit messages concise (50 chars or less for the subject line)
- Use imperative mood ("Add feature" not "Added feature")
- Do not include file names in the commit subject unless critical
- Group related changes into a single logical commit message
