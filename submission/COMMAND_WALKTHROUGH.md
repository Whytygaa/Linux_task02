# Command Walkthrough

Run these commands in a Kali Linux terminal. Commands that use `sudo` may request the password of the account you are currently using.

## Step 1 — Create and switch to a new user

Create the required user and set a password when prompted:

```bash
sudo useradd -m student01
sudo passwd student01
```

If the lab requires `student01` to have sudo access, add the account to the sudo group:

```bash
sudo usermod -aG sudo student01
```

Switch to the new user and confirm the active username:

```bash
su - student01
whoami
```

Expected `whoami` output:

```text
student01
```

If `student01` already exists, do not run `useradd` again; switch to it and continue. If your environment uses a different account-management policy, follow the instructor's instructions.

## Step 2 — Directory and file management

Run the following as `student01`:

```bash
cd ~
mkdir -p project/docs project/scripts project/bin
cd ~/project/docs
echo "This is the initial report by student01." > report.txt
ls -la
echo "Top Secret" > .secret.txt
```

## Step 3 — Edit and move files

Open the report in Nano:

```bash
nano report.txt
```

Add this as the second line, keeping the first line intact:

```text
Appended line using nano.
```

In Nano, save with `Ctrl+O`, press `Enter`, then exit with `Ctrl+X`.

Copy the report to `scripts`, move and rename the hidden file to `bin/classified.txt`, and create the installer script:

```bash
cp report.txt ../scripts/
mv .secret.txt ../bin/classified.txt
cat > ../scripts/install.sh <<'EOF'
#!/bin/bash
echo "Installing project dependencies..."
EOF
```

## Step 4 — Permissions with chmod

Make `install.sh` executable by all users:

```bash
chmod a+x ~/project/scripts/install.sh
```

Remove read permission for “others” from `classified.txt`:

```bash
chmod o-r ~/project/bin/classified.txt
```

Create `admin_notes.txt` in `docs`, then set permissions so only the owner can read and write it:

```bash
touch ~/project/docs/admin_notes.txt
chmod 600 ~/project/docs/admin_notes.txt
```

## Step 5 — Clean-up and final touches

Delete `admin_notes.txt`, create `backup`, and copy the entire contents of `docs` and `scripts` into it:

```bash
rm ~/project/docs/admin_notes.txt
mkdir -p ~/project/backup
cp -r ~/project/docs ~/project/scripts ~/project/backup/
```

This produces `backup/docs/` and `backup/scripts/`. Because the copy occurs after `admin_notes.txt` is deleted, that file should not be in the backup.

## Final checks

```bash
cd ~
tree project
ls -la ~/project/docs ~/project/scripts ~/project/bin ~/project/backup
```

If `tree` is not installed, the task instructs you to install it first:

```bash
sudo apt install tree
```

Because the terminal is running as `student01`, `sudo` may be needed for the installation.

Check the key permission requirements:

```bash
ls -l ~/project/scripts/install.sh
ls -l ~/project/bin/classified.txt
ls -l ~/project/docs
```

Interpretation:
- `install.sh` should have execute (`x`) permission for user, group, and others.
- `classified.txt` should not have read (`r`) permission for others.
- `admin_notes.txt` should have been deleted from `docs`.

## Optional bonus — command history

```bash
history
history > ~/commands_used.txt
```

The second command redirects the history output to `commands_used.txt` in `student01`'s home directory. This is optional. Review the file before sharing it because command history can contain sensitive information in other environments.
