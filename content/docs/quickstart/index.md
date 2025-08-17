+++
date = '2025-07-07T22:53:30-05:00'
draft = false
weight = 10
title = 'Quickstart'
description = "Get started with the extension here. Learn how to install the plugin and it's basic configuration. It also covers the core concepts of the plugin."
+++

### Getting Started

### 1. Installation

1. **Install from Mozilla Add-ons**
   - Visit the [Nixxer extension page](https://addons.mozilla.org/addon/nixxer/) on Mozilla Add-ons
   - Click "Add to Firefox"
   - Click "Add" when Firefox asks for permission confirmation
   - The extension will install automatically

2. **Verify Installation**
   - Look for the Nixxer icon in your Firefox toolbar
   - If not visible, click the puzzle piece icon and pin Nixxer to your toolbar

### 2. Initial Setup

- Extension auto-starts upon installation
- Default settings provide balanced protection
- No configuration required for basic use

### 3. Usage

###### Basic Operation

1. **Enable/Disable**: Click the Nixxer icon in your toolbar
2. **View Statistics**: See real-time blocking stats across all tracker types in the popup
3. **Recent Activity**: Monitor recently detected domains with tracker type indicators
4. **Export Blocklists**: Use the Export button for network-level blocking

### 4. Understanding Detection Types

- **🔴 3rd Party**: External tracking domains (safe to block at network level)
- **🟡 1st Party**: Self-hosted analytics (blocked in browser only)
- **🟣 Mixed**: Multiple detection methods or unclear classification

### Core Features

###### Blocking Modes

1. **Browser-Level**: Blocks requests and deletes cookies in Firefox only
2. **Network-Level**: Generate blocklists for router/DNS-level blocking

###### Export Formats

- **Pi-hole**: Plain text domain list
- **NextDNS**: JSON format with metadata
- **Hosts File**: Standard hosts file format
- **AdGuard Home**: Filter rule format

###### Statistics Tracking

- Requests blocked today
- Tracking cookies deleted
- Unique domains detected
- Performance metrics

###### Settings Configuration

Access via popup → Options or right-click extension icon

**Detection Settings**

- **Sensitivity**: Low/Medium/High detection aggressiveness
- **Self-hosted blocking**: Detect same-domain analytics
- **Debug logging**: Enable detailed console output

**Blocklist Management**

- **Max domains**: Storage limit (100-5000)
- **Auto-export threshold**: When to suggest network migration
- **Auto-cleanup**: Remove old entries automatically
