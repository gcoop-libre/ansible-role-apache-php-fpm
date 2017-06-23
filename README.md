Role Name
=========

An Ansible Role that configures Apache for PHP-FPM (php7.0) usage on Debian 9

Requirements
------------

This role is dependent upon `gcoop-lobre.apache`, and also requires you have PHP running with PHP-FPM somewhere on the server or elsewhere (I usually configure PHP with the `geerlingguy.php` role).

Role Variables
--------------


* apache_php_fpm_user: www-data
* apache_php_fpm_group: www-data
* apache_php_fpm_listen: /run/php/php7.0-fpm.sock
* apache_php_fpm_listen_owner: www-data
* apache_php_fpm_listen_group: www-data
* apache_php_fpm_pm: ondemand
* apache_php_fpm_pm_max_children: 5
* apache_php_fpm_pm_start_servers: 2
* apache_php_fpm_pm_min_spare_servers: 1
* apache_php_fpm_pm_max_spare_servers: 3
* apache_php_fpm_request_slowlog_timeout: 2



Dependencies
------------

None

Example Playbook
----------------

    - hosts: [suitecrmsaas]
      become: yes
      remote_user: "{{ remote_user }}"

      vars:
        apache_vhosts:
          - servername: "default"
            documentroot: "/var/www/html"

      roles:
        - role: geerlingguy.php
        - role: gcoop-libre.apache
        - role: gcoop-libre.apache-php-fpm

License
-------

GPLv2

Author Information
------------------

This role was created in 2017 with love by [gcoop Cooperativa de Software Libre](http://gcoop.coop).
