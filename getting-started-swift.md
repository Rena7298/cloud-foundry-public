---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-23"

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




# Getting started with Swift
{: #getting-started-swift}

Note the [Swift buildpack is deprecated](http://ibm.biz/cf-buildpack-swift-deprecation){: external}.
{: important}

Congratulations, you deployed a Hello World sample app on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-swift){: external} and explore on your own.


By following this tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.cloud}}, and integrate an {{site.data.keyword.cloud_notm}} database service in your app.
{: shortdesc}

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.cloud_notm}} CLI! The {{site.data.keyword.cloud_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.cloud_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.cloud_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-swift}

* [Git](https://git-scm.com/downloads){: external}
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli)
* [Swift compiler](https://swift.org/download/){: external} for your platform.

## Step 1: Clone the sample app
{: #clone-swift}

First, clone the repository and change to the directory to where the sample app is located.

```text
git clone https://github.com/IBM-Cloud/get-started-swift
```
{: pre}

```text
cd get-started-swift
```
{: pre}

Peruse the files in the `get-started-swift` directory to familiarize yourself with the contents.

## Step 2: Run the app locally
{: #run_locally-swift}

Once you have installed the Swift compiler and cloned this Git repository, you can now compile and run the app.

1. Go to the root directory of this repository on your system and issue the following command:

    ```text
    swift build
    ```
    {: pre}

    This command might take a few minutes to run.

2. When the app is successfully compiled, you can run the executable that was generated by the Swift compiler:

    ```text
    swift run
    ```
    {: pre}

    or
   
    ```text
    .build/debug/get-started-swift
    ```
    {: pre}

    You should see an output similar to the following:

    ```text
    Server is listening on port: 8080
    ```
    {: screen}

3. View your app at the following URL: `http://localhost:8080`

## Step 3: Prepare the app for deployment
{: #prepare-swift}

To deploy to {{site.data.keyword.Bluemix_short}}, it can be helpful to set up a `manifest.yml` file. The `manifest.yml` file includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample `manifest.yml` file in the `get-started-swift` directory.

Open the `manifest.yml` file, and change the `name` from `GetStartedSwift` to your app name, `app_name`.

```yaml
apps:
 - name: Get-Started-Swift
   random-route: true
   memory: 256M
   command: get-started-swift
   buildpack: swift_buildpack
```
{: codeblock}

In this `manifest.yml` file, `random-route: true` generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace `random-route: true` with `host: <myChosenHostName>`, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-swift}

You can use the {{site.data.keyword.cloud}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.cloud_notm}} account, and select an API endpoint.

    ```text
    ibmcloud login
    ```
    {: pre}

    If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more information.

    ```text
    ibmcloud login --sso
    ```
    {: pre}

2. Target a Cloud Foundry org and space:
  
    ```text	  
    ibmcloud target --cf
    ```
    {: pre}

    If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
    {: tip}

3. From within the `get-started-swift` directory, push your app to {{site.data.keyword.cloud_notm}}

    ```text
    ibmcloud cf push
    ```
    {: pre}

    This can take a minute. If there is an error in the deployment process you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your apps status and see the URL.

```text
ibmcloud cf apps
```
{: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external} to view your app.

## Step 5: Add a database
{: #add_database-swift}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this app and set up the app so that it can run locally and on {{site.data.keyword.cloud_notm}}.

1. In your browser, log in to {{site.data.keyword.cloud_notm}} and go to the Dashboard. Select **Create resource**.

2. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.

3. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.

4. In the navigation, go to **Connections**, then click **Create connection**. Select your app, and click **Connect**.

5. Using the default values, click **Connect & restage app** to connect the database to your app. Click **Restage** when prompted.

    {{site.data.keyword.cloud_notm}} will restart your app and provide the database credentials to your app using the `VCAP_SERVICES` environment variable. This environment variable is available to the app only when it is running on {{site.data.keyword.cloud_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of specifying a database password in your source code, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database
{: #use_database-swift}

We're now going to update your local code to point to this database. Create a `JSON` file that will store the credentials for the services the app will use. This file will get used ONLY when the app is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the VCAP_SERVICES environment variable.

Create a file called `my-cloudant-credentials.json` in the `config` directory with the following content (as reference, see `config/my-cloudant-credentials.json.example`):

```json
{
  "password": "<password>",
  "url": "<url>",
  "username": "<username>"
}
```
{: codeblock}

Update the `mappings.json` file in the `config` directory by replacing the `cloudant` placeholder with the **name** of your DB instance:

```json
{
  "MyCloudantDB": {
    "searchPatterns": [
      "cloudfoundry:cloudant",
      "env:kube-cloudant-credentials",
      "file:config/my-cloudant-credentials.json"
    ]
  }
}
```
{: codeblock}

This sample app uses the `CloudEnvironment` package to interact with {{site.data.keyword.cloud_notm}} to parse environment variables. [Learn more...](https://github.com/Kitura/CloudEnvironment){: external}

The `cloudant` placeholder in the `cloudfoundry:cloudant` configuration makes it easier to bind a user-provided Cloudant service to your app. With the `cloudfoundry:cloudant` configuration, you can create a Cloudant service that includes the string, `cloudant` somewhere in the service name and bind it to your app, without editing the `config.json` file. If you modify this configuration and later want to use a user-provided Cloudant service, you either need to edit the configuration to `cloudfoundry:cloudant` or define `cloudfoundry:` with the name of your user-provided service.
{: tip}

Find your app in the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

Copy and paste just the credentials to the corresponding fields in your local `config.json` file.

Build and run your app locally.

```text
swift build  
```
{: pre}

```text
.build/debug/kitura-helloworld
```
{: pre}

View your app at: `http://localhost:8080`. Any names you enter into the app will now get added to the database.

This sample app uses the `Kitura-CouchDB` package to interact with Cloudant. [Learn more...](https://github.com/Kitura/Kitura-CouchDB){: external}

Make any changes you want and re-deploy to {{site.data.keyword.cloud_notm}}!

```text
ibmcloud cf app push
```
{: pre}

View your app at the URL listed in the output of the push command, for example, `myUrl.mybluemix.net`.

Remember, if you don't need your app live, stop it so you don't incur any unexpected charges.
{: tip}

## Next steps
{: #nextsteps-swift}

* [Samples](https://ibm-cloud.github.io){: external}
* [Architecture Center](https://www.ibm.com/cloud/architecture/architectures){: external}


