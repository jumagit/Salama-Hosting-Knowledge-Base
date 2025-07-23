# Security Best Practices: Protecting Your Salama Hosting Account

Protecting your website and hosting account is paramount to safeguarding your data, sensitive customer information, and ensuring the continuous availability of your online presence. At Salama Hosting, we provide robust infrastructure, but **your active participation in security is crucial.** This guide outlines essential best practices every Salama Hosting customer should follow to maintain a secure hosting environment.

---

## 1. Fortify Your Credentials

Your passwords are the first line of defense. Weak or reused passwords are a hacker's easiest entry point.

* **Use Strong, Unique Passwords:**
    * **Complexity:** Aim for at least 12-16 characters. Combine uppercase and lowercase letters, numbers, and special symbols (e.g., `!@#$%^&*`).
    * **Uniqueness:** Never reuse passwords across different accounts (especially not between your cPanel, email, and other online services). If one account is compromised, all others remain secure.
    * **Avoid Guessable Patterns:** Steer clear of personal information (birthdates, names), common words, or simple sequences like '123456', 'password', or 'admin'.
    * **Leverage a Password Manager:** Consider using a reputable password manager (e.g., LastPass, Bitwarden, 1Password) to generate, store, and auto-fill complex passwords securely.

* **Enable Two-Factor Authentication (2FA) / Multi-Factor Authentication (MFA):**
    * **What it is:** 2FA adds an extra layer of security by requiring a second form of verification beyond just your password. Even if someone obtains your password, they can't log in without this second factor.
    * **How it works:** Typically involves "something you know" (your password) and "something you have" (a code from your phone via an authenticator app, SMS, or a physical security key).
    * **Salama Hosting Support:** Where supported (e.g., for your Salama Hosting Client Area or cPanel), always enable 2FA immediately. This significantly reduces the risk of unauthorized access.

---

## 2. Keep Your Software Updated

Outdated software is a primary vulnerability exploited by attackers. Updates often include critical security patches.

* **Regularly Update CMS Platforms:**
    * **WordPress, Joomla, Drupal, etc.:** Always keep your Content Management System (CMS) core files updated to the latest stable version.
    * **Plugins and Themes:** Do not neglect plugins and themes! These are very common entry points for hackers if they contain unpatched vulnerabilities. Update them regularly.
    * **Before Updating:** Always **back up your website** before performing major updates to ensure you can revert in case of compatibility issues.

* **Remove Unused Software & Plugins:**
    * Deactivate and delete any themes, plugins, or applications on your hosting account that you are no longer using. They can contain hidden vulnerabilities that create security risks even if inactive.

---

## 3. Implement Robust Backup Strategies

Backups are your ultimate safety net against data loss from hacks, accidental deletions, or server issues.

* **Maintain Regular Backups:**
    * **Automated Backups:** Check if Salama Hosting provides automated daily or weekly backups. Understand how to access and restore these.
    * **Manual Backups:** Complement automated backups with your own manual backups of your website files and databases (via cPanel's Backup Wizard or phpMyAdmin).
    * **Offsite Storage:** Store backups in a secure location *separate* from your hosting account (e.g., cloud storage, external hard drive). This protects your data even if your hosting account is completely compromised.
    * **Test Your Backups:** Periodically test restoring a backup to ensure it's viable. The worst time to discover a backup is corrupted is when you desperately need it.

---

## 4. Secure Connections & Data Transfer

Ensure that all communication with your hosting account and website visitors is encrypted.

* **Use HTTPS (SSL/TLS):**
    * **For Your Website:** Ensure your website loads over `HTTPS` (indicated by a padlock in the browser URL bar). This encrypts data transferred between your website and visitors, protecting sensitive information like login credentials and form submissions. Salama Hosting typically offers free SSL certificates (like Let's Encrypt) or allows easy installation of purchased ones.
    * **For cPanel/Webmail:** Always access your cPanel and webmail interfaces using `HTTPS`.
* **Use SFTP (Secure File Transfer Protocol) instead of FTP:**
    * **Encryption:** SFTP encrypts your login credentials and data during transfer, making it much more secure than traditional FTP, which sends information in plain text.
    * **Access:** Most FTP clients support SFTP. Use the same credentials you'd use for SSH access or cPanel.

---

## 5. Manage File Permissions Wisely

Incorrect file permissions are a common security oversight that can leave your website vulnerable.

* **Understand `chmod`:** Permissions determine who can read, write, or execute files and folders on your server. They are often represented by numeric codes (e.g., `755`, `644`).
* **Principle of Least Privilege:** Grant only the necessary permissions.
    * **Files:** Most files (HTML, CSS, JS, images) should be `644` (Owner: Read/Write, Group: Read, Others: Read).
    * **Folders:** Most folders should be `755` (Owner: Read/Write/Execute, Group: Read/Execute, Others: Read/Execute).
    * **Sensitive Files:** Configuration files (e.g., `wp-config.php`) should often be more restrictive, like `600` or `400` (Owner: Read/Write or Read only, no access for others).
* **Avoid `777`:** Never set permissions to `777` (world-writable) for any files or folders, especially `public_html` or its subdirectories. This grants anyone on the internet full control and is a massive security risk.
* **Use cPanel File Manager:** cPanel's File Manager allows you to easily view and change file permissions by right-clicking files/folders.

---

## 6. Monitor and Respond to Threats

Proactive monitoring can help you detect and address security issues before they escalate.

* **Review Access and Error Logs:**
    * Regularly check your website's access logs and error logs (available in cPanel). Look for unusual login attempts, repeated `404` errors for non-existent pages, or sudden spikes in traffic from suspicious IP addresses.
    * Error logs can help identify issues in your website code that might be exploitable.
* **Implement a Web Application Firewall (WAF) / Security Plugin:**
    * Consider using a WAF (if your Salama Hosting plan offers one) or a security plugin for your CMS (e.g., Wordfence for WordPress). These tools can block malicious traffic, protect against common attacks like SQL injection and cross-site scripting (XSS), and scan for malware.
* **Regular Security Scans:**
    * Periodically scan your website for malware and vulnerabilities. Many security plugins offer this feature, or you can use external online scanners.
* **Stay Informed:**
    * Subscribe to security advisories for your CMS and plugins. Be aware of new vulnerabilities and recommended patches.

---

## 7. Educate Yourself and Your Team

Human error is often a factor in security breaches.

* **Be Wary of Phishing:** Be extremely cautious of suspicious emails or messages asking for your login credentials or personal information. Salama Hosting will never ask for your password via email.
* **Click with Caution:** Avoid clicking on suspicious links or downloading attachments from unknown sources.
* **Limit User Accounts:** If you have multiple users for your website or cPanel, create separate accounts for each and grant them only the minimum necessary privileges (principle of least privilege). Remove accounts for former team members immediately.

---

!!! warning "If You Suspect a Breach"
    If you ever suspect your Salama Hosting account or website has been compromised:
    1.  **Change all your passwords immediately.**
    2.  **Contact Salama Hosting support** *without delay*. Provide as much detail as possible about what you're observing.
    3.  **Restore from a clean backup** (if available) as a last resort, after consulting with support.

---

By consistently applying these security best practices, you can significantly enhance the protection of your website and hosting account with Salama Hosting, ensuring a safer and more reliable online experience for both you and your visitors.

