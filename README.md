# Example installation of os2display in a vagrant box

<pre>
  mkdir htdocs

  git clone https://github.com/os2display/docs.git htdocs/docs

  vagrant up
  
  vagrant ssh
  
  sudo -i
  
  cd /vagrant/htdocs/docs/installation
  
  ./prepare_server.sh
  
  # MySQL root password: vagrant
  
  ## Adjust versions to newest in setup.sh:
  
  ## Versions
  # SEARCH_NODE_VERSION="v2.1.8"
  # MIDDLEWARE_VERSION="5.0.2"
  # ADMIN_VERSION="5.1.1"
  # SCREEN_VERSION="5.0.3"
  
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
  # FQDN for the administration interface (admin.example.com): middleware.test-os2display.vm
  # Who should the middleware be runned as (root):

  ## Installing Administration interface:
  
  # Where to place administration interface (/home/www/example_com/admin): /vagrant/htdocs/admin
  # Admin FQDN (admin.example.com): admin.test-os2display.vm
  # Database (admin_test-os2display_vm): os2display
  # Database username (root):
  # Database password (vagrant): vagrant
  # Secret token (ThisTokenIsNotSoSecretChangeIt):
  # Mail from address (webmaster@os2display.dk): webmaster@admin.test-os2display.vm
  # Mail from name (webmaster):
  # Search host (https://search.example.com): search.test-os2display.vm
  # Search API key:
  # Search index:
  # Middleware host (https://middleware.example.com): middleware.test-os2display.vm
  # Middleware API key:
  # Zencoder API key:
  # Site title (OS2Display example): Test OS2Display

  

</pre>
