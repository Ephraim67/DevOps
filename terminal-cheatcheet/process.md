**Process Monitoring** is the act of observing and managing active processes (running programs or system tasks) on a computer system to:

* Detect anomalies (e.g., malware or resource hogs)
* Track resource usage (CPU, RAM, I/O)
* Ensure critical processes are running
* Terminate or restart misbehaving processes
* Analyze system performance over time


###  Why It’s Important (Especially for Security & DevOps)

* Detect **rogue processes** (e.g., crypto miners, backdoors)
* Ensure **system stability and uptime**
* Catch **memory leaks or runaway CPU usage**
* Monitor **web server health**, **database responsiveness**, etc.


##  Cheatsheet: Process Monitoring (Linux + Windows)



###  Linux Process Monitoring Cheatsheet

| Command                      | Description                                             |
| ---------------------------- | ------------------------------------------------------- |
| `ps aux`                     | Show all running processes                              |
| `ps -ef`                     | Full-format listing                                     |
| `top` or `htop`              | Real-time CPU & memory usage (use `htop` for better UI) |
| `pidof <process>`            | Get PID (Process ID) of a process                       |
| `kill <PID>`                 | Kill process by PID                                     |
| `killall <process_name>`     | Kill all processes with that name                       |
| `nice` / `renice`            | Change process priority                                 |
| `strace -p <PID>`            | Trace syscalls of a process (debugging)                 |
| `lsof -p <PID>`              | List files a process has opened                         |
| `watch -n 1 ps aux`          | Refresh process list every second                       |
| `pgrep <name>`               | Get PIDs by name                                        |
| `systemctl status <service>` | Check status of a systemd service                       |
| `journalctl -u <service>`    | Logs for a specific service                             |
| `uptime`                     | Check how long system has been up and current load      |

**Advanced Tools:**

* `glances` – All-in-one monitoring tool (`pip install glances`)
* `atop` – Advanced real-time monitor with logs
* `netstat` / `ss` – View open network connections (used by processes)



###  Windows Process Monitoring Cheatsheet

| Tool                                | Description                                           |
| ----------------------------------- | ----------------------------------------------------- |
| `Task Manager (Ctrl + Shift + Esc)` | GUI for viewing and killing processes                 |
| `tasklist`                          | List all running processes (CMD)                      |
| `taskkill /PID <PID> /F`            | Forcefully kill a process                             |
| `Get-Process`                       | PowerShell: List running processes                    |
| `Stop-Process -Id <PID>`            | PowerShell: Kill process by PID                       |
| `Start-Process`                     | Start a new process                                   |
| `wmic process list brief`           | View all processes and their memory usage             |
| `resmon`                            | Open Resource Monitor for deeper analysis             |
| `perfmon`                           | Windows Performance Monitor                           |
| `Process Explorer`                  | Advanced task manager (Sysinternals)                  |
| `Procmon` (Process Monitor)         | Track file, registry, network activity (Sysinternals) |



###  Security Monitoring Tips

| Tip                                        | Tool                                                |
| ------------------------------------------ | --------------------------------------------------- |
| List all processes running as root (Linux) | `ps -U root -u root u`                              |
| Find suspicious processes                  | Look for no name, high CPU, odd ports               |
| Find processes listening on ports          | `netstat -tulnp` or `ss -tulnp`                     |
| Monitor startup processes                  | Linux: `systemctl`, Windows: `msconfig`, `Autoruns` |
| Check persistence mechanisms               | `crontab`, systemd units, Windows services          |
| Audit what a process is doing              | `lsof`, `strace`, `procmon`                         |



###  Quick Tools to Install for Deep Monitoring

* `htop`: `sudo apt install htop`
* `glances`: `pip install glances`
* `atop`: `sudo apt install atop`
* **Windows**: Download [Process Explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer) and [Procmon](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon)



##  Bonus: Create a Process Monitoring Script

**Linux Example (Bash)**:

```bash
#!/bin/bash
echo "High CPU usage processes:"
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
```

**PowerShell Example (Windows)**:

```powershell
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10
```
