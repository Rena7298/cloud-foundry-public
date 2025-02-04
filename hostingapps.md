---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-22"

keywords: cloud foundry

subcollection: cloud-foundry-public



---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Hosting apps in {{site.data.keyword.cloud_notm}}
{: #hosting_apps}

With {{site.data.keyword.cloud}}, you can create apps, and host your existing apps. You can move your app to {{site.data.keyword.cloud_notm}} as long as it is cloud-ready. {{site.data.keyword.cloud_notm}} provides lots of ways for you to run your apps, for example, Cloud Foundry, {{site.data.keyword.containershort}}, and virtual machines.

## Making your apps cloud-ready
{: #cloud-readyapps}

If all of the following principles are observed in your app, the app is cloud-ready and can be migrated to {{site.data.keyword.cloud_notm}}. If a principle is violated in your app, you can usually modify your app to adhere to the principles.

## Migrating your apps
{: #ht_hostapp}

You can migrate your apps to {{site.data.keyword.cloud_notm}} incrementally, instead of shifting the app completely to the cloud environment. You can migrate a portion of your app first and connect to the existing data or system of records by using the Cloud Integration service.

In your cloud apps, you might need to access the backend data or services, for example, a system of record. In {{site.data.keyword.cloud_notm}}, you can use the Secure Gateway service to establish a secured tunnel between an {{site.data.keyword.cloud_notm}} organization and the enterprise backend network. The service enables the apps on {{site.data.keyword.cloud_notm}} to access the backend network’s data and services. For details, see [Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console](https://www.ibm.com/blogs/cloud-archive/2015/04/reaching-enterprise-backend-bluemix-secure-gateway/){: external}.

To deploy your app to {{site.data.keyword.cloud_notm}} as a Cloud Foundry app, select a runtime from the {{site.data.keyword.cloud_notm}} catalog. The runtime contains a starter Hello World app that you can replace with your own app. If you cannot find a starter that provides the runtime you want, you can bring a custom, Cloud Foundry-compatible buildpack to {{site.data.keyword.cloud_notm}} by using the `–b` option with the `ibmcloud cf push` command. For details, see [Using community buildpacks](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks).

You can use the following tools and services that {{site.data.keyword.cloud_notm}} provides:

| Tool | Method |
|------|--------|
| Cloud Foundry CLI | Manage your code on local client and use the CLI to push your app to {{site.data.keyword.cloud_notm}} manually. For more information, see the [`ibmcloud cf push` command](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html){: external}. |
| Eclipse | Manage your code in Eclipse and use the {{site.data.keyword.IBM}} Eclipse tools for {{site.data.keyword.cloud_notm}} to push your app. |
| Git integration | Manage your code on GitHub and integrate Git into {{site.data.keyword.cloud_notm}}. You can collaborate with other developers. Your app is deployed to {{site.data.keyword.cloud_notm}} automatically when you commit changes in the code. You do not need to push the app manually. |
| {{site.data.keyword.cloud_notm}} DevOps Delivery Pipeline | Manage your code on DevOps GitHub repository and deploy your app to {{site.data.keyword.cloud_notm}} by using the DevOps Delivery Pipeline. |
{: caption="Table 1. {{site.data.keyword.cloud_notm}} tools" caption-side="top"}

If the Cloud Foundry platform does not support your app requirements, you can use a container or VM where the runtime is set up, configured, and maintained with more customized options.

## Developing and deploying your apps using toolchains in Continuous Delivery
{: ht_cd}

Add a [toolchain to your app](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app) and then use the [Continuous Delivery toolchain UI](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using) to develop and deploy your app.

## Uploading your apps by using ibmcloud cf cli
{: #ht_cfcli}

You can manage your code on local client and use Cloud Foundry command line interface to upload your app to {{site.data.keyword.cloud_notm}} manually. If you change the code, you must push your app to {{site.data.keyword.cloud_notm}} again to run the updated code.

Take the following steps to migrate your app:

Install the Cloud Foundry command line interface. Ensure that you use the latest version of the `ibmcloud cf` command line interface.

1. Download the installation program for your operating system.
2. Follow the tool wizard to install the command line.
3. Use the following command to verify the version of the `ibmcloud cf` command line interface: `ibmcloud cf -v`

Optional: If you want to specify and save the deployment details before you push an app to {{site.data.keyword.cloud_notm}}, you can add the app manifest by taking the following steps:

1. Go to the working directory of your app and create a file entitled manifest.yml, which is the default name.
2. Specify deployment details in the manifest file. The following example shows a manifest file for a Java™ app.

    ```text
    applications:
    - disk_quota: 1024M
    host: myjavatest
    name: MyJavaTest
    path: webStarterApp.war
    domain: mybluemix.net
    instances: 1
    memory: 512M
    ```
    {: codeblock}

For more information about the supported options that you can use in this file, see [App manifest](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps#appmanifest).

### Push your app

You can upload your app by using the `ibmcloud cf push` command.

1. Connect and log in to {{site.data.keyword.cloud_notm}} by running the following command. Select your organization and space when prompted.

    ```text
    ibmcloud cf login -a https://api.ng.bluemix.net
    ```
    {: pre}

    Add the `-sso` flag if your organization uses Single Sign On.

2. From your app directory, enter the `ibmcloud cf push` command with the app name. The app name must be unique in the {{site.data.keyword.cloud_notm}} environment.

    ```text
    ibmcloud cf push appname
    ```
    {: pre}

3. Optional: If you use an external buildpack, you must use the -b option with the `ibmcloud cf push` command. For example:

    ```text
    ibmcloud cf push appname -b buildpack_URL
    ```
    {: pre}

    See [Using community buildpacks](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks) for details.

Optional: If you change your app, you must upload those changes by entering the `cf push command` again. The `ibmcloud cf` command line interface uses your previous options and your responses to the prompts to update any running instances of your app with the new bits of code.

#### Notes:

* When you use the `ibmcloud cf push` command, the `ibmcloud cf` command line interface copies all of the files and directories from your current directory to {{site.data.keyword.cloud_notm}}. Ensure that you have only the required files in your app directory.
* Ensure that your organization has enough memory for all instances of your app. To view the memory quota for your org, use `ibmcloud cf org <org_name>`.
* For more information about `ibmcloud cf push`, see [Pushing an app](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html){: external}.

## Migrating your data and using services
{: #ht_service}

After you upload your app to {{site.data.keyword.cloud_notm}}, select the service that your app is connected to from the {{site.data.keyword.cloud_notm}} catalog, create a service instance, bind the instance to your app, and then restart your app.

The VCAP_SERVICES environment variable of your app is a JSON object that contains information about how to interact with a service instance in {{site.data.keyword.cloud_notm}}. The information includes the service instance name, credentials, and the connection URL to the service instance.

To run your code in {{site.data.keyword.cloud_notm}}, you must add the code logic for parsing the VCAP_SERVICES variable to obtain information about service connection. Modify your app to get the dynamically assigned host and port of the service instance through the environment variables. The following example shows how to get the credentials of a `Postgre` SQL service instance in a Ruby app:

```ruby
services = JSON.parse(ENV['VCAP_SERVICES'], :symbolize_names => true)
        url = services.values.map do |srvs|
          srvs.map do |srv|
            if srv[:credentials][:uri] =~ /^postgres/
              srv[:credentials][:uri]
            else
              []
            end
          end
        end.flatten!.first
```
{: codeblock}

To ensure that your app can run in a local environment after you modify the app for {{site.data.keyword.cloud_notm}}, check for the presence of the VCAP_SERVICES environment variable, which is set for all {{site.data.keyword.cloud_notm}} Cloud Foundry apps.


