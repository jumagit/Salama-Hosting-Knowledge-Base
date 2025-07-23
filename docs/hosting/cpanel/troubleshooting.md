# CPanel Hosting Troubleshooting Guide

## Login and Access Issues

### Cannot Access CPanel

**Symptom**: Unable to load cPanel login page or receive timeout errors.

**Common Causes & Solutions:**

**1. Incorrect URL**
- Verify the correct cPanel URL format
- Try alternative ports: `:2083` (SSL) or `:2082` (non-SSL)
- Use server IP instead of domain if DNS issues exist

**2. Browser Issues**
- Clear browser cache and cookies
- Disable browser extensions temporarily
- Try a different browser or incognito mode
- Check for JavaScript blockers

**3. Network Connectivity**
- Test internet connection with other websites
- Check firewall settings blocking the cPanel ports
- Try accessing from a different network
- Contact ISP if port blocking is suspected

**4. Server Issues**
- Check server status with your hosting provider
- Verify server maintenance schedules
- Review hosting provider's status page

### Login Credentials Not Working

**Symptom**: "Login Incorrect" or authentication failure messages.

**Troubleshooting Steps:**

1. **Verify Credentials**
   - Double-check username and password
   - Ensure caps lock is not enabled
   - Copy credentials from hosting provider's email

2. **Password Reset**
   - Use hosting provider's password reset option
   - Contact support for manual password reset
   - Check for temporary account suspension

3. **Account Status**
   - Verify hosting account is active and paid
   - Check for policy violations causing suspension
   - Review billing status with hosting provider

## Website Loading Issues

### Website Not Loading

**Symptom**: "This site can't be reached" or blank pages when visiting your domain.

**Diagnostic Steps:**

**1. DNS Issues**
```bash
# Check DNS propagation
nslookup yourdomain.com
dig yourdomain.com
```

**Solutions:**
- Verify nameservers are correctly set at domain registrar
- Allow 24-48 hours for DNS propagation
- Clear local DNS cache: `ipconfig /flushdns` (Windows) or `sudo dscacheutil -flushcache` (Mac)

**2. File Location Issues**
- Ensure website files are in `public_html` directory
- Check for correct index file (`index.html` or `index.php`)
- Verify file permissions: 644 for files, 755 for directories

**3. Domain Configuration**
- Check domain is properly added in cPanel
- Verify addon domains or subdomains are configured correctly
- Review redirect settings for infinite loops

### 500 Internal Server Error

**Symptom**: Server error messages instead of website content.

**Common Causes:**

**1. .htaccess File Issues**
- Rename `.htaccess` to `.htaccess-backup` temporarily
- If site loads, review .htaccess syntax line by line
- Common issues: syntax errors, incompatible directives

**2. File Permissions**
- Set files to 644 permissions
- Set directories to 755 permissions
- Avoid 777 permissions for security reasons

**3. PHP Errors**
- Check error logs in cPanel under "Error Logs"
- Review PHP version compatibility
- Check for missing PHP extensions

**4. Resource Limits**
- Monitor resource usage in cPanel
- Optimize scripts if hitting CPU or memory limits
- Contact hosting provider about limit increases

### 404 Page Not Found Errors

**Symptom**: Specific pages return 404 errors while others work.

**Troubleshooting:**

1. **File Existence**
   - Verify files exist in correct directories
   - Check case sensitivity in file names
   - Ensure proper file extensions

2. **URL Rewriting**
   - Review .htaccess rewrite rules
   - Check for broken internal links
   - Verify permalink structures (WordPress)

3. **Directory Structure**
   - Confirm proper folder organization
   - Check for missing index files in directories
   - Review addon domain directory mappings

## Email Problems

### Cannot Send or Receive Email

**Symptom**: Email bounces, delays, or complete failure to send/receive.

**Email Server Settings Verification:**

**IMAP Settings:**
- Server: mail.yourdomain.com or server hostname
- Port: 993 (SSL) or 143 (non-SSL)
- Security: SSL/TLS

**SMTP Settings:**
- Server: mail.yourdomain.com or server hostname
- Port: 465 (SSL) or 587 (TLS) or 25
- Authentication: Required

**POP3 Settings:**
- Server: mail.yourdomain.com
- Port: 995 (SSL) or 110 (non-SSL)

**Common Solutions:**

1. **Authentication Issues**
   - Verify email account exists in cPanel
   - Check password accuracy
   - Enable authentication in email client

2. **DNS Configuration**
   - Verify MX records point to correct mail server
   - Check SPF, DKIM, and DMARC records
   - Allow time for DNS propagation

