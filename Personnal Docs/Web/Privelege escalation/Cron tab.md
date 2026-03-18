---
share: true
---
```markdown
# Note: Viewing Scheduled Tasks with crontab

## What is crontab?

- `crontab` is the system used in Unix/Linux to schedule tasks (cron jobs) to run automatically at specified times and intervals.
- The main system-wide crontab file is `/etc/crontab`.

## How to View the System Crontab

To display the contents of the system crontab:

```bash
cat /etc/crontab
```

- This command shows all scheduled tasks for the system, including the timing, user, and command to be executed.

## Crontab File Format

Each line in `/etc/crontab` typically follows this format:

```
minute hour day month day_of_week user command
```

**Example:**
```
0 5 * * * root /usr/bin/some-script.sh
```
- This runs `/usr/bin/some-script.sh` as root every day at 5:00 AM.

## Tips

- To view your user’s personal crontab, use: `crontab -l`
- To edit your user’s crontab, use: `crontab -e`
- System-wide scheduled tasks are managed in `/etc/crontab` and sometimes in `/etc/cron.d/`

---

**Summary:**  
Use `cat /etc/crontab` to view all system-wide scheduled cron jobs and understand when and how automated tasks are run.