# New projects with NodeJS and Webpack
- Creating new app based on NodeJS
- Create folder structure:
    - [root_project]
        - webpack.config.js
        - src/index.html
        - src/app/index.js
        
- Install modules (webpack now 4.16.3)
    - npm init --yes    // Create a new file "package.json" into root project folder
    - npm i webpack webpack-dev-server html-webpack-plugin webpack-cli -D // Install Pack moduler, Development Local Server, Cli Webpack and Html to Production. All like DEV dependences.
- Define input/ouput routing paths
    - On "webpack.config.js"
       const htmlWebpack = require('html-webpack-plugin');
       const path = require('path');
       module.exports = {
            entry: './src/app/index.js',
            output: {
                path: path.join(__dirname, '/dist'),
                filename: 'bundle.js'
            }
        },
        devServer: {
            port: 8050
        },
        plugins: [
            new htmlWebpack({
                template: './src/index.html'
            })
        ]
        
    - On "package.json"
        "scripts": {
            "build": "webpack --mode production",
            "dev": "webpack-dev-server --mode development"
        },
    
- Testing output files
    - npm run build     // Create new files: dist/bundle.js and index.html within dist folder.
    - npm run dev       // Run local server for test our changes.


# Local Environment (Windows)
- noSQL Database
    - MongoDB 3.6

- WebApps
    - Typescript 2.7.1
    - Angular CLI: 1.6.8
    - Node 8.9.4 LTS, NPM 5.6.0
    
- Mobile
    - Android Studio 3

- DevOps
    - Vagrant 2.0.1
    - VirtualBox 5.2.6
    - Docker CE 17.12

- Web-Tools:
- BrowerSync
    $ npm install -g browser-sync
    $ browser-sync --version
      2.24.4
    $ npm init (for new projects)
    # npm install --save-dev browser-sync

- ReactJS
- npx create-react-app crud-app
- cd crud-app
- yarn start // Starts the development server (recommended)
- yarn build // Bundles the app into static files for production.
- yarn test  // Starts the test runner.
- yarn eject // Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can’t go back!

- Laravel:
   $ cd D:\JSiesquen\Box\Homestead
   $ vagrant box add laravel/homestead
   
   $ git clone https://github.com/laravel/homestead.git .
   $ git checkout v7.4.2
   $ bash init.sh (init.bat)
   
   $ ssh-keygen -t rsa -C "my.email@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Neksix/.ssh/id_rsa):
Created directory '/c/Users/Neksix/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Neksix/.ssh/id_rsa.
Your public key has been saved in /c/Users/Neksix/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:d/e96vcpv0YyrgOe72r1CHxA "my.email@gmail.com"
The key's randomart image is:
+---[RSA 2048]----+
|          ..     |
|          o. E   |
|         o..  .  |
|        . .. .   |
|     o..++==+=B*=|
+----[SHA256]-----+
    
   $ Edit Homestead.yaml file
   $ Edit host file (Windows) or hostname (Linux)
   $ vagrant up

# NPM
- Update: sudo npm install -g npm
- On Windows NodeJS install (node -v => v8.11.3; npm -v => 5.6.0).

# FrontEnd Commands
- npm install -g @angular/cli        # install
- npm uninstall -g @angular/cli      # upgrade (1)
- npm cache clean                    # upgrade (2) 
- npm install -g @angular/cli@latest # upgrade (3) if npm version is > 5 then use `npm cache verify` to avoid errors (or to avoid using --force)

# SASS https://sass-lang.com:
- Linux Install: sudo npm install -g sass (Nice! => )
- Windows Install: sudo npm install -g sass (Nice! => 1.9.2 compiled with dart2js 2.0.0-dev.66.0)

- Using choco fail (like Administrator) aren't use:
  - PowerShell Execute: Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
  - Check: choco /?
  - PowerShell Execute: choco install dart-sdk (instal stable release 1.24.3)
  - PowerShell Execute: choco upgrade dart-sdk --pre (install 2.0.0.68-dev-0)
  - PowerShell Execute: choco install sass (install 1.9.2)
  
  - Usage:
      - sass .\sass\styles.sass:css/style.css
      - scss .\scss\styles2.sass:css/style2.css
      - sass --watch .\sass\styles.sass:css/style.css
      - sass --watch app/sass:public/stylesheets
  
