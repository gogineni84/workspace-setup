# JRuby and Ruby Setup

This Automation suite runs on JRuby. Please refer to [TSB Approved](https://nwproduction.service-now.com/tsb/standard_technology.do) technologies.
## Installing Java

Click to [Download](http://www.oracle.com/technetwork/java/javase/downloads) Java.
## Installing JRuby or Ruby

Click to [Download](http://jruby.org/files/downloads/index.html) JRuby/Ruby.

    * Click the latest version of JRuby/Ruby

    * Choose the correct file to download based on your system 

    * Save the file and run it once it is downloaded

    * Click yes to allow the program to make changes to your computer

    * Click Next

    * Select the installation location and click next.

    * Enable Configure Path for me and click Next

    * Click Finish

    * Verify installation on Windows Command Prompt `jruby -v` or `ruby -v` (henceforth jruby or ruby commands will be shorthanded by [j]ruby since it is the same for both languages)

    * Determine list of gem repos with `[j]ruby -S gem sources`

    * Remove rubygems.org from gem sources `[j]ruby -S gem sources -r https://rubygems.org`

    * Add nexus repo `[j]ruby -S gem sources -a http://repo.nwie.net/nexus/content/groups/rubygems/`

    * Install the following gems `[j]ruby -S gem install bundler ruby-debug-ide ruby-debug-base rubycritic` (you may need to open console as an admin)
## Installing RubyMine IDE

Click to **[Download](https://www.jetbrains.com/ruby/download/#section=windows)** RubyMine.

    * When prompted enter "license key" select license server. 

    * Input license server “http://rubyminelicense.nwie.net:8080/licenseServer”.

    * Click Discover Sever and Activate.   
## Installing Git

Click to **[Download](https://git-scm.com/download)** Git.
    
    * Click the download button.
    
    * Save file and run after download.
    
    * Select "Yes" to allow the program to make changes to your computer.
    
    * Select next to accept the software license.
    
    * Select the installation location and click next.
    
    * Select components needed and click next. (Usually the default is sufficient).
    
    * Click next to select Start Menu Folder.
    
    * Select option on how you want to use git syntax's.
    
    * Select Use the OpenSSL Library and click next.
    
    * Select Checkout Windows-style, commit Unix-Style line endings and click next.
    
    * Select Use MinTTY and click next.
    
    * Enable file system caching and Git Credential Manager and click Install.
    
    * Enable View Release Notes and click Finish
## Configuring JRuby on RubyMine IDE

    * Navigate to **File -> Settings -> Language & Frameworks -> Ruby SDK and Gems** 

    * Click the green plus symbol to add Jruby version installed

    * Navigate to  the jruby file -> bin -> jruby.exe and click OK

    * Click the radio button next to your new jruby file then click Apply and OK  
## Configuring GitHub on RubyMine IDE

Navigate to **File -> Settings -> Version Control -> GitHub** to set GitHub credentials.
       
1. **Auth Type:** Password

2. **Host:**  "https://github.nwie.net"

3. **Login:** nwie username

4. **Password:** nwie password

5. Click the **Test button** to verify access 
