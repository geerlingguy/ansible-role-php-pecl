# Ansible php-pecl

Installs PHP PECL extensions on servers with PHP already installed.

## Role Variables

Available variables are listed below, along with default values:

 - *php_pecl_extensions*: A list of extensions that should be installed via `pecl install`.
 - *php_pecl_apt_packages*: The list of apt packages to install, you can use this variables to install libraries
   needed by the installed PECL extensions (ex. install ```libcurl3-openssl-dev``` when installing the ```pecl_http```
   extensions. Defaults to ```[php-pear]```.

## Example Usages

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - role: geerlingguy.php-pecl
          php_pecl_extensions:
           - xdebug


    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - role: geerlingguy.php-pecl
          php_pecl_extensions:
            - yaml
          php_pecl_apt_packages:
            - make
            - php-pear
            - php5-dev
            - libyaml-dev


## TODO

  - Continue refining the `changed`/`failed` conditions for PECL. Yuck.

## License

MIT / BSD

## Author Information

This role was created in 2014 by Jeff Geerling (@geerlingguy), author of Ansible for DevOps. You can find out more about the book at http://ansiblefordevops.com/, and learn about the author at http://jeffgeerling.com/.
