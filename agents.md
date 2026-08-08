# AI Project – Development & Server Administration Rules

## 1. User and Privilege Management

* Always use the `ubuntu` user with UID `1001` for normal operations.
* Do **not** switch to `root` unnecessarily.
* Use `sudo` only when elevated privileges are actually required.
* Do not create files, scripts, services, or configurations as `root` unless there is a specific system-level requirement.
* When creating or modifying files, ensure they remain owned by the `ubuntu` user where appropriate.

## 2. Cron Jobs

* All cron jobs must belong to the `ubuntu` user.
* When adding or modifying scheduled tasks, always use the `ubuntu` user's crontab.
* **Never** add project/application cron jobs to the root crontab.
* Use:

  ```bash
  crontab -e
  ```

  when editing the `ubuntu` user's crontab.
* If a cron job already exists, modify the existing `ubuntu` crontab entry rather than creating a duplicate.
* When providing cron-related instructions, clearly state which `ubuntu` crontab entry should be added or changed.

## 3. VI/VIM Only

* Always provide `vi`/`vim` commands for editing files.
* **Never provide `nano` commands.**
* For example:

  ```bash
  vi /path/to/file
  ```
* When a file needs to be modified, provide the exact `vi` command and the complete replacement content whenever practical.

## 4. Complete Scripts for Code Changes

* Whenever a script needs to be created or modified, always provide the **complete script**.
* Do **not** instruct me to modify individual lines, sections, or fragments of an existing script unless absolutely unavoidable.
* The preferred workflow is:

  1. Provide the exact `vi` command to open the file.
  2. Provide the **entire updated script**.
  3. Make it possible to copy and paste the complete script directly.
  4. Include the commands required to save, make executable, test, and run the script when applicable.
* Do not assume that I will manually merge code changes into my existing script.

## 5. Logging and Log Rotation

* Any script or application that generates log files must implement log rotation.
* Never allow logs to grow indefinitely and consume the server's storage.
* Prefer standard Linux log rotation mechanisms such as `logrotate` where appropriate.
* For scripts that maintain their own logs, implement a reasonable retention policy and maximum log size.
* When creating a new logging-enabled script, include the corresponding log-rotation configuration as part of the implementation.
* Consider:

  * Maximum log file size
  * Number of retained files
  * Compression of older logs
  * Automatic deletion of old logs
  * Appropriate ownership and permissions
* The solution must prevent logs from filling the server filesystem.

## 6. Safe Modification Principle

Before modifying an existing project:

* Inspect the current configuration/script before making changes.
* Preserve existing functionality unless the requested change specifically requires removing it.
* Do not overwrite unrelated configuration.
* Check file ownership and permissions after making system-level changes.
* Prefer reversible changes where practical.
* After making changes, provide commands to verify that the modification works.

## 7. Command Presentation

When providing commands:

* Give commands in the order they should be executed.
* Make commands directly copy/pasteable.
* Clearly distinguish between:

  * Normal `ubuntu` user commands
  * Commands requiring `sudo`
  * Commands that modify configuration
  * Commands used only for verification/testing
* Do not unnecessarily use `sudo`.
* Do not use `su`, `sudo -i`, or root shells unless there is a specific reason.

## 8. Verification

After any significant modification, provide appropriate verification commands.

For example:

```bash
systemctl status <service>
```

```bash
docker ps
```

```bash
crontab -l
```

```bash
df -h
```

The verification steps should confirm that:

* The configuration is valid.
* The service/script is running correctly.
* The expected user owns the relevant files.
* Cron jobs are present in the correct user's crontab.
* Log files are being rotated where applicable.
* No unnecessary root-owned project files or processes have been introduced.

## 9. Default Behaviour

When there is more than one reasonable implementation, prefer the solution that:

1. Uses the `ubuntu` user.
2. Minimizes the use of `sudo`.
3. Uses `vi`/`vim` rather than `nano`.
4. Provides complete scripts instead of partial modifications.
5. Uses `ubuntu`'s crontab rather than root's crontab.
6. Includes log rotation for generated logs.
7. Is safe to copy and paste.
8. Includes verification commands.
9. Minimizes the risk of filling the server's storage.

