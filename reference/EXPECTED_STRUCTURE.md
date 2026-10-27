# Expected Project Structure

After completing all required steps, the important structure under `/home/student01/project` should resemble:

```text
project/
├── backup/
│   ├── docs/
│   │   └── report.txt
│   └── scripts/
│       ├── install.sh
│       └── report.txt
├── bin/
│   └── classified.txt
├── docs/
│   └── report.txt
└── scripts/
    ├── install.sh
    └── report.txt
```

`tree` may display permissions or other metadata differently depending on its options and environment. The structure above focuses on required paths.

## Required file contents

`docs/report.txt` and its copies should contain these two lines:

```text
This is the initial report by student01.
Appended line using nano.
```

`bin/classified.txt` should contain:

```text
Top Secret
```

`scripts/install.sh` and its backup copy should contain:

```bash
#!/bin/bash
echo "Installing project dependencies..."
```

## Permission expectations

- `scripts/install.sh`: executable by all users. `chmod a+x` adds execute bits while preserving existing permission bits, so the exact mode can depend on the file's initial mode.
- `bin/classified.txt`: no read permission for others. `chmod o-r` removes only the “others” read bit.
- `docs/admin_notes.txt`: while it exists, mode `600` means owner read/write only. It is then deleted in Step 5, so it should not appear in the final tree or backup.

## Backup timing

The activity deletes `admin_notes.txt` before copying `docs` and `scripts` into `backup`. Therefore, the backup should contain the report and script files but not `admin_notes.txt`.
