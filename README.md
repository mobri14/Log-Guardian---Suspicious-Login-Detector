# Log Guardian - Suspicious Login Detector

## Overview

Log Guardian is a simple cybersecurity project written in Python that analyzes login logs and detects suspicious authentication activity.

The tool helps identify potential brute force attacks by tracking failed login attempts from the same IP address.

## Features

* Parse authentication logs
* Detect repeated failed logins
* Generate security alerts
* Count failed attempts per IP
* Easy to extend

## Source Code

```python
from collections import defaultdict

THRESHOLD = 5

failed_logins = defaultdict(int)

logs = [
    ("192.168.1.10", False),
    ("192.168.1.10", False),
    ("192.168.1.10", False),
    ("192.168.1.10", False),
    ("192.168.1.10", False),
    ("192.168.1.20", False),
    ("192.168.1.30", True),
]

for ip, success in logs:

    if not success:
        failed_logins[ip] += 1

for ip, count in failed_logins.items():

    if count >= THRESHOLD:
        print(
            f"[ALERT] Suspicious activity "
            f"detected from {ip} "
            f"({count} failed attempts)"
        )
```

## Example Output

```text
[ALERT] Suspicious activity detected from 192.168.1.10 (5 failed attempts)
```

## How It Works

The program analyzes authentication records and counts failed login attempts for each IP address.

When the number of failures exceeds a configurable threshold, an alert is generated.

## Applications

* SSH Login Monitoring
* FTP Login Monitoring
* Web Application Security
* SIEM Learning Projects
* Cybersecurity Education

## Future Improvements

* Read logs from files
* Export reports as CSV
* Real-time monitoring
* Email notifications
* Dashboard interface
* SQLite database support

## Requirements

```bash
python3
```

## Run

```bash
python3 log_guardian.py
```

## License

MIT License
