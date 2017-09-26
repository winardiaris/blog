---
id: 163
title: HowTo Install Redmine 2.5.x on Ubuntu 14.04 with Apache2 Phusion Passenger MySQL and Subversion
date: 2015-10-20T17:45:53+00:00
author: winardiaris
layout: post
guid: http://arwin.my.id/blog/?p=163
permalink: /howto-install-redmine-2-5-x-on-ubuntu-14-04-with-apache2-phusion-passenger-mysql-and-subversion/
dsq_thread_id:
  - "5201852866"
categories:
  - Catatan
---
<div class="wiki wiki-page">
  <ul class="toc">
    <ul>
      <li>
        <a href="#Installing-dependencies">Installing dependencies</a>
      </li>
      <li>
        <a href="#Installing-Subversion">Installing Subversion</a>
      </li>
      <li>
        <a href="#Installing-Ruby-and-Ruby-on-Rails">Installing Ruby and Ruby on Rails</a>
      </li>
      <li>
        <a href="#Installing-of-Redmine">Installing of Redmine</a> <ul>
          <li>
            <a href="#Redmine">Redmine</a>
          </li>
          <li>
            <a href="#MySQL">MySQL</a>
          </li>
          <li>
            <a href="#Configuration">Configuration</a>
          </li>
        </ul>
      </li>
      
      <li>
        <a href="#Installing-Phusion-Passenger">Installing Phusion Passenger</a> <ul>
          <li>
            <a href="#Add-repository">Add repository</a>
          </li>
          <li>
            <a href="#Installing">Installing</a>
          </li>
          <li>
            <a href="#Configuration-2">Configuration</a>
          </li>
        </ul>
      </li>
      
      <li>
        <a href="#Start-Redmine">Start Redmine</a>
      </li>
      <li>
        <a href="#e-Mail-configuration">e-Mail configuration</a>
      </li>
      <li>
        <a href="#Autoupdate-Subversion-repository-view">Autoupdate Subversion repository view</a>
      </li>
    </ul>
  </ul>
  
  <p>
    <a name="Installing-dependencies"></a>
  </p>
  
  <h2>
    Installing dependencies
  </h2>
  
  <pre>sudo apt-get update && sudo apt-get upgrade -y

sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server php5-mysql phpmyadmin libapache2-mod-perl2 libcurl4-openssl-dev libssl-dev apache2-prefork-dev libapr1-dev libaprutil1-dev libmysqlclient-dev libmagickcore-dev libmagickwand-dev curl git-core patch build-essential bison zlib1g-dev libssl-dev libxml2-dev libxml2-dev sqlite3 libsqlite3-dev autotools-dev libxslt1-dev libyaml-0-2 autoconf automake libreadline6-dev libyaml-dev libtool imagemagick apache2-utils
</pre>
  
  <p>
    I don&#8217;t know if every package needed, but it works.
  </p>
  
  <p>
    <a name="Installing-Subversion"></a>
  </p>
  
  <h2>
    Installing Subversion<a class="wiki-anchor" href="#Installing-Subversion"></a>
  </h2>
  
  <pre>sudo apt-get install subversion libapache2-svn
</pre>
  
  <pre>sudo mkdir -p /var/lib/svn
sudo chown -R www-data:www-data /var/lib/svn
sudo a2enmod dav_svn
</pre>
  
  <p>
    Open config file
  </p>
  
  <pre>sudo nano /etc/apache2/mods-enabled/dav_svn.conf
</pre>
  
  <p>
    Uncomment following lines
  </p>
  
  <pre>&lt;Location /svn&gt;
    DAV svn
    SVNParentPath /var/lib/svn
    AuthType Basic
    AuthName "My repository" 
    AuthUserFile /etc/apache2/dav_svn.passwd
    AuthzSVNAccessFile /etc/apache2/dav_svn.authz
    &lt;LimitExcept GET PROFIND OPTIONS REPORT&gt;
    Require valid-user
    &lt;/LimitExcept&gt;
&lt;/Location&gt;
</pre>
  
  <pre>sudo a2enmod authz_svn
</pre>
  
  <p>
    Add the redmine user for reading from repository
  </p>
  
  <pre>sudo htpasswd -c /etc/apache2/dav_svn.passwd redmine

sudo service apache2 restart
</pre>
  
  <p>
    Create the repository
  </p>
  
  <pre>sudo svnadmin create --fs-type fsfs /var/lib/svn/my_repository
