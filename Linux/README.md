# 🐧 Linux Commands Reference Guide

A comprehensive, hands-on learning resource for essential Linux commands with real terminal examples, practical use cases, and clear explanations. Perfect for DevOps engineers, system administrators, and anyone working with Linux/Unix systems.

## 📚 About This Guide

This folder contains **detailed markdown documentation** for Linux commands organized by functionality. Each guide includes:

- ✅ **What it does** — Clear, concise explanation
- ✅ **Syntax** — How to use the command
- ✅ **Real terminal output** — Actual examples you can replicate
- ✅ **Flags & options** — Quick reference tables
- ✅ **Practical use cases** — Real-world scenarios
- ✅ **Key points** — Tips and common pitfalls

---

## 📖 Command Categories

### 🔍 **File & Directory Operations**
- **`ls`** — List files and directories with permissions and formatting
- **`find`** — Locate files by name, type, size, or other criteria across directory trees

### 📝 **Text Processing & Data Manipulation**
- **`cut`** — Extract specific columns from structured data (CSV, logs, etc.)
- **`sort`** — Sort lines alphabetically, numerically, or by custom rules
- **`awk`** — Advanced field extraction, filtering, and text processing

### 👤 **User & System Information**
- **`whoami`** & **`id`** — Check current user identity and group membership

### 🔐 **Permissions & Security**
- **`umask`** — Understand and control default file/folder permissions

### 📡 **I/O Streams & Redirection**
- **`stdin`, `stdout`, `stderr`** — Master the three data streams for piping and redirection

### 📦 **Package Management**
- **`apt`** — Install, update, remove, and manage packages on Ubuntu/Debian systems

### 🔧 **Shell Scripting**
- **`functions`** — Write reusable code blocks in bash scripts

---

## 🚀 Quick Start

1. **Browse the commands folder** — Each file is named with a number and the command name
2. **Pick a command** — Open any `.md` file that interests you
3. **Learn by doing** — Copy examples and run them in your terminal
4. **Combine commands** — Use pipes and redirection to build powerful one-liners

---

## 💡 Example: Building a Data Pipeline

Here's how commands work together:

```bash
# Extract IPs from access logs, sort them, count occurrences, rank by frequency
awk '{print $1}' access.log | sort | uniq -c | sort -rn | head -5
