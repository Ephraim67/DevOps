## What is Performance Monitoring?

> **Performance Monitoring** is the continuous observation of system and application behavior to detect bottlenecks, failures, or performance degradation.



## Why It Matters

| Reason             | Why It's Important                                          |
| ------------------ | ----------------------------------------------------------- |
| 🧩 Troubleshooting | Helps identify CPU spikes, memory leaks, or slow I/O        |
| 🔐 Security        | Detect anomalies like crypto miners or brute force attempts |
| 💼 DevOps          | Ensures systems meet SLAs and handle user load              |
| 📊 Optimization    | Improve response time, resource usage, and uptime           |



##  Cheatsheet: Performance Monitoring (Linux + Windows)



### 🐧 Linux Performance Monitoring Cheatsheet

| Command/Tool   | Purpose                                                 |
| -------------- | ------------------------------------------------------- |
| `top` / `htop` | Real-time process & resource monitor                    |
| `vmstat 1`     | Virtual memory, CPU, I/O stats                          |
| `iostat -xz 1` | Disk I/O performance                                    |
| `free -m`      | Memory usage                                            |
| `uptime`       | Load averages over time                                 |
| `sar`          | Historical performance data (via `sysstat`)             |
| `dstat`        | Combined CPU, disk, net, etc.                           |
| `iotop`        | Disk I/O by process                                     |
| `iftop`        | Live network usage per connection                       |
| `netstat -s`   | Network statistics                                      |
| `perf top`     | CPU performance counters                                |
| `pidstat`      | Resource usage per process over time                    |
| `glances`      | All-in-one real-time monitoring (`pip install glances`) |

---

### 🪟 Windows Performance Monitoring Cheatsheet

| Tool                                | Description                                        |
| ----------------------------------- | -------------------------------------------------- |
| **Task Manager**                    | Real-time resource usage (CPU, memory, disk, etc.) |
| **Resource Monitor** (`resmon`)     | Deeper look into CPU, disk, network                |
| **Performance Monitor** (`perfmon`) | Custom performance data collection                 |
| `tasklist` / `taskkill`             | CLI for process info                               |
| `Get-Process`                       | PowerShell process info                            |
| **Sysinternals Tools**              | `Process Explorer`, `Procmon`, `TCPView`           |
| `wmic`                              | Query system data from CLI                         |
| `netstat -an`                       | View network connections and performance           |
| `diskperf -y`                       | Enable disk performance counters                   |

---

### 📊 Key Metrics to Monitor

| Resource    | Metric                 | Sign of Trouble                  |
| ----------- | ---------------------- | -------------------------------- |
| CPU         | Load Avg, % Usage      | Sustained high usage = overload  |
| Memory      | Free RAM, Swap Usage   | Swap in use = not enough RAM     |
| Disk        | IOPS, latency, % busy  | High I/O wait = bottleneck       |
| Network     | Bandwidth, packet loss | Spikes or drops = congestion     |
| Processes   | Count, states          | Zombie/hung processes            |
| Application | Response time, errors  | Laggy APIs = app bug or overload |

##  Tools for Continuous Monitoring

### CLI & Light Tools

* `glances` (Linux) – One-stop for real-time CPU, memory, disk, network
* `atop` – Historical and live stats
* `sysstat` – Enables `iostat`, `sar`, etc.

### Full Monitoring Suites

| Tool                     | Use                                   |
| ------------------------ | ------------------------------------- |
| **Prometheus + Grafana** | Time-series metrics + visualization   |
| **Zabbix**               | Full system and network monitoring    |
| **Nagios**               | Alerts & uptime monitoring            |
| **Netdata**              | Real-time performance charts          |
| **New Relic / Datadog**  | Cloud-based app and system monitoring |
| **Elastic Stack (ELK)**  | Logs and metrics centralization       |


##  Performance Bottleneck Checklist

* [ ] **CPU** at 90–100% for extended time?
* [ ] **Memory** swapping heavily?
* [ ] **Disk I/O** queue time increasing?
* [ ] **Network** bandwidth maxed or dropping packets?
* [ ] **Processes** in uninterruptible sleep?
* [ ] **Application** slow to respond or throwing 5xx errors?



## Quick Bash Script (Linux)

```bash
#!/bin/bash
echo "CPU & Memory Usage:"
top -b -n1 | head -10

echo -e "\nDisk IO:"
iostat -xz 1 1

echo -e "\nNetwork:"
ifstat 1 1
```



## Want to Practice?

* Simulating high CPU: `yes > /dev/null`
* Simulating memory usage: `stress --vm 2 --vm-bytes 500M --timeout 10s`
* Monitoring your app under load using tools like:

  * `ab` (Apache Benchmark)
  * `wrk`
  * `locust`
