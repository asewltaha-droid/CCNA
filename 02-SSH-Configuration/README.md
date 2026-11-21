# CCNA Lab 01 – Basic Router and Switch Configuration

## 📌 Lab Overview
This lab covers the basic configuration of a Cisco router and switch using Cisco IOS CLI commands.

The goal is to practice device naming, password configuration, password encryption, and saving configurations.

## 🎯 Lab Objectives

1. Change the router hostname to `R1`.
2. Change the switch hostname to `SW1`.
3. Configure an unencrypted enable password (`CCNA`) on both devices.
4. Test the enable password from User EXEC mode.
5. View passwords in the running configuration.
6. Enable password encryption using `service password-encryption`.
7. Configure a secure enable secret password (`Cisco`) on both devices.
8. Test privileged EXEC access.
9. Compare the encryption types of `enable password` and `enable secret`.
10. Save the running configuration to startup configuration.

## 🛠️ Lab Environment

- **Devices:** 1 Cisco Router and 1 Cisco Switch
- **Router Name:** R1
- **Switch Name:** SW1
- **Operating System:** Cisco IOS
- **Simulation Software:** Cisco Packet Tracer

## 💻 Commands Used

| Command | Purpose |
|---|---|
| `hostname R1` | Change router hostname |
| `hostname SW1` | Change switch hostname |
| `enable password CCNA` | Configure an enable password |
| `service password-encryption` | Encrypt plaintext passwords in the configuration |
| `enable secret Cisco` | Configure an encrypted enable secret |
| `show running-config` | Display the current configuration |
| `copy running-config startup-config` | Save the configuration |

## 🔍 Important Observations

- `enable password` configures a password for privileged EXEC mode.
- `service password-encryption` encrypts plaintext passwords in the configuration.
- `enable secret` provides a more secure password than the traditional `enable password`.
- When both `enable password` and `enable secret` are configured, **enable secret takes priority**.
- Type 7 encryption is used by `service password-encryption`.
- Type 5 encryption is commonly used for `enable secret` in this lab (MD5-based hash).

## ❓ Lab Questions and Answers

**1. Which password is required to enter Privileged EXEC mode when both passwords are configured?**

Answer: `Cisco` (enable secret).

**2. What encryption type is used for enable password?**

Answer: Type 7.

**3. What encryption type is used for enable secret?**

Answer: Type 5.

**4. Which command saves the configuration?**

Answer: `copy running-config startup-config`.

## 📚 What I Learned

- How to configure Cisco router and switch hostnames.
- The difference between User EXEC and Privileged EXEC modes.
- How to configure enable passwords.
- The difference between `enable password` and `enable secret`.
- How Cisco IOS password encryption works.
- How to save device configurations.

## 📸 Lab Screenshots

_Add screenshots of your Packet Tracer topology and CLI configurations here._

---

**Status:** Completed ✅