# TypeScript
- tsc -init
- tsc -w

# MongoDB (27017 default port)
- Database > Collections (Tables) > Documents (Rows) key-value pair.
- Document: key (string), value (string, number, array or list, date, boolean, object).
- use [dbname] / db / show dbs / db.dropDatabase() 
- db.[collection].insert({"key":"value"}) / db.createCollection("[collection]") / show collections / db.[collection].drop()

# Sublime Text 3
- Install Package Controls: https://packagecontrol.io/installation
- See Preferences > Package Control. After Install [E] => HTML5, EMMET, AutoFilename, SFTP, Bootstrap 3 Snippets, Bootstrap 4 Snippets, jQuery, BracketHighlighter.


# Linux
- Find distribution version
    - uname -a
    - lsb_release -a
    - cat /etc/*release
    - sudo bash -c 'echo > /var/log/apache2/error.log'
- Useful commands
    - sudo bash -c 'echo > /var/log/apache2/error-site.log'    # Cleaning log files
    - tar -cvzf docs.tar.gz /home/neksix/Documents/            # Compress the tar file with gzip pass the -z option
    - tar -cvzf docs.tar.bz2 /home/vivek/Documents/            # Compress the tar file with bzip2 pass the -j option
    - tar -tvf docs.tar                                        # List the contents of a files
    - tar -tvzf docs.tar.gz
    - tar -tvjf docs.tar.bz2
    - tar -xvf docs.tar                                        # Extract the contents of a tar file
    - tar -xvzf docs.tar.gz
    - tar -xvjf docs.tar.bz2                                   # t: List contents; x: Extract; z: Compress gzip; j: Compress bzip2
    
- Using SysV Init scripts directly:
    - /etc/init.d/php-fpm restart    # typical
    - /etc/init.d/php5-fpm restart   # debian-style
    - /etc/init.d/php7.0-fpm restart # debian-style PHP 7

- Using service wrapper script
    - service --status-all-
    - service php-fpm restart    # typical
    - service php5-fpm restart   # debian-style
    - service php7.0-fpm restart # debian-style PHP 7

- Using Upstart (e.g. ubuntu):
    - restart php7.0-fpm         # typical (ubuntu is debian-based) PHP 7
    - restart php5-fpm           # typical (ubuntu is debian-based)
    - restart php-fpm            # uncommon

- Using systemd (newer servers):
    - systemctl restart php-fpm.service    # typical
    - systemctl restart php5-fpm.service   # uncommon
    - systemctl restart php7.0-fpm.service # uncommon PHP 7

- sudo apt-get update
- sudo apt-get upgrade -y | sudo apt-get dist-upgrade -y

# Nginx
- /etc/php/7.0/fpm/pool.d/www.conf   # Time Out limits
- sudo systemctl status nginx |service nginx status
- sudo systemctl reload nginx | service nginx reloadg

# Composer
- composer create-project slim/slim-skeleton [my-app-name]
- composer install (Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.)
- composer show -i (Show information about packages)

# Docker (https://docs.docker.com/get-started/)
- Linux: https://get.docker.com/
    - sudo curl -fsSL get.docker.com -o get-docker.sh
    - 
- Windows (Docker CE): https://store.docker.com/editions/community/docker-ce-desktop-windows
    - 

# Git
- Config
    - git config --global user.email "email@gmail.com"
    - git config --global user.name "John Doe"
- Change login authentication (.git/config)
    - git config -e
- Clone repo remote
    - git clone http://user@server.com/package.git new_folder
- Download objects and refs from another repository
    - git fetch
- State Latest of repository
    - git remote -v
- Switched to a another branch
    - git checkout develop

- Show the working tree status
    - git status
    - git diff                    //check diff between files prepared for commit
    - git diff --cached           //check diff between files no prepared
    - git diff --staged           //check diff between files no prepared
- Revert (reset) changes to a file if they haven’t been committed yet:
    - git checkout -- <file>
- Revert (reset) a single file to a specific revision (with Previous Commit)
    - git checkout <commit_hash> -- <file>
- Commit and Push
    - git add .                      // Add file contents to the index
    - git commit -a -m "message"     // Record changes to the repository; -a for ommit "git add" command
    - git push origin develop        // Update remote refs along with associated objects
    - git reset HEAD~                // Undo a commit and redo
    - git reset <file>               // Remove "Add" action previously
- Recovery new changes (Fetch from and integrate with another repository or a local branch) 
    - git pull
- Show commit logs
    - git log
- Show all commits
    - git log --all --oneline
- Target to hash
    - git checkou <hash>   // Previuos State
    - git checkou master   // Current State
- Initializate a existent repository on existing local code
    - echo "# GithubClient" >> README.md
    - git init
    - git add README.md
    - git commit -m "first commit"
    - git remote add origin https://github.com/jsiesquen/GithubClient.git
    - git push -u origin master
    
# MySQL
- vim /etc/mysql/debian.cnf
- mysql -u debian-sys-maint -p[xxxxxxxx]
- SET PASSWORD FOR 'user-name-here'@'hostname' = PASSWORD('new-password');      // <5.7.5
- ALTER USER 'user'@'hostname' IDENTIFIED BY 'newPass';   // >5.7.6

# Vagrant
- https://app.vagrantup.com/boxes/search?utf8=✓&sort=downloads&provider=virtualbox
- Initialization
    - vagrant up --provider=virtualbox --provision

# Magento QA Code
    - https://github.com/magento/marketplace-tools
    - https://github.com/magento/marketplace-eqp

# Magento IDE integration
    - https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm

# Magento 2 Cli
- Know virtual path admin panel.
    - vagrant@magento2:/vagrant/source$ ./bin/magento info:adminuri

- php bin/magento cache:status

        Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
                           eav: 1
         customer_notification: 0
                     full_page: 0
            config_integration: 1
        config_integration_api: 1
                     translate: 1
             config_webservice: 1
     
- vagrant@magento2:/vagrant/source$ php bin/magento cache:clean

        Cleaned cache types:
        config
        layout
        block_html
        collections
        reflection
        db_ddl
        eav
        customer_notification
        full_page
        config_integration
        config_integration_api
        translate
        config_webservice

- vagrant@magento2:/vagrant/source$ php bin/magento cache:flush

        Flushed cache types:
        config
        layout
        block_html
        collections
        reflection
        db_ddl
        eav
        customer_notification
        full_page
        config_integration
        config_integration_api
        translate
        config_webservice

- vagrant@magento2:/vagrant/source$ php bin/magento setup:static-content:deploy

        Requested languages: en_US
        Requested areas: frontend, adminhtml
        Requested themes: Magento/blank, Magento/luma, Magento/backend
        === frontend -> Magento/blank -> en_US ===
        === frontend -> Magento/luma -> en_US ===
        === adminhtml -> Magento/backend -> en_US ===

        Successful: 2013 files; errors: 0
        ---
        Successful: 2138 files; errors: 0
        ---
        Successful: 2063 files; errors: 0
        ---
        === Minify templates ===
        Successful: 869 files modified
        ---
        New version of deployed files: 1513037090

- vagrant@magento2:/vagrant/source$ php bin/magento indexer:status

        Design Config Grid:                                Ready
        Customer Grid:                                     Ready
        Category Products:                                 Ready
        Product Categories:                                Ready
        Product Price:                                     Ready
        Product EAV:                                       Ready
        Catalog Search:                                    Ready
        Stock:                                             Ready
        Catalog Rule Product:                              Reindex required
        Catalog Product Rule:                              Ready

- php bin/magento deploy:mode:show
- php bin/magento deploy:mode:set developer|production
- php bin/magento indexer:reindex catalogrule_rule
- php bin/magento module:status                                            # Module Status
- php bin/magento module:enable J2t_Payplug --clear-static-content         # Enable
- php bin/magento setup:upgrade                                            # Register
- php bin/magento setup:di:compile                                         # Recompile
- php bin/magento module:status
- rm -rf var/di var/cache var/generation/ var/page_cache/                  # remove temps


# AWS
- https://www.linkedin.com/pulse/listado-de-todos-los-servicios-amazon-web-services-daniel-pe%C3%B1a-silva/?published=t


# CMS
# Concrete5
- (https://github.com/concrete5/composer)
- mkdir concrete5.test
- composer create-project -n concrete5/composer concrete5.test
- cd concrete5.test/
- sudo ./vendor/bin/concrete5 c5:install -i

The current user is root: this is discouraged for this CLI command.
Do you want to proceed anyway [Y/N]? Y
Checking required preconditions:
- PHP 5.5.9... passed (you are running PHP version 7.2.4-1+ubuntu18.04.1+deb.sury.org+1).
- MySQL PDO Extension Enabled... passed.
- JSON Extension Enabled... passed.
- DOM Extension Enabled... passed.
- ASP Style Tags Disabled... passed.
- Fileinfo Extension Enabled... passed.
- Image Manipulation Available... passed.
- XML Support... passed.
- Writable Files and Configuration Directories... passed.
- Internationalization Support... passed.
- PHP Comments Preserved... passed.
- Tokenizer Extension Enabled... passed.
- Memory limit 64.00 MB.... passed (current memory limit: 512.00 MB).
Checking optional preconditions:
- Remote File Importing... passed.
- Zip Support... passed.

Location of database server? [127.0.0.1]:
Database name?: themeconcrete5
Database username?: root
Database password?:
The system time zone, compatible with the database one? [UTC]:
Name of the site? [concrete5 Site]: Neksix Site
Canonical URL?: http://themeconcrete5.test/
Alternative canonical URL?: http://themeconcrete5.test/
Starting point to use? [elemental_blank]:
  [0] elemental_blank
  [1] elemental_full
 > 1
Email of the admin user of the install? [admin@example.com]: jsiesquen@adperu.com
Password of the admin user of the install?:
Additional user username?: jsiesquen
Additional user email? [demo@example.com]: jsiesquen@neksix.com
Additional user password?:
The default concrete5 interface language (eg en_US)? [en_US]: es_ES
The default site locale (eg en_US)? [es_ES]:
Use configuration file for installation? [none]:

Checking required configuration preconditions:
- Canonical URLs... passed.
- Database is empty... passed.
- MySQL InnoDB engine... passed.
- Starting Point... passed.
Checking optional configuration preconditions:
- Database time zone... passed.
- Table case... passed (Table names are stored in the specified lettercase (lookups are performed in a case-sensitive way).).

+---------------------------+-----------------------------+
| Question                  | Value                       |
+---------------------------+-----------------------------+
| env                       |                             |
| db-server                 | 127.0.0.1                   |
| db-username               | root                        |
| db-password               | HIDDEN                      |
| db-database               | themeconcrete5              |
| timezone                  | UTC                         |
| site                      | Neksix Site                 |
| canonical-url             | http://themeconcrete5.test/ |
| canonical-url-alternative | http://themeconcrete5.test/ |
| starting-point            | elemental_full              |
| admin-email               | jsiesquen@adperu.com        |
| admin-password            | HIDDEN                      |
| demo-username             | jsiesquen                   |
| demo-password             | HIDDEN                      |
| demo-email                | jsiesquen@neksix.com        |
| language                  | es_ES                       |
| site-locale               | es_ES                       |
| config                    | none                        |
+---------------------------+-----------------------------+
Would you like to install with these settings? [Y]es / [N]o / [E]dit: Y

5%: Starting installation and creating directories.
10%: Creating database tables.
12%: Creating site.
15%: Adding admin user.
20%: Installing permissions & workflow.
23%: Installing Custom Data Objects.
26%: Creating home page.
30%: Installing attributes.
35%: Adding block types.
39%: Adding gathering data sources.
40%: Page type basic setup.
45%: Adding themes.
47%: Installing automated jobs.
50%: Installing dashboard.
55%: Installing login and registration pages.
57%: Adding image editor functionality.
60%: Configuring site.
65%: Importing files.
70%: Adding pages and content.
85%: Adding desktops.
90%: Setting site permissions.
95%: Finishing.
Adding demo user... done.
Installation Complete!
