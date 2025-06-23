# mk_yumseccheck

`mk_yumseccheck` is a **Checkmk local plugin** for monitoring Linux systems that use **YUM** or **DNF** (such as RHEL, CentOS, Oracle Linux, Rocky, or AlmaLinux).

It checks for:

- Security updates (Important & Moderate)
- Kernel updates

If any such updates are found, the plugin reports a **CRIT** status to Checkmk. If nothing is pending, it reports **OK**.

---

## 🔍 What It Does

The plugin runs as part of the Checkmk agent and reports:

- Count of **Important** and **Moderate** security updates
- Whether a **newer kernel** version is available
- The current and newest available kernel version (if applicable)

---

## ✅ Example Output

```text
<<<yum_security:sep(124)>>>
2 YumSecurity - CRIT - Security updates: 2 important, 5 moderate | Kernel update available: Current=5.14.0-427.24.1.el9_4.x86_64, New=5.14.0-503.40.1.el9_5.cloud.1.0
