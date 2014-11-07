!! WIP = work in progress

# Mac OS X web development environment

When I first started to work and play in the awesome web development world it was really hard for me to set up a nice and well working local dev envoirment. 
As a result, I took a clean install of my OS as an oppurtunity to write a good and clear (I hope!) beginner's guide that will help you to set a web development environment on Mac OS X.

- [Terminal](#terminal)
- [Homebrew](#homebrew)
- [Git](#git)
- [Sublime Text](#sublime-text)
- [Vim](#vim)
- [Node.js](#node-js)
- [Npm](#npm)
- [Ruby](#ruby)
- [Apache](#apache)
- [PHP](#php)
- [Virtual hosts](#virtual-hosts)

## [](terminal)Terminal
We will spend a lot of time inside Terminal.app. So it's really advised to set up a nice and [solorized](http://ethanschoonover.com/solarized) command-line.
You will find Terminal.app under `~/Applications/Utilities`.
Running this commands will install `aliases`(a series of shorten commands), a `.bash_profile` and a `.bash_prompt` that will provide you a colorful and helpful terminal.
```
$ cd ~
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.aliases
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.bash_profile
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.bash_prompt
```
I strongly suggest you to discover and play with all the shortcuts that you can now use. Have a look at the `.aliases` file [here](https://github.com/aminalhazwani/dotfiles/blob/master/.aliases).

We don't want to press SHIFT every time we have to type an uppercase letter. This simple hack will autocomplete the path for yous(while navigating with Terminal.app you can autocomplete your path pressing TAB).
```
$ cd ~
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.inputrc
```


## [](#homebrew)Homebrew
Homebrew is a nice package manager that makes easier to install and update applications in a blink. In order to install it we first need to install command line tools for Xcode.app.

### Install Command Line Tools fox Xcode
If you are running at least Mac OS X 10.9 Mavericks you can install Command Line Tools directly from the Terminal.app. Simply type
```
$ xcode-select --install
```

### Install Homebrew
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

In order to make sure everything works type
```
brew doctor
```
you should get: `Your system is ready to brew.`.

## [](#git)Git
Git is an awesome tool for developers. To learn more about it and about its super powers I suggest you to look throw this [awesome resources](http://bradfrost.com/blog/post/gitgithub-resources/) collected by the awesome [Brad Frost](http://bradfrost.com/).

To install Git run
```
brew install git
```

As for Terminal.app we can also add some colors to git commands and basic git outputs
```
$ cd ~
$ curl -O https://github.com/aminalhazwani/dotfiles/blob/master/.gitconfig
```

And finally define your git user(you must have a GitHub or Heruko account)
```
$ git config --global user.name "Your Name Here"
$ git config --global user.email "your_email@youremail.com"
```
and generate a ssh key following this guide: [https://help.github.com/articles/generating-ssh-keys/](https://help.github.com/articles/generating-ssh-keys/).


## [](#sublime-text)Sublime Text
Sublime Text 2 is my favorite text editor. It's simply awesome. I will here describe how to set some basic users preferences and how to install some important tools.

First download it from the [official site](http://www.sublimetext.com/2).

### Install Package Control
Package Control is for Sublime what Homebrew is for your OS. With it you can install an enormus amount of packages that will bring your text editor to the Mars and back. Launch Sublime and open the console with the shortcut `ctrl + backtick` and paste inside the appropriate Python code for your version of Sublime Text (in our case Sublime Text 2).
```
import urllib2,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```

### Install packages
To install a package you have to launch Package Control. To launch a command in Sublime Text you use the shortcut `shift+cmd+P`. Then type `package control` and press Return. You will see a small progress bar in the bottom side of your window. Sublime is loading all the packages. Then simply type the name of your package of interest and press enter to install it.

My favorite packages are:
- Theme - Spacegrey
- MarkdownEditing
- AdvancedNewFile

### Sublime Text User preferences
One of the many factor that make Sublime Text my favorite text editor is user preferences. You can choose and tweak every single aspect. To use my preferences simply run this commands below. The user preferences file is simple plain text. Easy to read. If before installing you want to read it go and check it [here](https://github.com/aminalhazwani/dotfiles/blob/master/init/Preferences.sublime-settings)
```
$ cd ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/User/
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/init/Preferences.sublime-settings
```

### Launch Sublime Text from the command-line
Since we will spend a lot of time in the Terminal.app it could be very handy to launch Sublime Text with a simple and short command. This will allow you to launch it only typing `subl`
```
$ ln -s /Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```


## [](#vim)Vim
It can happen – from time to time – that you must edit a file on-the-code inside Terminal.app. And here is where [Vim](http://www.vim.org/) is helpuful. I prefer it over [nano](http://www.nano-editor.org/dist/v2.2/nano.html). Both are two ways of coding and writing inside the command-line. To install it type this
```
$ mkdir -p ~/.vim/autoload ~/.vim/bundle && \
    curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```
add some basic preferences
```
$ cd ~
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.vimrc
```
and finally let's add some colors as for the rest of our system
```
$ cd ~
$ mkdir .vim
$ cd .vim
$ curl -O https://raw.githubusercontent.com/aminalhazwani/dotfiles/master/.vim/colors/solarized.vim
```


## [](#node-js)Node.js
Install [Node.js](http://nodejs.org/) with Homebrew
```
$ brew install node
```

This command installs also the [npm](https://www.npmjs.org/) package manages. Node modules are installed locally in the `node_modules` folder of each project by default.

Some packages I couldn't live without are for example [Gulp.js](http://gulpjs.com/) and [SASS](http://sass-lang.com/). But let's keep this guide on simply setting everything necessary as web developer before diving in new and awesome tools.

## [](#npm)NPM
To install a package the formula is
```
$ npm install <package> 
```
To learn about all the possibilities offered by npm I suggest [this](http://howtonode.org/introduction-to-npm) guide. I hope I can manage to write soon a guide about getting started with Gulp.js and SASS. Subscribe to my [RSS](http://aminalhazwani.com/feed.xml) to stay tuned! 

## [](#ruby)Ruby

## [](#Apache)Apache
```
$ sudo apachectl start
```

### Sites folder
```
$ cd ~
$ mkdir Sites
```

### Add username.conf
```
$ cd /etc/apache2/users
$ sudo nano yourusername.conf
```
paste this
```
<Directory "/Users/yourusername/Sites/">
    AllowOverride All
    Options Indexes MultiViews FollowSymLinks
    Require all granted
</Directory>
```
and set the right permission
```
$ sudo chmod 644 yourusername.conf
```

### Set Document Root
```
$ sudo nano /etc/apache2/httpd.conf
```
uncomment this lines
```
LoadModule authz_core_module libexec/apache2/mod_authz_core.so
LoadModule authz_host_module libexec/apache2/mod_authz_host.so
LoadModule userdir_module libexec/apache2/mod_userdir.so
Include /private/etc/apache2/extra/httpd-userdir.conf
```

```
$ sudo nano /etc/apache2/extra/httpd-userdir.conf
```
uncomment this line
```
Include /private/etc/apache2/users/*.conf
```
and restart apache
```
$ sudo apachectl restart
```

```
$ sudo nano /etc/apache2/httpd.conf
```
Set 
```
AllowOverride All
```
and uncomment this line
```
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
```


## [](#php)PHP
```
$ sudo nano /etc/apache2/httpd.conf
```
and uncomment this line
```
LoadModule php5_module libexec/apache2/libphp5.so
```
restart apache
```
$ sudo apachectl restart
```
create a new file `phpinfo.php`, place it in ~/Sites and add this content
```
<?php phpinfo(); ?>
```
Open it in your browser and chech if everything is fine

### Show PHP and HTML errors
```
$ sudo nano /etc/php.ini
```
and set 
```
display_errors = On
html_errors = On
```
and uncomment
```
zend_extension=”/usr/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so”
```
and restart apache
```
$ sudo apachectl restart
```

### Set Permission on ~/Sites folder
```
$ sudo chown -R _www ~/Sites/
```


## [](#virtual-hosts)Virtual Hosts
```
$ sudo nano /etc/apache2/httpd.conf
```
and uncomment this lines
```
Include /private/etc/apache2/extra/httpd-vhosts.conf
LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
```

### Edit vhosts.conf
```
sudo nano /etc/apache2/extra/httpd-vhosts.conf
```
and add this below the dummy content
```
<VirtualHost *:80>
ServerAdmin youremail@yourprovider.domain
DocumentRoot "/User/yourusername/Sites/yourwebsitefolder"
ServerName yourwebsitename.domain
ErrorLog "/private/var/log/apache2/yourwebsitename.domain-error_log"
CustomLog "/private/var/log/apache2/yourwebsitename.domain-access_log" common
</VirtualHost>
```

### Map IP Address to localhost
```
$ sudo nano /etc/hosts
```
add both the domain and the alias
```
127.0.0.1 yourwebsitename.domain www.yourwebsitename.domain
```
and restart apache
```
$ sudo apachectl restart
```
