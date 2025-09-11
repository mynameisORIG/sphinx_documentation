composer
***************

What is it
################

A composer is a tool for dependency management in PHP-based applications running on the RHEL or CentOS operating systems. It simplifies managing dependencies by allowing developers to easily install, update, and remove packages from a centralized repository. A composer is a command-line tool that uses a JSON file called “composer.json” to specify the dependencies and their version constraints.

Commands to install
#########################

URLS:

* https://vpsie.com/knowledge-base/how-to-install-composer-on-rhel-or-centos/
* https://reintech.io/blog/install-use-composer-centos-9#google_vignette

Option 1
+++++++++++++++++++

.. code-block:: console

    sudo dnf install wget -y
    sudo wget https://getcomposer.org/installer -O composer-installer.php
    sudo php composer-installer.php --filename=composer --install-dir=/usr/bin

Option 2
++++++++++++++++++

.. code-block:: console

    sudo dnf install php-cli php-json php-zip wget unzip
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
    sudo mv composer.phar /usr/local/bin/composer
    composer init