3. **Quota and Limits**
   - Check mailbox quota usage
   - Clear old emails if quota is full
   - Verify sending limits aren't exceeded

### Email Marked as Spam

**Symptom**: Legitimate emails being filtered to spam folders.

**Spam Prevention:**

1. **Authentication Setup**
   - Configure SPF records: `v=spf1 include:servername.com ~all`
   - Set up DKIM signing in cPanel
   - Create DMARC policy: `v=DMARC1; p=quarantine; rua=mailto:admin@yourdomain.com`

2. **Content Optimization**
   - Avoid spam trigger words
   - Maintain good text-to-image ratio
   - Include unsubscribe links
   - Use reputable email service practices

3. **Server Reputation**
   - Monitor server IP reputation
   - Report false spam classifications
   - Maintain clean mailing lists

## Database Issues

### Database Connection Errors

**Symptom**: "Error establishing database connection" or similar messages.

**Troubleshooting Steps:**

1. **Credential Verification**
   - Check database name, username, and password
   - Verify database user has proper privileges
   - Test connection through phpMyAdmin

2. **Database Server Status**
   - Check if MySQL service is running
   - Review database server error logs
   - Monitor resource usage affecting database performance

3. **Configuration Issues**
   - Verify database host name (usually localhost)
   - Check for table corruption and repair if needed
   - Review database size limits

### Database Performance Issues

**Symptom**: Slow website loading, timeouts, or database errors under load.

**Optimization Strategies:**

1. **Query Optimization**
   - Identify slow queries in logs
   - Add appropriate database indexes
   - Optimize complex JOIN operations
   - Remove unnecessary queries

2. **Database Maintenance**
   - Regular table optimization
   - Remove spam and unnecessary data
   - Archive old data to reduce database size
   - Update database statistics

3. **Caching Implementation**
   - Enable database query caching
   - Implement application-level caching
   - Use content delivery networks (CDN)

## SSL Certificate Issues

### SSL Certificate Not Working

**Symptom**: Browser security warnings or "Not Secure" indicators.

**Common SSL Problems:**

1. **Certificate Installation**
   - Verify certificate is properly installed
   - Check certificate chain completeness
   - Ensure certificate matches domain name

2. **Mixed Content Issues**
   - Update all HTTP links to HTTPS
   - Fix images, CSS, and JavaScript references
   - Use relative URLs when possible
   - Check for hardcoded HTTP links in database

3. **Certificate Renewal**
   - Set up automatic renewal for Let's Encrypt
   - Monitor certificate expiration dates
   - Update certificate before expiration
   - Test renewal process regularly

### HTTPS Redirect Issues

**Symptom**: Website loads over HTTP despite SSL certificate installation.

**Solutions:**

1. **Force HTTPS Redirect**
   ```apache
   # Add to .htaccess file
   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   ```

2. **cPanel SSL Configuration**
   - Enable "Force HTTPS Redirect" in SSL/TLS settings
   - Update website URLs in application settings
   - Clear browser cache after changes

## File and FTP Issues

### File Upload Problems

**Symptom**: Cannot upload files through File Manager or FTP.

**Common Causes:**

1. **Permission Issues**
   - Check directory write permissions (755 or 775)
   - Verify user ownership of directories
   - Review file permission requirements

2. **Size Limitations**
   - Check PHP upload_max_filesize setting
   - Verify post_max_size configuration
   - Consider file compression for large uploads

3. **File Type Restrictions**
   - Review allowed file extensions
   - Check for security restrictions on executable files
   - Verify MIME type configurations

### FTP Connection Problems

**Symptom**: Cannot connect to FTP server or frequent disconnections.

**Troubleshooting:**

1. **Connection Settings**
   - Verify FTP server address and port (21 or 22 for SFTP)
   - Check username and password accuracy
   - Test both active and passive FTP modes

2. **Firewall and Network**
   - Configure firewall to allow FTP ports
   - Try SFTP (port 22) if FTP is blocked
   - Check with ISP about FTP restrictions

3. **Client Configuration**
   - Update FTP client software
   - Adjust timeout settings
   - Use different FTP clients for comparison

## Performance Issues

### Slow Website Loading

**Symptom**: Pages take excessive time to load or timeout.

**Performance Optimization:**

1. **Resource Usage Analysis**
   - Monitor CPU and memory usage in cPanel
   - Identify resource-intensive processes
   - Review error logs for bottlenecks

2. **Content Optimization**
   - Compress images and media files
   - Minify CSS and JavaScript files
   - Enable gzip compression
   - Implement browser caching headers

3. **Database Optimization**
   - Optimize database tables regularly
   - Remove unnecessary plugins and themes
   - Clean up spam comments and revisions
   - Implement database caching

