.. _backup_link: (https://assets.nagios.com/downloads/nagiosxi/docs/Configuring-SSL-with-Nagios%20XI.pdf)

Add SSL cert to nagios server
*********************************************

Installing packages
########################

.. code-block:: console

    dnf -y install mod_ssl openssl

Certificate Directory
#############################

This is from the */usr/local/nagiosxi/var/certs* folder

.. code-block::console

    mkdir -p /usr/local/nagiosxi/var/certs
    chown -R nagios.nagios /usr/local/nagiosxi/var/certs
    chmod 775 /usr/local/nagiosxi/var/certs
    cd /usr/local/nagiosxi/var/certs/

Generate needed files and permissions
##########################################


.. code-block:: console

    openssl genrsa -out nagiosxi.key 2048
    openssl req -new -key nagiosxi.key -out nagiosxi.csr
    openssl x509 -req -days 365 -in nagiosxi.csr -signkey nagiosxi.key -out nagiosxi.crt
    chmod go-rwx nagiosxi.*

Update Apache Configuration
#####################################

.. code-block:: console

    vi /etc/httpd/conf.d/ssl.conf
        SSLCertificateFile /usr/local/nagiosxi/var/certs/nagiosxi.crt
        SSLCertificateKeyFile /usr/local/nagiosxi/var/certs/nagiosxi.key

In the same file, navigate to the end and before the line *</VirtualHost>* add the following lines:

.. code-block:: console

    <IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule nagiosxi/api/v1/(.*)$ /usr/local/nagiosxi/html/api/v1/index.php?request=$1 [QSA,NC,L]
    </IfModule>

Add the following lines to the end of the file

.. code-block:: console

    <IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule nagiosxi/api/v1/(.*)$ /usr/local/nagiosxi/html/api/v1/index.php?request=$1 [QSA,NC,L]
    NEW_LINE: RewriteCond %{HTTPS} off
    NEW_LINE: RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
    </IfModule>

Restart Apache
#######################

.. code-block:: console

    systemctl restart httpd