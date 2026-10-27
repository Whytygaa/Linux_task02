# Task Checklist

Tick items only after completing them in Kali Linux.

## Step 1 — User
- [ ] Create user `student01`.
- [ ] Set a password interactively.
- [ ] Add `student01` to `sudo` group if required.
- [ ] Switch to `student01` using `su` or `login`.
- [ ] Run `whoami` and verify it prints `student01`.

## Step 2 — Directories and files
- [ ] Create `project/docs`, `project/scripts`, and `project/bin` inside the new user's home directory.
- [ ] Create `docs/report.txt` with the exact first line: `This is the initial report by student01.`
- [ ] Run `ls -la`.
- [ ] Create `docs/.secret.txt` containing `Top Secret`.

## Step 3 — Edit and move
- [ ] Use Nano to add `Appended line using nano.` as the second line of `report.txt`.
- [ ] Copy `report.txt` into `scripts`.
- [ ] Move `.secret.txt` into `bin` and rename it `classified.txt`.
- [ ] Create `scripts/install.sh` with the required Bash shebang and echo line.

## Step 4 — Permissions
- [ ] Make `scripts/install.sh` executable by all users.
- [ ] Remove read permission for others from `bin/classified.txt`.
- [ ] Create `docs/admin_notes.txt`.
- [ ] Set `admin_notes.txt` to owner read/write only (`600`).

## Step 5 — Cleanup and backup
- [ ] Delete `docs/admin_notes.txt`.
- [ ] Create `project/backup`.
- [ ] Copy the entire contents of `docs` and `scripts` into `backup`.

## Final checks
- [ ] Return to the home directory.
- [ ] Run `tree project` (install `tree` only if needed).
- [ ] Use `ls -la` to check locations and permissions.
- [ ] Optional: run `history` and redirect it to `~/commands_used.txt`.
- [ ] Capture evidence screenshots and complete the results template.
