# **NPM**
- Update: sudo npm install -g npm
    - npm list -g --depth=0 (Work)
       ```sh
        +-- madge@4.0.0
        +-- npm@6.14.11
        +-- terser@5.5.1
        `-- uglifycss@0.0.29
       ```
- Information:
    - node -v   // v8.11.3, v12.16.1, v14.15.1
    - npm -v    // 5.6.0, 6.13.4, 6.14.3, 6.14.8, 6.14.11

# **Compress & Minify**
## CSS
```sh
npm install uglifycss -g
uglifycss _src/css/global.css > Code/Files/global.css
```
## Javascript
```sh
npm install terser -g           # mangler/compressor toolkit for ES6+
terser _src/js/global.js -c -m -o Code/Files/global.js
npm install uglifyjs -g         # No support ES6+
uglifyjs _src/js/global.js -c -o _src/files/global.js
npm install uglify-js -g        # Support ES5 only
uglifyjs -c -m -- _src/js/global.js
```

# **TypeScript**
- tsc -init
- tsc -w

# **Webpack**
```sh
$ node -v       # 8.12
$ npm install webpack webpack-cli -g    # Global install, release 4.20.2 and cli 3.1.2
```

## Webpack-starter-kit@1.0.0
```sh
$ npm init                            # Set project information & create package.json (without dependences)
$ npm install webpack webpack-cli -D  # Local installation with development dependencies (use npm install for get dependences) open package.json and set "scripts": { "build": "webpack" create src folder and create index.js test: npm run build, open package.json and set: "build": "webpack --mode production", "dev": "webpack --mode development"
$ npm run build
$ npm run dev
```

## New projects with NodeJS and Webpack
- Creating new app based on NodeJS
- Create folder structure:
    - [root_project]
        - webpack.config.js
        - src/index.html
        - src/app/index.js
        
- Install modules (webpack now 4.16.3)
    ```sh
    $ npm init --yes    # Create a new file "package.json" into root project folder
    $ npm i webpack webpack-dev-server html-webpack-plugin webpack-cli -D # Install Pack moduler, development Local Server, Cli Webpack and html module with (-D) DEV dependencies only.
    ```
- Define input/ouput routing paths
    - On "webpack.config.js"
        ```sh
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
        ```
    - On "package.json"
        ```sh
        "scripts": {
            "build": "webpack --mode production",
            "dev": "webpack-dev-server --mode development"
        },
        ```

- Testing output files
    - npm run build     // Create new files: dist/bundle.js and index.html within dist folder.
    - npm run dev       // Run local server for test our changes.

## New Web project with Node + Webpack + Bootstrap
- Create folder structure:
    - [root_project]
        - src/index.html
        - src/index.js
        - src/main.css
        
- Install modules (webpack 4.16.5, webpack-cli 3.1.0)
    ```sh
    $ npm init --yes         # Create a new file "package.json" within project folder
    $ npm i webpack --save-dev
    $ npm i webpack-cli --save-dev
    # Now open up package.json and add a build script:
    #    "scripts": {
    #      ...
    #      "dev": "webpack --mode development",
    #      "build": "webpack --mode production"
    #    }
    $ npm run build        # Create a minified bundle file within dist/main.js
    $ npm run dev          # Create a bundle file within dist/main.js
    $ npm i babel-core babel-loader babel-preset-env --save-dev        # Transpiling JS ES6 with Babel
    $ npm i html-webpack-plugin html-loader --save-dev     # Additional components for processing HTML
    $ npm i mini-css-extract-plugin css-loader --save-dev  # Extract CSS
    $ npm i webpack-dev-server --save-dev   # Webpack dev server
    $ npm run start:dev
    $ npm install bootstrap                      # 4.1.3
    $ npm install --save jquery popper.js        # Bootstrap Dependences
    $ npm install style-loader css-loader postcss-loader precss autoprefixer sass-loader --save # Loaders
    ```

# **GIT**
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
- Change Remote URL from SSH a HTTPS
    - git remote set-url origin https://github.com/name/repo.git
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
- Commit and Push (If repository aren't exist yet)
    ```sh
    <<Enter local folder>>
    git init
    git status                      
    git add -A                # Add file contents to index
    git commit -m "message"   # Record changes on repository
    git remove add origin git@github.com:jsiesquen/repository-name.git
    git push -u origin master
    ```
- Commit and Push
    ```sh
    git add .                   # Add file content to index
    git commit -a -m "message"  # Save changes on repository
                                # -a for ommit "git add" command
    git push origin develop     # Update remote refs along with associated objects
    git reset HEAD~             # Undo a commit and redo
    git reset <file>            # Remove "Add" action previously
    ```
- Recovery new changes (Fetch from and integrate with another repository or a local branch) 
    - git pull
    - git pull origin Desarrollo
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
- More:
    - git commit --amend -m "New commit message"        // change the commit message
    - git add file6 && git commit --amend --no-edit     // add file to MY previous commit itself
    - git config user.email "your email id"             // configure the email id for current project after of commit
    - git commit --amend --author "Author Name <Email>"  // Change the author of your previous commit as well (local repo)

# **Local Environment (Windows)**
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
    ```sh
    $ npm install -g browser-sync
    $ browser-sync --version
      2.24.4
    $ npm init (for new projects)
    $ npm install --save-dev browser-sync
    ```
- ReactJS
    ```sh
    - npx -v        # 6.14.3
    - npx create-react-app crud-app
    - cd crud-app
    - yarn start    # Starts the development server (recommended)
    - yarn build    # Bundles the app into static files for production.
    - yarn test     # Starts the test runner.
    - yarn eject    # Removes this tool and copies build dependencies, configuration files and scripts into the app directory.
    ```
- [Wordpress](http://vccw.cc)
    ```sh
    $ cd \JSiesquen\Box\vccw-3.21.1\
    $ vagrant up
    $ vagrant reload --provision
    $ vagrant ssh
    $ sudo nano /etc/php/7.0/apache2/php.ini
    $ sudo systemctl status apache2.service
    $ sudo systemctl restart apache2.service
    ```
- Laravel:
    - Installation:
        ```sh
        $ cd \JSiesquen\Box\Homestead
        $ vagrant box add laravel/homestead
            ==> box: Loading metadata for box 'laravel/homestead'
                box: URL: https://vagrantcloud.com/laravel/homestead
            ==> box: Adding box 'laravel/homestead' (v8.2.1) for provider: virtualbox
                box: Downloading: https://vagrantcloud.com/laravel/boxes/homestead/versions/8.2.1/providers/virtualbox.box
                box: Download redirected to host: vagrantcloud-files-production.s3.amazonaws.com
                box: Progress: 100% (Rate: 106k/s, Estimated time remaining: --:--:--)
            ==> box: Successfully added box 'laravel/homestead' (v8.2.1) for 'virtualbox'!
        
        $ git clone https://github.com/laravel/homestead.git .
        $ git checkout release      // v7.4.2
        $ init.bat                  // For Windows
        $ bash init.sh              // For Linux (Ok)
            * Homestead initialized!
        $ ssh-keygen -t rsa -C "my.email@gmail.com"
            ```sh
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
        ```
    - Edit Homestead.yaml file
    - Edit host file (Windows) or hostname (Linux)
    - Started
        ```sh
        $ vagrant up
        ```

