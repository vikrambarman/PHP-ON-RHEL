# PHP-ON-RHEL
Complete guide to install PHP on RHEL Server
# PHP Installation Guide on Red Hat

This guide walks you through installing PHP on Red Hat (RHEL) with Apache or Nginx web server support.

## 1. Enable EPEL and Remi Repositories

The default Red Hat repositories may not have the latest PHP versions. You can use the **Remi** repository for more updated versions of PHP. You might also need the **EPEL** (Extra Packages for Enterprise Linux) repository.

```bash
sudo yum install epel-release
sudo yum install https://rpms.remirepo.net/enterprise/remi-release-9.rpm

2. Install and Enable the Desired PHP Version

List available PHP versions from the Remi repository:

bash

sudo yum module list php

Enable the desired PHP version. For example, to install PHP 8.1:

bash

sudo yum module reset php
sudo yum module enable php:remi-8.1

3. Install PHP and Required Extensions

Once the desired PHP module is enabled, install PHP with the following command:

bash

sudo yum install php php-cli php-mysqlnd php-json php-common php-xml php-mbstring

This will install PHP along with common extensions like MySQL support, JSON, XML, and more. You can add more extensions as needed.
4. Verify PHP Installation

Check the installed PHP version:

bash

php -v

This will display the PHP version and additional information about the installation.
5. Configure Apache Web Server to Work with PHP

If you’re using Apache as your web server, install the PHP module for Apache:

bash

sudo yum install httpd
sudo systemctl start httpd
sudo systemctl enable httpd

Then restart Apache to load PHP:

bash

sudo systemctl restart httpd

6. Test PHP Setup

Create a PHP test file to check if PHP is correctly installed. Place this file in the Apache root directory (usually /var/www/html):

bash

sudo nano /var/www/html/info.php

Add the following PHP code to the file:

php

<?php
phpinfo();
?>

Save the file and then access it through a browser by visiting:

arduino

http://localhost/info.php

You should see a page with detailed information about your PHP installation.
7. Install PHP-FPM (Optional)

If you prefer using PHP-FPM (FastCGI Process Manager), install it with:

bash

sudo yum install php-fpm

Enable and start PHP-FPM:

bash

sudo systemctl enable php-fpm
sudo systemctl start php-fpm

8. Restart Apache or Nginx (Depending on Your Setup)

    If you're using Apache, restart it:

bash

sudo systemctl restart httpd

    For Nginx users, after configuring Nginx to use PHP-FPM, restart Nginx:

bash

sudo systemctl restart nginx

9. Check and Configure Firewall

Ensure your firewall is open for HTTP and HTTPS traffic:

bash

sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload

Conclusion

This completes the installation of PHP on Red Hat with Apache or Nginx support. You are now ready to run PHP applications on your RHEL server.

vbnet


This `README.md` provides a clear and organized step-by-step guide for installing PHP on Red Hat, suitable for use in a GitHub repository.