### High Resource Usage Warnings

**Symptom**: Receiving resource limit notifications from hosting provider.

**Resource Management:**

1. **Identify Resource Hogs**
   - Review resource usage statistics
   - Monitor processes during peak times
   - Identify problematic scripts or applications

2. **Optimization Strategies**
   - Update software to latest versions
   - Remove unused plugins and applications
   - Implement caching solutions
   - Optimize database queries

3. **Upgrade Considerations**
   - Evaluate hosting plan limitations
   - Consider VPS or dedicated hosting
   - Implement content delivery networks

## Security Issues

### Malware and Hacking

**Symptom**: Website defaced, redirects to malicious sites, or security warnings.

**Security Response:**

1. **Immediate Actions**
   - Change all passwords (cPanel, FTP, database, CMS admin)
   - Update all software to latest versions
   - Scan for malware using security plugins
   - Review user accounts and permissions

2. **Cleanup Process**
   - Restore from clean backup if available
   - Remove malicious files and code
   - Update security plugins and configurations
   - Implement stronger authentication methods

3. **Prevention Measures**
   - Enable automatic updates
   - Use strong, unique passwords
   - Install security monitoring tools
   - Regular security audits and scans

### Suspicious Activity

**Symptom**: Unusual traffic patterns, unauthorized file changes, or resource spikes.

**Investigation Steps:**

1. **Log Analysis**
   - Review access logs for suspicious patterns
   - Check error logs for attack attempts
   - Monitor resource usage during incidents
   - Analyze email logs for spam activity

2. **Security Hardening**
   - Implement IP blocking for malicious addresses
   - Enable two-factor authentication
   - Restrict file permissions and access
   - Use security headers and CSP policies

## Application-Specific Issues

### WordPress Problems

**Common WordPress Issues:**

1. **White Screen of Death**
   - Enable debug mode: `define('WP_DEBUG', true);`
   - Check error logs for specific errors
   - Deactivate plugins one by one
   - Switch to default theme temporarily

2. **Plugin Conflicts**
   - Deactivate all plugins
   - Activate plugins one by one to identify conflicts
   - Check plugin compatibility with WordPress version
   - Review plugin error logs

3. **Database Issues**
   - Repair WordPress database through cPanel
   - Update WordPress URLs in database after migration
   - Check for corrupted tables
   - Optimize database regularly

### E-commerce Platform Issues

**Common E-commerce Problems:**

1. **Payment Gateway Errors**
   - Verify SSL certificate installation
   - Check payment gateway credentials
   - Test in sandbox mode first
   - Review payment gateway logs

2. **Inventory Management**
   - Check database connections
   - Verify product import/export processes
   - Monitor stock level updates
   - Review automated inventory systems

## Advanced Troubleshooting

### Using Error Logs

**Log Locations in cPanel:**
- Error Logs: Shows Apache and PHP errors
- Raw Access Logs: Detailed visitor information
- AWStats: Processed log statistics

**Reading Error Logs:**
- Look for timestamps matching problem periods
- Identify recurring error patterns
- Note specific file or script errors
- Check for resource limit violations

### Command Line Troubleshooting

**If SSH access is available:**

```bash
# Check disk usage
df -h

# Monitor real-time logs
tail -f /path/to/error.log

# Check running processes
top

# Test database connection
mysql -u username -p database_name

# Check PHP configuration
php -m  # Show loaded modules
php -v  # Show PHP version
```

### Testing and Validation

**Website Testing Tools:**
- GTmetrix for performance analysis
- SSL Labs for certificate validation
- DNS Checker for propagation status
- W3C Validator for HTML/CSS validation

**Local Testing:**
- Use staging environments for testing fixes
- Backup before making changes
- Test on different devices and browsers
- Validate functionality after fixes

## When to Contact Support

### Escalation Criteria

Contact your hosting provider when:
- Server-level issues require administrative access
- Resource limits need adjustment beyond self-service options
- Security incidents require professional investigation
- Hardware failures or network issues affect service
- Complex configuration changes need expert assistance

### Preparing Support Requests

**Information to Provide:**
- Detailed description of the problem
- Steps taken to reproduce the issue
- Relevant error messages and screenshots
- Timeline of when the issue started
- Recent changes made to the account

**Log Information:**
- Relevant error log entries
- Resource usage during problem periods
- Specific URLs or areas affected
- Browser and device information

This troubleshooting guide covers the most common issues encountered with cPanel hosting. Remember that systematic diagnosis and testing of solutions is key to effective troubleshooting. When in doubt, start with the simplest solutions before moving to more complex fixes, and always maintain current backups before making significant changes.