# Setup (GitHub CLI recommended)

1. Extract this ZIP and open a terminal inside the `daily-mikarin` directory.
2. Install GitHub CLI (`gh`) if needed, then authenticate with `gh auth login`.
3. Create the public repository and push the initial files:

   ```bash
   git init -b main
   git add .
   git commit -m "Initial commit: Daily Mikarin"
   gh repo create daily-mikarin --public --source=. --remote=origin --push
   ```

4. Open the repo → Actions → Daily Mikarin → Run workflow to test it immediately.
5. Confirm a new line appears in `MIKARIN.md` and a commit was added.

## Notes

- The workflow must exist on the repository's default branch for scheduled runs.
- If the push fails with a 403, check Settings → Actions → General → Workflow permissions. The workflow explicitly asks for `contents: write`, but account or organization restrictions can still override it.
- GitHub automatically disables scheduled workflows in public repositories after 60 days with no repository activity. Ordinary daily commits should normally count as repository activity, but check the Actions tab if it stops.
- Contributions count only when GitHub associates the author email with your account and other contribution eligibility rules are met. The workflow uses GitHub's ID-based noreply email for the triggering actor. If a manual test runs under another account, its commits may be attributed to that account.
- Scheduled workflows can be delayed or dropped. This isn't a guaranteed daily calendar clock.