# **Angular**
 ```sh
$ npm install -g @angular/cli        # install
$ npm uninstall -g @angular/cli      # upgrade (1)
$ npm cache clean                    # upgrade (2) 
$ npm install -g @angular/cli@latest # upgrade (3) if npm version is > 5 then use `npm cache verify` to avoid errors (or to avoid using --force)
```

# **SASS** 
- [SASS](https://sass-lang.com)
- Linux Install: sudo npm install -g sass (Nice! => )
- Windows Install: sudo npm install -g sass (Nice! => 1.9.2 compiled with dart2js 2.0.0-dev.66.0)

- Using choco fail (like Administrator) aren't use:
  - PowerShell Execute: Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
  - Check: choco /?
  - PowerShell Execute: choco install dart-sdk (instal stable release 1.24.3)
  - PowerShell Execute: choco upgrade dart-sdk --pre (install 2.0.0.68-dev-0)
  - PowerShell Execute: choco install sass (install 1.9.2)
  
  - Usage:
      - sass --watch style.scss:style.min.css --style compressed
      - sass .\sass\styles.sass:css/style.css
      - scss .\scss\styles2.sass:css/style2.css
      - sass --watch .\sass\styles.sass:css/style.css
      - sass --watch app/sass:public/stylesheets

# **MongoDB** 
- 27017 default port
- Database > Collections (Tables) > Documents (Rows) key-value pair.
- Document: key (string), value (string, number, array or list, date, boolean, object).
- use [dbname] / db / show dbs / db.dropDatabase() 
- db.[collection].insert({"key":"value"}) / db.createCollection("[collection]") / show collections / db.[collection].drop()

# **IDE**
## Sublime Text 3
- [Install Package Controls](https://packagecontrol.io/installation) 
- See Preferences > Package Control. After Install [E] => HTML5, EMMET, AutoFilename, SFTP, Bootstrap 3 Snippets, Bootstrap 4 Snippets, jQuery, BracketHighlighter.

# **Linux**
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

# **Nginx**
- /etc/php/7.0/fpm/pool.d/www.conf   # Time Out limits
- sudo systemctl status nginx |service nginx status
- sudo systemctl reload nginx | service nginx reloadg

# **Composer**
- composer create-project slim/slim-skeleton [my-app-name]
- composer install (Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.)
- composer show -i (Show information about packages)

# **Docker 2021**
- Started:
    # Clone the repository by running Git in a container.
    - docker run --name repo alpine/git clone https://github.com/docker/getting-started.git
    - docker cp repo:/git/getting-started/ .
    # A Docker image is a private file system just for your container.
    # It provides all the files and code your container needs.
    - cd getting-started
    - docker build -t docker101tutorial .
    # Start a container based on the image you built in the previous step.
    # Running a container launches your application with private resources, securely isolated from the rest of your machine.
    - docker run -d -p 80:80 --name docker-tutorial docker101tutorial
    # Save and share your image on Docker Hub to enable other users to easily download and run the image on any destination machine.
    - docker tag docker101tutorial jsiesquen/docker101tutorial
    - docker push jsiesquen/docker101tutorial
# **Docker**
- [Docker Started](https://docs.docker.com/get-started/)
- [Docker Hub](https://hub.docker.com)
- [Docker Linux](https://get.docker.com)
    - sudo curl -fsSL get.docker.com -o get-docker.sh
    
    Quick:
    - yum -y install docker     # Installiing Docker
    - systemctl enable docker   # Enable Docker Service
    - systemctl start docker    # Start Docker Service
    - docker run hello-world    # Testing
    
    [From Docker.com](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-repository) 
    - sudo apt-get update
    - sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
    - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    - sudo apt-key fingerprint 0EBFCD88
    - sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   - sudo apt-get update
   - sudo apt-get install docker-ce
   - apt-cache madison docker-ce
   - sudo docker run hello-world
    
- Windows: 
    - [Without Hyper-V - Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)
    - [With Hyper-V - Docker CE](https://store.docker.com/editions/community/docker-ce-desktop-windows)

- On Runtime:
    - docker run -ti --rm --name test ubuntu bash
    - docker run -ti --rm --name test ubuntu                        # -ti: interactive terminal; --rm: remove after stop container; 
                                                                    # ubuntu: docker image;
    - docker run -ti --rm --name test-nginx -p 8181:80 nginx
    - docker run -it -p 139:139 -p 445:445 --name samba -d dperson/samba
    - docker exec -it samba /bin/bash

- Creating Custom image
   - Create Dockerfile included all commands.
   - Execute:
    - docker build -t custom-nginx .
    - docker run -d --name nginx -p 8080:80 custom-nginx
    - curl localhost:8080

 - Key Commands
    - docker info
    - docker ps -a
    - docker images
    - docker logs [name or container_id]
    - docker pause|stop|rm|rmi [name or container_id]
    
  - Important Articles:
    - https://getintodevops.com/blog/keeping-the-whale-happy-how-to-clean-up-after-docker

# **MySQL**
- vim /etc/mysql/debian.cnf
- mysql -u debian-sys-maint -p[xxxxxxxx]
- SET PASSWORD FOR 'user-name-here'@'hostname' = PASSWORD('new-password');      // <5.7.5
- ALTER USER 'user'@'hostname' IDENTIFIED BY 'newPass';   // >5.7.6

# **Vagrant**
- https://app.vagrantup.com/boxes/search?utf8=✓&sort=downloads&provider=virtualbox
- New Box (Example):
    - vagrant init bento/ubuntu-16.04
    - vagrant box update
    - vagrant up
- Initialization
    - vagrant up --provider=virtualbox --provision

# **AWS**
- [Listado de todos los servicios AWS](https://www.linkedin.com/pulse/listado-de-todos-los-servicios-amazon-web-services-daniel-pe%C3%B1a-silva/?published=t)
- [AWS Training](https://www.aws.training/Dashboard)

## AWS CLI 2 (AWS Command Line Interface)
$ where aws
    ```
    C:\Program Files\Python37\Scripts\aws
    C:\Program Files\Python37\Scripts\aws.cmd
    C:\Program Files\Amazon\AWSCLIV2\aws.exe
    ```
- aws --version     (Output: aws-cli/2.0.0 Python/3.7.5 Windows/7 botocore/2.0.0dev4;
                        C:\Users\<user>\.aws\config|credentials)
- aws configure --profile <profile>
- aws configure get region --profile <profile>
- aws ec2 describe-instances --profile <profile>
- export AWS_PROFILE=<profile>
- git clone codecommit://<profile>@template-backend-nodejs

# **Python**
- python --version  (Output: Python 3.7.4)

## PIP Package Management
- Download packages from PyPI (Python Package Index - Repository Central)
- [Install](https://pip.pypa.io/en/stable/installing/)
    - Download: curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    - python get-pip.py
        ```sh
        Collecting pip
        Downloading pip-20.0.2-py2.py3-none-any.whl (1.4 MB)
            |████████████████████████████████| 1.4 MB 1.3 MB/s
        Collecting wheel
        Downloading wheel-0.34.2-py2.py3-none-any.whl (26 kB)
        Installing collected packages: pip, wheel
        Attempting uninstall: pip
            Found existing installation: pip 19.0.3
            Uninstalling pip-19.0.3:
            Successfully uninstalled pip-19.0.3
        Successfully installed pip-20.0.2 wheel-0.34.2
        ```
    - python -m pip install -U pip  (Upgrade)
- Main Commands:
    - pip install <package-name>
    - pip install <package-name>==1.0.0
    - pip install <package-name> --upgrade
    - pip install <package-name> --upgrade --force-reinstall (remove)
    - pip install <package-name> --upgrade --force-reinstall (reinstall)
    - pip show <package-name>
    - pip search "query"
    - pip list
    - pip list --outdated
    - pip --version (output: pip 20.0.2 from c:\program files\python37\lib\site-packages\pip (python 3.7))
    - pip3 --version (output: pip 20.0.2 from c:\program files\python37\lib\site-packages\pip (python 3.7))
- Install dependences: Active Directory on CodeCommit
    - pip install awscli
    - pip install -U git+https://github.com/jatorres5/awsprocesscreds.git
    - pip install git-remote-codecommit

# **Ecommerce Solutions**

## Magento
    - https://github.com/magento/marketplace-tools
    - https://github.com/magento/marketplace-eqp

### Magento IDE integration
    - https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm

### Magento 2 Cli
- Know virtual path admin panel.
    - vagrant@magento2:/vagrant/source$ ./bin/magento info:adminuri

- php bin/magento cache:status
    ```sh
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
    ```
- vagrant@magento2:/vagrant/source$ php bin/magento cache:clean
    ```sh
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
    ```
- vagrant@magento2:/vagrant/source$ php bin/magento cache:flush
    ```sh
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
    ```
- vagrant@magento2:/vagrant/source$ php bin/magento setup:static-content:deploy
    ```sh
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
    ```
- vagrant@magento2:/vagrant/source$ php bin/magento indexer:status
    ```sh
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
    ```
- php bin/magento deploy:mode:show
- php bin/magento deploy:mode:set developer|production
- php bin/magento indexer:reindex catalogrule_rule
- php bin/magento module:status         // Module Status
- php bin/magento module:enable J2t_Payplug --clear-static-content  //Enable
- php bin/magento setup:upgrade         // Register
- php bin/magento setup:di:compile      // Recompile
- php bin/magento module:status
- rm -rf var/di var/cache var/generation/ var/page_cache/   // Remove temps

# **CMS Solutions**
## Gatsby
- Default Starter: [Getting started](https://www.gatsbyjs.com/docs/quick-start/)
    - npm init gatsby
        ```sh
        What would you like to call your site?
        √ · My Gatsby 101
        What would you like to name the folder where your site will be created?
        √ 101/ gatsby-101
        √ Will you be using a CMS?
        · No (or I'll add it later)
        √ Would you like to install a styling system?
        · styled-components
        ? Would you like to install additional features with other plugins?
        (Multiple choice) Use arrow keys to move, enter to select, and choose "Done" to confirm your choices
        (*) Add the Google Analytics tracking script
        (*) Add responsive images
        ( ) Add page meta tags with React Helmet
        (*) Add an automatic sitemap
        ( ) Enable offline functionality
        (*) Generate a manifest file
        ( ) Add Markdown support (without MDX)
        ( ) Add Markdown and MDX support
        ─────
        > Done

        Great! A few of the selections you made need to be configured. Please fill in the options for each plugin now:

        √ Configure the gatsby-plugin-google-analytics plugin.
        See https://www.gatsbyjs.com/plugins/gatsby-plugin-google-analytics/ for help.

        Thanks! Here's what we'll now do:
            Create a new Gatsby site in the folder gatsby-101
            Get you set up to use styled-components for styling your site
            Install gatsby-plugin-google-analytics, gatsby-plugin-sharp, gatsby-plugin-sitemap, gatsby-plugin-manifest

        √ Shall we do this? (Y/n) · Yes
        √ Cloning site template
        > Installing Gatsby...
        ```
    - cd gatsby-101
    - npm run develop

- From Repository [Create a Gatsby site](https://www.gatsbyjs.com/docs/tutorial/part-zero/#create-a-gatsby-site/part-zero/):
    - npm init gatsby
        ```sh
        $ npm install -g gatsby-cli
        $ gatsby --help
        $ gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world
        $ cd hello-world
        $ gatsby develop
        ```

## Wordpress
- [Vagrant Setup](https://www.howtoforge.com/setup-a-local-wordpress-development-environment-with-vagrant/)
- vagrant -v        // 2.2.5
- vagrant plugin install vagrant-hostsupdater  // On OS's hosts file
    ```sh
    Installing the 'vagrant-hostsupdater' plugin. This can take a few minutes...
    Fetching: vagrant-hostsupdater-1.1.1.160.gem (100%)
    Installed the plugin 'vagrant-hostsupdater (1.1.1.160)'!
    ```
- git clone -b master git://github.com/Varying-Vagrant-Vagrants/VVV.git ~/vvv
- cd vvv            // C:\Users\EB9263\~\vvv
- vagrant up        // Varying Vagrant Vagrants v3.1.1 C:/Users/EBXXXX/~/vvv
- Add new site on vvv-custom.yml
- vagrant reload --provision

## Drupal 8 
- which drush
    * /home/vagrant/.composer/vendor/bin/drush
- brew install drush    // if aren't install
- drush dl drupal-8 --select
    ```sh
    Choose one of the available releases for drupal:
    [0]  :  Cancel
    [1]  :  8.7.x-dev    -  2018-Aug-06  -  Development
    [2]  :  8.6.0-beta2  -  2018-Aug-03  -  Supported
    [3]  :  8.5.6        -  2018-Aug-01  -  Security, Recommended
    
    Project drupal (8.5.6) downloaded to /home/vagrant/code/drupal8.test/public/drupal-8.5.6. [success]
    Project drupal contains: [success]
    - 2 profiles: standard, demo_umami
    - 16 themes: classy, stark, seven, bartik, twig, stable, demo_umami_content, umami, testing_multilingual, testing_missing_dependencies, testing_multilingual_with_english, drupal_system_listing_compatible_test, testing,
    testing_config_overrides, testing_config_import, minimal
    - 75 modules: field, file, block, system, tracker, contextual, serialization, language, inline_form_errors, hal, layout_builder, big_pipe, responsive_image, content_translation, ban, content_moderation, help, dblog, views_ui,
    block_place, telephone, migrate_drupal, breakpoint, datetime_range, views, statistics, path, history, node, migrate, menu_link_content, datetime, menu_ui, rdf, color, book, filter, contact, ckeditor, editor, image,
    field_layout, workflows, comment, locale, taxonomy, search, settings_tray, entity_reference, user, shortcut, rest, basic_auth, field_ui, syslog, options, aggregator, simpletest, text, quickedit, page_cache, dynamic_page_cache,
    toolbar, automated_cron, config_translation, media, forum, migrate_drupal_ui, update, tour, block_content, config, link, layout_discovery, action
    ```

## Concrete5
- [Repository Concrete](https://github.com/concrete5/composer)
- mkdir concrete5.test
- composer create-project -n concrete5/composer concrete5.test
- cd concrete5.test/
- sudo ./vendor/bin/concrete5 c5:install -i
```sh
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
    Would you like to install 
    with these settings? [Y]es / [N]o / [E]dit: Y

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
```
