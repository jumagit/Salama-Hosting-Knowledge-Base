# SSL Certificates: Securing Your Website with HTTPS

SSL (Secure Socket Layer) and its successor, TLS (Transport Layer Security), certificates are absolutely essential for encrypting data exchanged between your website and its visitors. They create a secure, encrypted connection, protecting sensitive information like login credentials, personal data, and payment details from being intercepted.

At Salama Hosting, we understand the critical importance of website security. That's why we provide **easy SSL integration for all hosted domains**, making it simple to secure your online presence.

---

## Understanding SSL Certificates

### What is an SSL Certificate?

An SSL certificate is a digital certificate that authenticates the identity of a website and encrypts information sent to the server using SSL/TLS technology. It's like a digital passport for your website that ensures:
1.  **Data Encryption:** Information sent between the user's browser and the website server is scrambled, making it unreadable to unauthorized parties.
2.  **Authentication:** It verifies that you are communicating with the genuine website, not a fraudulent one.

### Why SSL Matters More Than Ever

Using SSL (HTTPS) for your website is no longer optional; it's a fundamental requirement for trust, security, and online visibility.

* **1. Data Encryption & Security:**
    * **Protects Sensitive Data:** Ensures that personal information (usernames, passwords, credit card numbers, contact forms) submitted by your visitors remains private and cannot be eavesdropped on by malicious actors.
    * **Prevents Tampering:** Guarantees that the data exchanged between the browser and the server has not been altered during transit.
* **2. Build Trust & Credibility:**
    * **Green Padlock Icon:** Modern web browsers prominently display a padlock icon and "HTTPS" in the address bar for secure sites, reassuring visitors that their connection is safe.
    * **"Not Secure" Warnings:** Browsers actively warn users when they visit a website that doesn't use HTTPS, significantly deterring visitors and eroding trust.
* **3. Search Engine Optimization (SEO) Benefit:**
    * **Google's Preference:** Google explicitly favors HTTPS-enabled websites and considers SSL an important ranking signal. Having HTTPS can positively impact your website's visibility in search results.
* **4. Compliance Requirements:**
    * Many industry standards (e.g., PCI DSS for handling credit card information) and data privacy regulations (e.g., GDPR, CCPA) require websites to use SSL.
* **5. Modern Browser Compatibility:**
    * Some new browser features and technologies are only available on HTTPS-enabled websites.

---

## Types of SSL Certificates Supported by Salama Hosting

Salama Hosting offers flexible options to secure your domains:

* ### Let's Encrypt (Free SSL)
    * **Description:** This is a free, automated, and open certificate authority that provides Domain Validated (DV) certificates. It's the easiest and most common way to get SSL for most personal and business websites.
    * **Validation Level:** Domain Validation (DV) - verifies that you control the domain name.
    * **Ideal for:** Blogs, small businesses, portfolios, informational sites, and anyone needing basic, strong encryption without additional cost.
    * **Automatic Installation:** For most domains hosted with Salama Hosting, Let's Encrypt certificates are **automatically installed and renewed** via cPanel's AutoSSL feature.

* ### Commercial SSL Certificates (Paid Options)
    * **Description:** For businesses requiring higher levels of trust and validation, Salama Hosting also supports the installation of commercially purchased SSL certificates. These are usually bought from third-party Certificate Authorities (CAs).
    * **Validation Levels:**
        * **Organization Validation (OV):** Verifies the domain owner's identity and confirms the existence of the organization.
        * **Extended Validation (EV):** The highest level of validation, involving a thorough verification of the organization's legal, operational, and physical existence. Often displays the organization's name in the browser bar (though this visual cue is less common in modern browsers).
    * **Ideal for:** E-commerce stores, financial institutions, large corporations, or any entity that needs to project the highest level of trust and undergo rigorous validation.

---

## How to Install and Manage an SSL Certificate via cPanel

Salama Hosting simplifies SSL management directly through your cPanel.

### A. For Let's Encrypt (AutoSSL) - Automated Setup

For most new domains added to your Salama Hosting account, AutoSSL attempts to provision and install a free Let's Encrypt SSL certificate automatically within 24 hours.

1.  **Login to cPanel.**
2.  Navigate to the **`Security`** section and click on **`SSL/TLS Status`**.
3.  Here, you will see a list of your domains.
    * Domains with a green padlock are already secured.
    * Domains with a red warning might need attention.
4.  If a domain isn't showing as secured, check the checkbox next to it and click **`Run AutoSSL`**.
5.  Allow a few minutes for the process to complete. You might need to refresh the page.

!!! tip "Troubleshooting AutoSSL"
    If AutoSSL fails for a domain, ensure:
    * Your domain's **DNS is correctly pointing to Salama Hosting's nameservers.**
    * The domain is accessible from the internet (e.g., not blocked by firewall rules).
    * There are no conflicting `.htaccess` rules or redirects preventing AutoSSL from verifying the domain.
    * Contact Salama Hosting support if issues persist.

