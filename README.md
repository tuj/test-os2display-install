# Example installation of os2display in a vagrant box

<pre>
  mkdir htdocs

  # git clone https://github.com/os2display/docs.git htdocs/docs

  # Because of fixes to install script.
  # And commented-out commands, because of permission issues with vagrant.
  git clone https://github.com/tuj/docs.git docs
  cd docs
  git checkout hotfix/install-update
  cd ..

  vagrant up
  
  vagrant ssh
  
  sudo -i
  
  cd /vagrant/docs/installation

  export LANGUAGE=en_US.UTF-8
  export LANG=en_US.UTF-8
  export LC_ALL=en_US.UTF-8
  locale-gen en_US.UTF-8
  dpkg-reconfigure locales
  
  ./prepare_server.sh
  
  # MySQL root password: vagrant
    
  ./setup.sh
  
  #############
  ## Answers
  #############
  
  # Use fake SSL certificate (y/n)? y
  # What should we install (1-5)? 1
  
  ## Installing Search Node:
  
  # Where to place search node (/home/www/search_node): /vagrant/htdocs/search_node
  # Search node FQDN (search.example.com): search.test-os2display.vm
  # Name to identify the search index by (os2display-index):
  # Name to identify the API key by (os2display-test):
  # Who should the search node be runned as (root):
  
  ## Installing Middleware:
  
  # Where to place middleware (/home/www/middleware): /vagrant/htdocs/middleware
  # Middelware FQDN (middleware.example.com): middleware.test-os2display.vm
  # Administrator username (admin):
  # Administrator password (admin):
  # Secret token used in communcation (MySuperSecret):
  # Name to identify the API key by (os2display-test):
  # FQDN for the administration interface (admin.example.com): admin.test-os2display.vm
  # Who should the middleware be runned as (root):

  ## Installing Administration interface:
  
  # Where to place administration interface (/home/www/example_com/admin): /vagrant/htdocs/admin
  # Admin FQDN (admin.example.com): admin.test-os2display.vm
  # Database (admin_test-os2display_vm): os2display
  # Database username (root):
  # Database password (root): vagrant
  # Secret token (ThisTokenIsNotSoSecretChangeIt):
  # Mail from address (webmaster@os2display.dk): webmaster@admin.test-os2display.vm
  # Mail from name (webmaster):
  # Search host (https://search.example.com): 'https://search.test-os2display.vm'
  # Search API key:
  # Search index:
  # Middleware host (https://middleware.example.com): 'https://middleware.test-os2display.vm'
  # Middleware API key:
  # Zencoder API key:
  # Site title (OS2Display example): TestOS2Display

  # Super user name (admin): admin
  # Super user password (admin): admin
  # Super user mail (admin@example.com): [your mail]

  # Name of the normal OS user (root): vagrant

  ## Installing Screen:

  # Where to place screen (/home/www/example_com/screen): /vagrant/htdocs/screen
  # Screen FQDN (screen.example.com): screen.test-os2display.vm
  # Admin FQDN (admin.example.com): admin.test-os2display.vm
  # Middleware API key: 

  # Manual node module install (because of vagrant permissions)
  # exit sudo mode
  # ./install.sh  (in search_node and middleware)
  # sudo service supervisor restart

  # Activate search index  

  # Make sure cron is set for www-data
  sudo crontab -e -u www-data
  # Insert:
  # */1 * * * * /usr/bin/php /vagrant/htdocs/admin/app/console os2display:core:cron --env=prod
  
  ## Visit and accept false certificates.
  # https://admin.test-os2display.vm/
  # https://screen.test-os2display.vm/
  # https://middleware.test-os2display.vm/
  # https://search.test-os2display.vm/
  
  # Enable templates: https://admin.test-os2display.vm/#/admin-templates
  # Create one of each type of content.

  # Test that screen works and gets content from backend.
</pre>

## Troubleshooting

Search or middleware give 502. Try to run apps directly from their directories:
<pre>
  node app.js
</pre>

Make sure search indexes are activated:
See https://github.com/os2display/vagrant/blob/development/scripts/search_activate.sh for script example.

Make sure 1 of each type of content has been created, to initialize search:
See https://github.com/os2display/vagrant/blob/development/scripts/search_initialize.sh for script example.

