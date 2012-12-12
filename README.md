guvnor_automated_deployment_example
===================================

Sample **Drools** project that shows how to build a full **Guvnor** repository from command line and deploy it automatically to a Guvnor Instance.

The project uses [guvnor-buld-importer](https://github.com/droolsjbpm/guvnor/tree/5.5.0.Final/guvnor-bulk-importer), a tool part of the official Drools project: https://github.com/droolsjbpm

The interesting part of the whole project is in [rules/pom.xml](https://github.com/paoloantinori/guvnor_automated_deployment_example/blob/master/rules/pom.xml).

In this maven project file you will find 2 defined profiles:

- build_technical_rules
- deploy_brms

**build_technical_rules** it's used to build an .xml file that is a full JCR repository that you can import manually in Guvnor web interface.
**deploy_brms** it's just to deploy the file generated in the previous step. This uses **Guvnor REST api** but it's performed automatically by a **Groovy script** embdedded in the pom.xml file.

Note:
- A full debug log it's included in the repo to have an idea of what happens during the build process.
- It seems that the produced export has a slight validation bug. In my example, the order of **package** and **import** are in the wrong order. This causes a validation error but doesn't prevent to build the pacakge.