# Nmap Basics — Initial Reconnaissance

## Overview

This is my first hands-on practice with Nmap in Kali Linux. The goal was to understand basic TCP port scanning, port states, and service detection rather than simply memorizing Nmap commands.

## Environment

* Kali Linux
* Nmap 7.98
* Target: `127.0.0.1` (localhost)

## What is Nmap?

Nmap is a network discovery and security auditing tool used to identify hosts, discover open ports, detect services and versions, and gather information about a target's network attack surface.

## 1. Basic Scan

I started by scanning localhost:

```bash
nmap 127.0.0.1
```

The host was detected as up, but the default 1,000 TCP ports scanned were closed.

This showed me that a host being reachable does not necessarily mean that it has accessible services running on its ports.

## 2. SYN Scan

I then performed a TCP SYN scan:

```bash
sudo nmap -sS 127.0.0.1
```

The result again showed the host as up and the scanned ports as closed.

The `-sS` option performs a TCP SYN scan. It uses TCP connection behavior to determine the state of ports without completing a normal TCP connection in the usual way.

## 3. Specific Port Scanning

I then focused on three commonly used ports:

```bash
sudo nmap -p 22,80,443 127.0.0.1
```

The result was:

```text
22/tcp  closed  ssh
80/tcp  closed  http
443/tcp closed  https
```

This helped me understand the difference between a port being associated with a particular service and that service actually being available.

For example, port 22 is commonly associated with SSH, but in this case it was closed because no SSH service was listening on that port.

## 4. Service Version Detection

I then used:

```bash
sudo nmap -sV 127.0.0.1
```

Nmap performed service detection, but because there were no open ports among the scanned ports, there was no service or version information to identify.

This demonstrated that service detection becomes useful after Nmap discovers accessible services.

## Understanding Port States

### Open

An application or service is actively listening on the port and accepting connections.

### Closed

The host is reachable, but no application is listening on that port.

### Filtered

Nmap cannot determine whether the port is open because packet filtering, such as a firewall, prevents it from obtaining enough information.

## Key Lessons

* `127.0.0.1` refers to the local machine.
* A host can be up while its ports are closed.
* `-sS` performs a TCP SYN scan.
* `-p` allows specific ports to be scanned.
* `-sV` attempts to identify services and their versions.
* Port numbers provide common service associations but do not guarantee which service is actually running.
* Nmap results need to be interpreted rather than simply collected.

## Pentesting Perspective

The initial Nmap workflow helped me understand the beginning of network reconnaissance:

```text
Target
  ↓
Host discovery
  ↓
Port discovery
  ↓
Port state analysis
  ↓
Service identification
  ↓
Further enumeration
```

The next step is to practice against an authorized lab target with actual services exposed so that I can investigate service and version enumeration in a realistic environment.

## Tools Used

* Kali Linux
* Nmap 7.98

## Next Steps

* Practice Nmap against an authorized lab target.
* Explore service and version enumeration.
* Learn UDP scanning.
* Explore Nmap scripting capabilities (NSE).
* Learn how to save and analyze scan results.
