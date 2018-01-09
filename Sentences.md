# Sublime Text 3
- Install Package Controls: https://packagecontrol.io/installation
- See Preferences > Package Control. After Install [E] => HTML5, EMMET, AutoFilename, SFTP, Bootstrap 3 Snippets, Bootstrap 4 Snippets, jQuery, BracketHighlighter.


# Linux
- Useful commands
    - sudo bash -c 'echo > /var/log/apache2/error-site.log'    # Cleaning log files
    
- Using SysV Init scripts directly:
    - /etc/init.d/php-fpm restart    # typical
    - /etc/init.d/php5-fpm restart   # debian-style
    - /etc/init.d/php7.0-fpm restart # debian-style PHP 7

- Using service wrapper script
    - service --status-all
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

# Composer
- composer create-project slim/slim-skeleton [my-app-name]
- composer install (Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.)
- composer show -i (Show information about packages)


# Git
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
    - git reset HEAD~                //Undo a commit and redo
- Recovery new changes (Fetch from and integrate with another repository or a local branch) 
    - git pull
- Show commit logs
    - git log


# Vagrant
- https://app.vagrantup.com/boxes/search?utf8=✓&sort=downloads&provider=virtualbox
- Initialization
    - vagrant up --provider=virtualbox --provision


# Linux
- Find distribution version
    - uname -a
    - lsb_release -a
    - cat /etc/*release
    - sudo bash -c 'echo > /var/log/apache2/error.log'


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
