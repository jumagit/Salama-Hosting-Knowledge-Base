# DirectAdmin Hosting: In-depth Features

DirectAdmin is renowned for its comprehensive suite of features, all designed to make web hosting management intuitive and efficient. This section provides an in-depth look at the key functionalities available at the User, Reseller, and Administrator levels, highlighting how they empower users to control their hosting environments.

## User Level Features

These features are accessible to individual website owners for managing their specific hosting accounts.

### 1. Website Management
* **Domain Setup:** Easily add, remove, and manage your primary domain and additional domains (addon domains) on your account. Each domain gets its own dedicated space and configuration.
* **Subdomain Management:** Create subdomains (e.g., `blog.yourdomain.com`) for organizing different sections of your website or for staging environments.
* **Domain Pointers (Aliases/Parked Domains):** Point multiple domain names to the same website content, useful for branding or capturing common misspellings.
* **Site Redirection:** Set up 301 (permanent) or 302 (temporary) redirects to forward visitors from one URL to another, crucial for SEO and site restructuring.
* **Error Pages:** Customize standard HTTP error pages (e.g., 404 Not Found, 403 Forbidden) to match your website's branding and provide helpful messages to visitors.

### 2. Email Management
* **E-mail Accounts:** Create, delete, and manage POP3/IMAP email accounts associated with your domains (e.g., `info@yourdomain.com`). Set storage quotas and passwords for each.
* **Email Forwarders:** Automatically redirect incoming emails from one address to another, useful for consolidating mail or sending copies to multiple recipients.
* **Autoresponders:** Set up automatic replies to incoming emails, ideal for "out of office" messages or acknowledging receipt of inquiries.
* **Mailing Lists:** Create and manage mailing lists for group communication, allowing subscribers to send and receive emails from the list address.
* **Spam Filters (SpamAssassin/Rspamd):** Configure powerful spam filtering tools to reduce unwanted emails in your inbox. Users can set custom rules, whitelist/blacklist addresses, and adjust sensitivity.
* **Webmail Access:** Directly access your email accounts through popular webmail clients like Roundcube or SquirrelMail, usually provided as part of the DirectAdmin installation.

### 3. Database Management
* **MySQL Databases:** Create and manage MySQL/MariaDB databases and database users. This is essential for dynamic websites, content management systems (CMS) like WordPress, e-commerce platforms, and forums.
* **phpMyAdmin:** Access a web-based interface for managing your MySQL databases directly within DirectAdmin, allowing you to browse, edit, import, and export database tables.

### 4. File Management
* **File Manager:** A robust, web-based file manager that allows you to upload, download, edit, copy, move, delete, and manage permissions for your website files directly through your browser. It includes features like ZIP/unZIP functionality.
* **FTP Management:** Create and manage multiple FTP accounts with specific directory access permissions, allowing you to upload and download files using an FTP client (e.g., FileZilla).
* **Anonymous FTP:** Option to enable anonymous FTP access for public file sharing (use with caution).

### 5. Security Features
* **SSL Certificates:** Easily install, manage, and renew SSL/TLS certificates (including free Let's Encrypt certificates) to secure your websites with HTTPS, crucial for SEO, security, and user trust.
* **Password Protected Directories:** Secure specific directories on your website with an additional username and password, restricting access to sensitive content.
* **IP Blocker:** Block specific IP addresses or IP ranges from accessing your website, useful for mitigating malicious activity.
* **Hotlink Protection:** Prevent other websites from "hotlinking" to your images or files, saving your bandwidth.
* **SSH Access:** (Often enabled by hosting providers) Allows secure command-line access to your server for advanced management tasks.

### 6. Advanced Tools
* **Cron Jobs:** Schedule automated tasks (scripts or commands) to run at specific intervals (e.g., hourly, daily, weekly), useful for backups, cleanup, or data processing.
* **Mime Types:** Configure custom MIME types to instruct browsers on how to handle specific file extensions.
* **Apache Handlers:** Define how the Apache web server should process files with certain extensions.
* **PHP Selector:** Select and switch between different PHP versions (e.g., PHP 7.4, 8.0, 8.1, 8.2, 8.3) for individual domains or subdomains, ensuring compatibility with your applications. This also often includes enabling/disabling various PHP extensions.
* **Site Backup:** Generate full or partial backups of your website data (files, databases, emails) and easily restore them from stored archives.

### 7. Statistics and Logs
* **Site Summary/Statistics:** View detailed statistics about your website's usage, including disk space, bandwidth, and number of email accounts/databases.
* **Raw Access Logs:** Download raw server access logs for detailed analysis of website traffic.
* **Webalizer/AWStats:** Integrated graphical statistics programs that provide visual reports on website visitor behavior.

## Reseller Level Features

In addition to all User-level features (which a Reseller can manage for their clients), Resellers gain powerful tools for managing their own hosting business.

* **Account Management:** Create, modify, suspend, unsuspend, and delete user accounts.
* **Reseller Packages:** Define customized hosting packages with specific resource allocations (disk space, bandwidth, number of domains, databases, emails, etc.) that users can subscribe to.
* **IP Management:** Allocate specific IP addresses to user accounts.
* **DNS Management:** Control the DNS zones for all domains hosted under their reseller account.
* **Message System:** Communicate with their users through an integrated messaging system.
* **Customization:** Brand the DirectAdmin interface with their own logo and color scheme for a professional look.

## Administrator Level Features

The highest tier, providing complete control over the server. Administrators can access all Reseller and User-level features, plus critical server management tools.

* **Reseller/Admin Management:** Create and manage other administrator and reseller accounts.
* **IP Manager:** Add and manage all IP addresses on the server, assigning them to resellers or users.
* **DNS Administration:** Manage DNS for the entire server, including global nameserver settings and DNS clustering.
* **Mail Queue Administration:** View and manage the server's email queue, troubleshooting delivery issues.
* **System/Services Info:** Monitor system resources (CPU, RAM, disk usage) and manage server services (Apache, Nginx, PHP-FPM, MySQL, Exim, Dovecot) by starting, stopping, or restarting them.
* **Complete Usage Statistics:** Get a detailed overview of overall server resource usage and individual account resource consumption.
* **Software Updates:** Manage updates for DirectAdmin itself and core server software components (Apache, PHP, MySQL, etc.) via CustomBuild.
* **Security Settings:** Configure brute force detection, firewall rules (often through integration with CSF), and other server-wide security parameters.
* **File Editor (Server Configuration):** Directly edit server configuration files for services like Apache, PHP, and MySQL.
* **DNS Clustering:** Set up and manage DNS clustering with other DirectAdmin servers for redundancy and improved DNS resolution.
* **Licensing:** Manage the DirectAdmin license for the server.

DirectAdmin's comprehensive feature set, organized across these three distinct levels, ensures that all users, from individual website owners to large hosting providers, have the necessary tools to manage their web hosting efficiently and securely.