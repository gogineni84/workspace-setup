## This page will serve as a running collection of all the questions and problems associates may encounter when using Websphere.

### Q: When my Websphere instance is starting, my console outputs a stack trace for a "non-deferrable alarm" thread being returned. What does this impact?
A: These warnings are quite common but do not affect the functionality of the Websphere instance, so they can be ignored for testing code. Eliminating the warning from a housekeeping perspective is another matter.

### Q: How can I confirm my Java version is correct for my given Websphere profile?
A: From the bin folder in your Websphere installation directory you can run the command managesdk -listEnabledProfileAll. This will list all of your server profiles and the SDK they are using. If you want to see a list of available SDKs you can run managesdk -listAvailable, and if you want to specify a certain SDK from that list for a profile you can run managesdk -enableProfile -profileName <profile name> -sdkname <sdkname> -enableServers. In general for our Websphere applications it would be expect for websphere to be using the IBM websphere java 7 version.

### Q: How can I retrieve an up-to-date SSL certificate?
A: Go the admin console and navigate to security -> SSL certificate and key management on the left. Then on the right side of the page go to Key stores and certificates, then click NodeDefaultTrustStore. Then click Signer certificates, and click the retrieve from port button. Provide the host name and the secure port number of 443, then provide an alias of you choosing and click retrieve signer information. Click apply and save.