### B. For Commercial SSL Certificates - Manual Installation

If you've purchased a Commercial SSL certificate from a third-party, you'll need to install it manually.

1.  **Generate a Certificate Signing Request (CSR):**
    * In cPanel, go to `Security > SSL/TLS`.
    * Click on **`Generate, view, or delete SSL certificate signing requests.`**
    * Fill in your domain details accurately. **Save the generated CSR code**; you'll need to provide this to your SSL certificate provider.
    * **Save the private key** that is generated along with the CSR (usually shown on the same page). You'll need this later.

2.  **Purchase Your SSL Certificate:**
    * Go to your chosen Certificate Authority (e.g., Comodo, DigiCert, Sectigo, etc.) and purchase your certificate. They will ask you to paste your generated CSR.
    * Follow their validation process (e.g., domain control validation via email or DNS record).

3.  **Install the Certificate (CRT and CA Bundle):**
    * Once your CA issues the certificate, you'll receive the **Certificate (CRT)** code and usually a **CA Bundle** (sometimes called "Chain Certificate" or "Intermediate Certificates").
    * In cPanel, go to `Security > SSL/TLS`.
    * Click on **`Manage SSL Sites`** under "Install and Manage SSL for your site (HTTPS)".
    * Select the **`Domain`** you want to secure from the dropdown menu.
    * Paste the **`Certificate (CRT)`** code into the "Certificate (CRT)" field.
    * Paste the **`Private Key (KEY)`** you generated in step 1 into the "Private Key (KEY)" field. (cPanel often auto-fills this if it finds a matching key).
    * Paste the **`Certificate Authority Bundle (CABUNDLE)`** code into the "Certificate Authority Bundle (CABUNDLE)" field.
    * Click **`Install Certificate`**.

---

## Step 4: Force Your Website to Use HTTPS

After installing the SSL certificate, your website can now be accessed via both `http://` and `https://`. To ensure all visitors land on the secure version and for better SEO, you **must redirect all HTTP traffic to HTTPS.**

### A. Via cPanel Redirects (Recommended for Simplicity)

1.  Login to cPanel.
2.  Navigate to `Domains > Redirects`.
3.  Select **`Permanent (301)`**.
4.  Choose your domain from the dropdown.
5.  Ensure **`Redirect with or without www.`** is selected.
6.  Leave the `/` field empty (this redirects the entire domain).
7.  In the "Redirects to" field, enter `https://yourdomain.com/` (replace `yourdomain.com` with your actual domain).
8.  Click **`Add`**.

### B. Via `.htaccess` File (More Control)

This method involves editing the `.htaccess` file in your website's `public_html` (or subdomain) directory.

1.  Login to cPanel and open `File Manager`.
2.  Navigate to your website's root directory (`public_html` or your specific domain folder).
3.  Find the `.htaccess` file. If you don't see it, click `Settings` in the top right of File Manager and enable "Show Hidden Files (dotfiles)".
4.  Right-click the `.htaccess` file and choose `Edit`.
5.  Add the following code to the **top** of the file:

    ```apache
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
    ```
6.  Click `Save Changes`.

!!! warning "Caution with .htaccess"
    Be very careful when editing `.htaccess` files. A single typo can break your entire website. Always make a backup of the file before editing it.

### C. For WordPress Users

If you use WordPress, in addition to the `.htaccess` redirect, it's crucial to update your WordPress settings and sometimes use a plugin:

1.  **Update WordPress Address (URL) settings:**
    * In your WordPress admin dashboard, go to `Settings > General`.
    * Change both `WordPress Address (URL)` and `Site Address (URL)` from `http://yourdomain.com` to `https://yourdomain.com`. Click "Save Changes." You will likely be logged out and need to log back in.
2.  **Use a "Force HTTPS" Plugin (Optional but Recommended):** Plugins like "Really Simple SSL" can automatically handle mixed content issues and ensure all links are updated to HTTPS.

---

## Step 5: Verify Your SSL Installation

After installation and forcing HTTPS, it's crucial to verify that your SSL certificate is correctly installed and working.

1.  **Check your Browser:**
    * Open your website in your browser. Look for the padlock icon in the address bar. Click on it for certificate details.
2.  **Use Online SSL Checkers:**
    * Use tools like [SSL Shopper's SSL Checker](https://www.sslshopper.com/ssl-checker.html) or [Qualys SSL Labs SSL Test](https://www.ssllabs.com/ssltest/) to perform a comprehensive scan of your SSL certificate and identify any issues like mixed content warnings or incomplete chains. Simply enter your domain name and run the test.

---

By following these steps, you can ensure your Salama Hosting website is fully secured with an SSL certificate, building trust with your visitors and benefiting from improved search engine visibility.