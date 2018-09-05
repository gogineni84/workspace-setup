# JRuby and Ruby Setup

EDS Automation suites run on Ruby and JRuby. Please refer to [TSB Approved](https://nwproduction.service-now.com/tsb/standard_technology.do) technologies.

## Installing Ruby

* Install the latest version of [Ruby](https://rubyinstaller.org/)
* In a command prompt, validate your installation

```console
$ ruby -v
```

* Configure you `gem` commands

```console
$ gem sources -a http://repo.nwie.net/nexus/content/groups/rubygems/
$ gem sources -r https://rubygems.org
```

* Open terminal as an admin and run `gem install bundler ruby-debug-ide ruby-debug-base rubycritic rubocop`

## Installing JRuby

* Install the latest [Java](http://www.oracle.com/technetwork/java/javase/downloads) Java.
* Install the latest [JRuby](http://jruby.org/files/downloads/index.html) JRuby.
* In a command prompt, validate your installation

```console
$ jruby -v
```

* Configure you `gem` commands

```console
$ jgem sources -a http://repo.nwie.net/nexus/content/groups/rubygems/
$ jgem sources -r https://rubygems.org
```

* Open terminal as an admin and run `jgem install bundler ruby-debug-ide ruby-debug-base rubycritic rubocop`

## Installing RubyMine IDE

Install **[RubyMine](https://www.jetbrains.com/ruby/download/#section=windows)**.

* When prompted enter "license key" select license server. 
* Input license server “http://jetbrains-license-server.nwie.net/r”.
* Click Discover Sever and Activate.

## Installing Git

Click to **[Download](https://git-scm.com/download)** Git.

## Configuring Ruby on RubyMine IDE

* Navigate to **File -> Settings -> Language & Frameworks -> Ruby SDK and Gems**
* Click the green plus symbol to add ruby version and engine (c-based or java based) installed
* Navigate to  the (j)ruby file -> bin -> (j)ruby.exe and click OK
* Click the radio button next to your new (j)ruby file then click Apply and OK

## Configuring GitHub on RubyMine IDE

Navigate to **File -> Settings -> Version Control -> GitHub** to set GitHub credentials.

1. **Auth Type:** Password
2. **Host:**  "https://github.nwie.net"
3. **Login:** nwie username
4. **Password:** nwie password
5. Click the **Test button** to verify access
6. Click Apply and OK

## Configure Rubocop

Navigate to **File -> Settings -> Editor -> Inspections**

1. Click the *Ruby* dropdown
![Inspection Settings](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/images/rubocop-configuration.png)
2. Uncheck all Inspections execept for *RuboCop*
![](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/images/rubocop-configuration-2.png)
3. Click Apply and OK

## Optional Eclipse Keymapping

![Optional Keymapping for very particular and grumpy developers](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/images/rubymine-keymap.png)