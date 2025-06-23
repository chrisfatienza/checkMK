**mk_yumseccheck**
A custom Checkmk local plugin that monitors YUM/DNF-based Linux systems for:

Security updates (Important and Moderate)

Kernel updates

The plugin returns a CRIT state if any such updates are available, and OK otherwise.

**What It Does**
This plugin checks for:

Any available Important or Moderate security notices

Any available kernel updates

**Displays:**

The current running kernel version

The latest available kernel version (if newer exists)

**Example Output**
When security + kernel updates are found:

2 SecurityUpdate - CRIT - Security updates: 2 important, 5 moderate | Kernel update available: Current=5.14.0-427.24.1.el9_4.x86_64, New=5.14.0-503.40.1.el9_5.cloud.1.0
When the system is fully up-to-date:

0 YumSecurity - OK - No security or kernel updates

📦 **Installation**
Copy the plugin to the Checkmk agent local plugin directory:

sudo cp mk_yumseccheck /usr/lib/check_mk_agent/local/
sudo chmod +x /usr/lib/check_mk_agent/local/mk_yumseccheck

Ensure yum and yum-plugin-security are installed:

sudo yum install -y yum-plugin-security

On RHEL/Rocky/Oracle Linux 8 and 9, yum is a compatibility wrapper for dnf — this plugin works with both.

**Test the plugin manually:**

/usr/lib/check_mk_agent/local/mk_yumseccheck

The plugin output appears under the section:

<<<yum_security:sep(124)>>>

✅ Compatibility
Distribution	Version	Compatible
RHEL	7, 8, 9	✅
CentOS	7	✅
Oracle Linux	7, 8, 9	✅
Rocky Linux	8, 9	✅
AlmaLinux	8, 9	✅

The plugin works with YUM or DNF as long as the yum CLI is available (yum is typically symlinked to dnf in EL 8/9 systems).

🛠️ **Requirements**
yum (or yum symlinked to dnf)

yum-plugin-security (or native support in EL8+)

**Checkmk agent 2.x or later**

❗ **Alerting Logic**
A CRIT status is triggered if:

There are any Important or Moderate security updates

A newer kernel package is available

An OK status is returned only when:

No security updates are pending

No newer kernel packages are available
