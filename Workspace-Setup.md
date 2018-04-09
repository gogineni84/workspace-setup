## Workspace Setup

### Eclipse Setup
- Download and install [Eclipse Oxygen](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2/eclipse-inst-win64.exe). 
- Once installed, launch it and setup proxy settings under Window->Preferences->search "proxy" to point to your local Cntlm or Nationwide's http-proxy.

### Eclipse Plugins
- Install the following plugins from the Eclipse Marketplace: [SonarLint](https://marketplace.eclipse.org/content/sonarlint), [Websphere](https://marketplace.eclipse.org/content/ibm-websphere-application-server-v85x-developer-tools), and [Spotbugs](https://marketplace.eclipse.org/content/spotbugs-eclipse-plugin) (formerly Findbugs) 
- Install [JD-Eclipse](http://jd.benow.ca/). You will need to download the release zip and add it as an archive repo in Eclipse->Help->Install new software->Add...->Archive...

### Eclipse Configuration
- Clone the [Sonar dev-tools repo](https://github.com/SonarSource/sonar-developer-toolset). Follow the instructions in the README for Eclipse Configure, specifically the Imports section. The Additional Configuration can be ignored at this time.
- Import the [compiler settings](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/workspace-setup/eclipseWarnings.epf): File->Import...->General->Preferences->select the preferences file from the download link.
- Setup the XML formatter: Window->Preferences->search "xml"->select XML->XML Files->Editor->follow the [screenshot](https://github.nwie.net/Nationwide/EDS-Apps/blob/master/workspace-setup/eclipseXmlSettings.png)