sudo chown -R www-data:www-data /var/lib/svn
</pre>
  
  <p>
    Open file for configuration of repository access
  </p>
  
  <pre>sudo nano /etc/apache2/dav_svn.authz
</pre>
  
  <p>
    Add access rights for redmine to the repository in the config file
  </p>
  
  <pre>[my_repository:/]
redmine = r
</pre>
  
  <p>
    <a name="Installing-Ruby-and-Ruby-on-Rails"></a>
  </p>
  
  <h2>
    Installing Ruby and Ruby on Rails<a class="wiki-anchor" href="#Installing-Ruby-and-Ruby-on-Rails"></a>
  </h2>
  
  <pre>sudo apt-get install ruby1.9.3 ruby1.9.1-dev ri1.9.1 libruby1.9.1 libssl-dev zlib1g-dev
sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.9.1 400 \
         --slave   /usr/share/man/man1/ruby.1.gz ruby.1.gz \
                        /usr/share/man/man1/ruby1.9.1.1.gz \
        --slave   /usr/bin/ri ri /usr/bin/ri1.9.1 \
        --slave   /usr/bin/irb irb /usr/bin/irb1.9.1 \
        --slave   /usr/bin/rdoc rdoc /usr/bin/rdoc1.9.1

sudo gem update
sudo gem install bundler
</pre>
  
  <p>
    <a name="Installing-of-Redmine"></a>
  </p>
  
  <h2>
    Installing of Redmine<a class="wiki-anchor" href="#Installing-of-Redmine"></a>
  </h2>
  
  <p>
    <a name="Redmine"></a>
  </p>
  
  <h3>
    Redmine<a class="wiki-anchor" href="#Redmine"></a>
  </h3>
  
  <p>
    Exampe for version 2.5.2, change the version number for other releases
  </p>
  
  <pre>cd /usr/share
sudo wget http://www.redmine.org/releases/redmine-2.5.2.tar.gz
sudo tar xvfz redmine-2.5.2.tar.gz
sudo rm redmine-2.5.2.tar.gz
sudo mv redmine-2.5.2 redmine
sudo chown -R root:root /usr/share/redmine
sudo chown www-data /usr/share/redmine/config/environment.rb
sudo ln -s /usr/share/redmine/public /var/www/html/redmine
</pre>
  
  <p>
    <a name="MySQL"></a>
  </p>
  
  <h3>
    MySQL<a class="wiki-anchor" href="#MySQL"></a>
  </h3>
  
  <pre>mysql -u root -p
</pre>
  
  <p>
    Execute following lines to MySQL
  </p>
  
  <pre>CREATE DATABASE redmine character SET utf8;
CREATE user 'redmine'@'localhost' IDENTIFIED BY 'my_password';
GRANT ALL privileges ON redmine.* TO 'redmine'@'localhost';
exit
</pre>
  
  <p>
    Configure Redmine database connection
  </p>
  
  <pre>sudo cp redmine/config/database.yml.example redmine/config/database.yml
</pre>
  
  <p>
    Open database config file
  </p>
  
  <pre>sudo nano redmine/config/database.yml
</pre>
  
  <p>
    Change the username and the password in the config file
  </p>
  
  <pre>database.yml:
production:
 adapter: mysql2
 database: redmine
 host: localhost
 username: redmine
 password: my_password
 encoding: utf8
</pre>
  
  <p>
    <a name="Configuration"></a>
  </p>
  
  <h3>
    Configuration<a class="wiki-anchor" href="#Configuration"></a>
  </h3>
  
  <pre>cd /usr/share/redmine/
sudo bundle install --without development test postgresql sqlite
sudo rake generate_secret_token
sudo RAILS_ENV=production rake db:migrate 
sudo RAILS_ENV=production rake redmine:load_default_data
sudo mkdir public/plugin_assets
sudo chown -R www-data:www-data files log tmp public/plugin_assets
sudo chmod -R 755 files log tmp public/plugin_assets
</pre>
  
  <p>
    <a name="Installing-Phusion-Passenger"></a>
  </p>
  
  <h2>
    Installing Phusion Passenger<a class="wiki-anchor" href="#Installing-Phusion-Passenger"></a>
  </h2>
  
  <p>
    <a name="Add-repository"></a>
  </p>
  
  <h3>
    Add repository<a class="wiki-anchor" href="#Add-repository"></a>
  </h3>
  
  <p>
    Add repository for Phusion Passenger
  </p>
  
  <pre>sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 561F9B9CAC40B2F7
