setup
***************

base path -> `/etc/puppetlabs/code/environments/production/`

.. code-base:: console
    modules
    |
    |
    ----MODULE_NAME
        |
        |
        ----Files
        ---- Templates
        ----manifests

Files
############

Templates
#####################

manifests
################

This is the core Puppet code that defines the desired state of your systems.

config.pp
+++++++++++++++++

This specifies any services and files to use

.. code-block:: console

    class nextcloud::config {
        if $::fqdn == 'nextcloud.deathstar.com' {
            service { httpd:
                ensure	=>	running
            }
            file { "/var/www/html/nextcloud/config/config.php":
                path    => "/var/www/html/nextcloud/config/config.php",
                owner   => apache,
                group   => apache,
                mode   =>  "0644",
                source => "puppet:///modules/nextcloud/config.php",
            }
        }
    }

init.pp
+++++++++++++++

What the puppet module is called within puppet

.. code-block:: console

    class nextcloud {
        notify {"nextcloud loaded":}
        contain nextcloud::config
    }

services.pp
+++++++++++++++++

What services need to be up for this module on a host

.. code-block:: console

    class named::service {
        if $facts['networking']['fqdn'] == 'dns.deathstar.com' {
                service { named:
                        ensure  => running,
                        enable     => true,
                        hasrestart => true,
                        hasstatus  => true,
                }
        }
    }

install.pp
++++++++++++++++

Installs packages on the systems

.. code-block:: console

    class named::install {
        if $facts['networking']['fqdn'] == 'dns.deathstar.com' {
            package { 'bind':
                ensure  => installed,
                name    => bind,
            }
        }
    }
