## Workspace Setup
- [Java Setup](#JavaSetup)
- [Eclipse Setup](#EclipseSetup)
- [Eclipse Plugins](#EclipsePlugins)
- [Eclipse Configuration](#EclipseConfiguration)
- [Eclipse Websphere Deploy Issues](#EclipseWebsphereDeployIssues)

<a name="JavaSetup"></a>Java Setup
----------
1. Download and install [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). This will needed by Eclipse to properly run the SonarLint plugin.
2. Either set JAVA_HOME to this location of this JDK, or add ```-vm <javaw.exe location>``` to the eclipse.ini file. Do not quote the path if it has spaces, just ensure it's on a line by itself. It should be placed BEFORE the -vmargs line.

<a name="EclipseSetup"></a>Eclipse Setup
-------------
1. Download and install [Eclipse Oxygen](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2/eclipse-inst-win64.exe). 
2. Once installed, launch it and setup proxy settings under Window->Preferences->search "proxy" to point to your local Cntlm or Nationwide's http-proxy.

<a name="EclipsePlugins"></a>Eclipse Plugins
---------------
- Install the following plugins from the Eclipse Marketplace: [SonarLint](https://marketplace.eclipse.org/content/sonarlint) and [Spotbugs](https://marketplace.eclipse.org/content/spotbugs-eclipse-plugin) (formerly Findbugs) 
- Install [JD-Eclipse](http://jd.benow.ca/). You will need to download the release zip and add it as an archive repo in Eclipse->Help->Install new software->Add...->Archive...
- Install [Websphere](https://developer.ibm.com/wasdev/downloads/#asset/tools-IBM_Liberty_Developer_Tools_for_Eclipse_Oxygen). Like JD-Eclipse, you will need to download the zip and add it as an archive repo in Eclipse->Help->Install new software->Add...->Archive...

<a name="EclipseConfiguration"></a>Eclipse Configuration
---------------------
- Clone the [Sonar dev-tools repo](https://github.com/SonarSource/sonar-developer-toolset). Follow the instructions in the README for Eclipse Configure, specifically the Imports section. The Additional Configuration can be ignored at this time.
- Import the [compiler settings](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/workspace-setup/eclipseWarnings.epf): File->Import...->General->Preferences->select the preferences file from the download link.
- Setup the XML formatter: Window->Preferences->search "xml"->select XML->XML Files->Editor->follow the [screenshot](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/workspace-setup/eclipseXmlSettings.png)

<a name="EclipseWebsphereDeployIssues"></a>Eclipse Websphere Deploy Issues
-------------------------------
- After installing Websphere, copy the com.ibm.ws.orb_8.5.*.jar from the websphereInstall/runtimes directory to separate folder to be added to the Eclipse classpath. To do this, add the following to the eclipse.ini: ```-Djava.endorsed.dirs=<ibmOrbJardirectory>```