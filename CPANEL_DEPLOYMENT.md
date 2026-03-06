# cPanel Deployment Guide for Thee Zulu Yogi Website

## Pre-Deployment Checklist
- [ ] Domain name registered and pointed to hosting server
- [ ] cPanel hosting account set up
- [ ] SSL certificate installed (recommended)

## Files to Upload
Upload ALL files and folders to your cPanel hosting:
- `index.html` (main website file)
- `favicon.jpeg` (browser tab icon)
- `logo.jpeg` (site logo)
- `pics/` folder (all images)
- `.htaccess` (server configuration)
- `robots.txt` (SEO configuration)

## Deployment Steps

### Method 1: File Manager (Recommended for beginners)
1. Log into your cPanel account
2. Navigate to **File Manager**
3. Go to `public_html` directory (or your domain's root folder)
4. Click **Upload** button
5. Select and upload all files and folders
6. Ensure the `pics` folder structure is maintained

### Method 2: FTP Upload
1. Use an FTP client (FileZilla, WinSCP, etc.)
2. Connect using your cPanel FTP credentials:
   - Host: ftp.yourdomain.com
   - Username: Your cPanel username
   - Password: Your cPanel password
   - Port: 21
3. Upload all files to `public_html` directory

### Method 3: Git Deployment (Advanced)
1. In cPanel, go to **Git Version Control**
2. Click **Create**
3. Enter repository URL: `https://github.com/Princengwane/Thee-Zulu-Yogi.git`
4. Set clone path to `public_html` or your domain folder
5. Click **Create**

## Post-Deployment Configuration

### 1. Enable HTTPS (SSL)
1. In cPanel, go to **SSL/TLS Status**
2. Install free Let's Encrypt SSL certificate
3. After SSL is active, uncomment these lines in `.htaccess`:
   ```apache
   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   ```

### 2. Verify File Permissions
- Files: 644
- Folders: 755
- `.htaccess`: 644

### 3. Test the Website
1. Visit your domain: `http://yourdomain.com`
2. Test all navigation links
3. Test the contact form submission
4. Check mobile responsiveness
5. Verify social media links work

### 4. Set Up Email (Optional)
If you want to receive contact form emails:
1. Go to **Email Accounts** in cPanel
2. Create email: `info@yourdomain.com` or `theezuluyogi@yourdomain.com`
3. Consider updating the Google Form or adding server-side email handling

## Performance Optimization

### Enable Compression
Already configured in `.htaccess` - no action needed.

### Browser Caching
Already configured in `.htaccess` - no action needed.

### Image Optimization (Optional)
Consider compressing images in the `pics/` folder for faster loading:
- Use tools like TinyPNG or ImageOptim
- Recommended: Convert to WebP format for better compression

## Troubleshooting

### Site not loading
- Check if files are in correct directory (`public_html`)
- Verify domain DNS is pointing to hosting server
- Clear browser cache

### Images not showing
- Check file paths are correct (case-sensitive on Linux servers)
- Verify `pics/` folder uploaded correctly
- Check file permissions (should be 644)

### .htaccess errors
- If site shows 500 error, temporarily rename `.htaccess` to `.htaccess.bak`
- Contact hosting support to enable required Apache modules

### Contact form not working
- The form currently submits to Google Forms (no server-side processing needed)
- Ensure internet connection is stable when testing

## Security Recommendations
1. Keep cPanel password strong and secure
2. Enable two-factor authentication in cPanel
3. Regularly backup your website files
4. Monitor access logs for suspicious activity
5. Keep all software updated

## Backup Strategy
1. Use cPanel **Backup Wizard** to create regular backups
2. Download backups to local storage
3. Consider automated daily backups if available in your hosting plan

## Support
- Hosting Support: Contact your cPanel hosting provider
- Website Issues: Contact Nobz Tech at https://nobztech.co.za/
- Developer: Check GitHub repository for updates

## Domain Configuration
Once deployed, update these if needed:
- Google Form submission URL (already configured)
- Social media links (already configured)
- Contact information (already configured)

---

**Note:** This is a static HTML website with no database requirements, making deployment straightforward and hosting costs minimal.
