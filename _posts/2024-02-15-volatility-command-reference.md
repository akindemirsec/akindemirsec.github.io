---
layout: post
title: "Volatility Command Reference"
date: 2024-02-15
categories: [forensics, tools]
tags: [volatility, memory-forensics, cheatsheet]
excerpt: "Quick reference for Volatility memory forensics commands - from image profiling to process analysis, credential extraction, and browser artifact recovery."
---

## Image Profile

```bash
$ volatility -f <example.raw> imageinfo
```

## Process Analysis

```bash
# List processes
$ volatility -f <example.raw> --profile=<profile> pslist

# Process tree
$ volatility -f <example.raw> --profile=<profile> pstree

# Process scan (includes hidden/terminated)
$ volatility -f <example.raw> --profile=<profile> psscan

# Generate graph visualization
$ volatility -f <example.raw> --profile=<profile> psscan --output=dot --output-file=<filename.dot>

# Dump process
$ volatility -f <example.raw> --profile=<profile> procdump -p <pid> -D <output/>
```

## Command Line Artifacts

```bash
# Executed commands
$ volatility -f <example.raw> --profile=<profile> cmdscan

# Console outputs
$ volatility -f <example.raw> --profile=<profile> consoles

# Command line arguments (all processes)
$ volatility -f <example.raw> --profile=<profile> cmdline

# Command line for specific PID
$ volatility -f <example.raw> --profile=<profile> cmdline -p <pid>
```

## System Information

```bash
# Environment variables
$ volatility -f <example.raw> --profile=<profile> envars

# NTLM password hashes
$ volatility -f <example.raw> --profile=<profile> hashdump
```

## Network

```bash
$ volatility -f <example.raw> --profile=<profile> netscan
```

## DLL & Module Analysis

```bash
# List loaded DLLs
$ volatility -f <example.raw> --profile=<profile> dlllist -p <pid>

# Dump specific DLL
$ volatility -f <example.raw> --profile=<profile> dlldump -p <pid> -b <base_address> -D <output_directory>
```

## Registry

```bash
$ volatility -f <example.raw> --profile=<profile> dumpregistry -D <output_directory>
```

## File Operations

```bash
# Scan for files
$ volatility -f <example.raw> --profile=<profile> filescan | grep <filename>

# Extract file from memory
$ volatility -f <example.raw> --profile=<profile> dumpfiles -Q <dataoffset> -D <output-directory>
```

Change file extension after extracting based on actual file type.

## Memory Analysis

```bash
# Extract process memory (change extension to .data)
$ volatility -f <example.raw> --profile=<profile> memdump -p <pid> -D <output>

# List handles
$ volatility -f <example.raw> --profile=<profile> handles -p <pid> -t <type>
# Types: mutant, process, file, key, etc.

# Find injected code / suspicious memory allocations
$ volatility -f <example.raw> --profile=<profile> malfind -p <pid>

# Dump memory region
$ volatility -f <example.raw> --profile=<profile> vaddump -b <base_address> -D <output_directory>
```

## Yara Scanning

```bash
$ volatility -f <example.raw> --profile=<profile> yarascan -Y "<yara_rule>"
```

## Browser Artifacts

```bash
# Chrome history (requires volatility-plugins)
# Download: https://github.com/superponible/volatility-plugins
$ volatility --plugins=plugins/ -f <example.raw> --profile=<profile> chromehistory > <output_file>

# IE history
$ volatility -f <example.raw> --profile=<profile> iehistory
```

Alternative: extract browser history file and open it in SQLite.

## Quick Reference

| Command | Purpose |
|---------|---------|
| `imageinfo` | Identify image profile |
| `pslist` | List processes |
| `pstree` | Process tree view |
| `psscan` | Find all processes (including hidden) |
| `cmdscan` | Extract command history |
| `consoles` | Console output history |
| `envars` | Environment variables |
| `hashdump` | Dump password hashes |
| `netscan` | Network connections |
| `filescan` | Scan for files in memory |
| `dumpfiles` | Extract files |
| `dlllist` | Loaded modules |
| `malfind` | Find injected code |
| `mftparser` | Export NTFS MFT |
| `yarascan` | Scan with Yara rules |
