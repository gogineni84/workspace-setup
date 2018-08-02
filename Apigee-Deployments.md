## Apigee Deployments <!-- omit in toc -->
- [Github Project Standards](#github-project-standards)
- [Testing](#testing)
- [Deployment Standards](#deployment-standards)
    - [Adding a New Version to UCD](#adding-a-new-version-to-ucd)

### Github Project Standards
See [here](https://github.nwie.net/Nationwide/nw-apigee-cli/wiki) for details on setting up and using the CLI for generating Apigee proxy projects. Github projects should be created in the Nationwide organization repo (github.nwie.net/Nationwide) with the same name as the proxy in Apigee.

### Testing
The CLI scripts referenced above will create a skeleton project including npm modules for unit testing any JS files created as part of the proxy and the [Ruby restassured gem](https://github.nwie.net/Nationwide/restassured-gem) for testing simple Apigee proxy interactions. Tests should be written to cover all JS code paths, and all tests should be passing when checking in. 

One standard of note with restassured tests is that they use one or multiple Apigee environments to test, and the Jenkins builds often use the test environment (api-test.nwie.net or api-int-test.nwie.net) to test, so this effectively means that the proxy being built **must be deployed to dev and test** in order for tests to pass.

### Deployment Standards
Jenkins jobs should be created to build the proxy into Nexus; new jobs can have their Jenkins files modeled off of existing jobs, as there's a shared Jenkins library used to build these (if this isn't created as part of the CLI creation script). These jobs are created [here](http://dgsjenkins.aws.nwcmc.net/).

UCD scripts should be created to deploy the proxy to Apigee. The scripts and components should also be named the same as the Github project and Apigee proxy. A couple of things to note about these UCD scripts at the time of this writing:
1) These will only deploy the proxy. Any KVMs (Key Value Mappings) will not be deployed and must be manually added/setup. For stage and prod, this will require sending an email to the API Infrastructure email group. Prod can be done at anytime (not needed inside of an RFC window).

#### Adding a New Version to UCD
After building, retrieve the version from [Nexus](repo.nwie.net:8080/nexus) by searching for the proxy name (which should also be the name of the built artifact). Copy this version and paste it into the "Import new version" prompt for the proxy in UCD.