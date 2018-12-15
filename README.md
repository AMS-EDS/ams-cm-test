# CloudManager Test Project

No-op test project for CloudManager integration. Contains a single Sling Model, unit tests, and "Hello World" component only.

## How to use

1. Check out this repo: `git clone https://git.corp.adobe.com/jessup/ams-cm-test.git`
1. Add Cloud Manager as a new remote: `https://adobecloudmanager-acsorg@dev.azure.com/adobecloudmanager-<tenant>/<tenant>/_git/<tenant>` (you can get this URL from the VSTS console)
1. Push the project to Cloud Manager: `git push -u cloudmanager --all`
1. Deploy via Cloud Manager (see CM docs/wiki for how to setup a pipeline and deploy it)

## Background

This project is designed to allow testing of CM pipelines with minimal risk of impacting any other activities in a given environment. It deploys a single package with a single bundle, which will happily co-exist alongside any code without impacting functionality or triggering a cascade of OSGi service restarts.

You can use this to perform end-to-end testing of CM in a live customer environment without having to worry about breaking or disrupting anything else. This project should get a clean bill of health from CM for unit testing and code analysis, allowing CxEs to focus on environment health and any other non-code requirements to get CM working.

## How to build locally

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project and deploy into AEM with  

    mvn clean install -PautoInstallPackage
    
Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallPackagePublish
    
Or alternatively

    mvn clean install -PautoInstallPackage -Daem.port=4503

Or to deploy only the bundle to the author, run

    mvn clean install -PautoInstallBundle

## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html