sudo apt-get install apt-transport-https ca-certificates
</pre>
  
  <p>
    Open repository config file
  </p>
  
  <pre>sudo nano /etc/apt/sources.list.d/passenger.list
</pre>
  
  <p>
    Add following repository source
  </p>
  
  <pre>deb https://oss-binaries.phusionpassenger.com/apt/passenger trusty main
</pre>
  
  <pre>sudo chown root: /etc/apt/sources.list.d/passenger.list
sudo chmod 600 /etc/apt/sources.list.d/passenger.list
</pre>
  
  <p>
    <a name="Installing"></a>
  </p>
  
  <h3>
    Installing<a class="wiki-anchor" href="#Installing"></a>
  </h3>
  
  <pre>sudo apt-get update
sudo apt-get install libapache2-mod-passenger
</pre>
  
  <p>
    <a name="Configuration-2"></a>
  </p>
  
  <h3>
    Configuration<a class="wiki-anchor" href="#Configuration-2"></a>
  </h3>
  
  <p>
    Open passenger config file
  </p>
  
  <pre>sudo nano /etc/apache2/mods-available/passenger.conf
</pre>
  
  <p>
    Add following line to passenger config file
  </p>
  
  <pre>PassengerDefaultUser www-data
</pre>
  
  <p>
    Open apache2 config file
  </p>
  
  <pre>sudo nano /etc/apache2/sites-available/000-default.conf
</pre>
  
  <p>
    Add following part to apache2 config file
  </p>
  
  <pre>&lt;Directory /var/www/html/redmine&gt;
    RailsBaseURI /redmine
    PassengerResolveSymlinksInDocumentRoot on
&lt;/Directory&gt;
</pre>
  
  <pre>sudo a2enmod passenger
sudo service apache2 restart
</pre>
  
  <p>
    <a name="Start-Redmine"></a>
  </p>
  
  <h2>
    Start Redmine<a class="wiki-anchor" href="#Start-Redmine"></a>
  </h2>
  
  <p>
    Remine should now available at your host
  </p>
  
  <pre>http://yourhost/redmine
</pre>
  
  <p>
    Login data:<br /> Username: admin<br /> Password: admin
  </p>
  
  <p>
    <a name="e-Mail-configuration"></a>
  </p>
  
  <h2>
    e-Mail configuration<a class="wiki-anchor" href="#e-Mail-configuration"></a>
  </h2>
  
  <p>
    Example for smtp and encryption
  </p>
  
  <p>
    Open redmine config file
  </p>
  
  <pre>sudo nano /usr/share/redmine/config/configuration.yml
</pre>
  
  <p>
    Add following to redmine config file
  </p>
  
  <pre># Outgoing email settings

production:
  email_delivery:
    delivery_method: :smtp
    smtp_settings:
      enable_starttls_auto: true
      address: smtp.host.com
      port: 587
      domain: host.com
      authentication: :login
      user_name: myname
      password: mypassword
</pre>
  
  <p>
    You can check the e-Mail config in web interface with testmail function
  </p>
  
  <p>
    <a name="Autoupdate-Subversion-repository-view"></a>
  </p>
  
  <h2>
    Autoupdate Subversion repository view<a class="wiki-anchor" href="#Autoupdate-Subversion-repository-view"></a>
  </h2>
  
  <p>
    In the project archive settings over web interface its needed to enable the web service for project archives and generate a api key
  </p>
  
  <p>
    The following cronjob updates redmine to current subversion changesets every 15 minutes
  </p>
  
  <pre>sudo crontab -e
</pre>
  
  <p>
    Add the cronjob
  </p>
  
  <pre>*/15 *    * * * curl "http://yourhost/redmine/sys/fetch_changesets?key=APIKEY" &gt; /dev/null
</pre>
  
  <p>
    If your hosting does not offer cron job configuration then you can use external services like these:<br /> <a class="external" href="https://www.easycron.com">https://www.easycron.com</a>.
  </p>
  
  <p>
    <a href="https://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_25x_on_Ubuntu_1404_with_Apache2_Phusion_Passenger_MySQL_and_Subversion" target="_blank">Source</a>
  </p>
</div>