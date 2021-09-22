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


# Use your own JRE
{: #using_own_jre}

You can run your Liberty app on {{site.data.keyword.cloud}} with your own JRE. The liberty-for-java buildpack will provide support for the [runtimes supported by WebSphere Liberty](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_restrict.html#rwlp_restrict__rest13){: external}, but cannot guarantee full functionality of unsupported versions. You must complete the following to make your JRE available for your app.
* Host the JRE in a location that the buildpack can download it from.
* Host an `index.yml` file that provides the location of the JRE.
* Configure your app to use your JRE.

## Host the JRE and `index.yml`
{: #hosting_jre}

You must host the JRE file on a web server that the liberty-for-java buildpack can download from. You can host the file on {{site.data.keyword.cloud_notm}} with any of the available server facilities, or you can host it in a publicly available location. The server must be configured with an `index.yml` file that specifies details about the JRE file.

Complete the following steps to host the JRE and the `index.yml` file:
    1. Acquire the JRE, which must be the version for use on a UNIX 64-bit OS, and must be a `tar.gz` file.
    2. Host the JRE file in a location from which the liberty-for-java buildpack can download it.
    3. Provide an `index.yml` file at the hosting location. The `index.yml` file must include an entry that contains a version ID of the JRE followed by a colon and the complete JRE file location URL.
        * Define the JRE version in the `index.yml` file.

        ```text
        ---
        jre_version: https://hostingLocation/jreName.tar.gz
        ```
        {: codeblock}

        * Include the JRE version ID and the complete JRE file location.  For example:

        ```
        ---
        1.8.0_91: https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz
        ```
        {: codeblock}

## Configure the app
{: #configure_app}

You must set two environment variables on the Liberty app to configure the buildpack to use an alternative JRE. Set the `JBP_CONFIG_OPENJDK` to identify the location of the `index.yml` file  and set the `JVM` environment variable to `openjdk`. For more information on the format for version-value strings, see the Cloud Foundry documentation on [Version Syntax and Ordering and Wildcards](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/util-repositories.md){: external}.

The value for the `JBP_CONFIG_OPENJDK` variable is the `index.yml` file location and the JRE version to choose from the index.yml file.

    ```text
    '{repository_root: "https://locationToIndexYml", version: version-value}'
    ```
    {: codeblock}

Issue the `ibmcloud cf se myAPP` command to set the `JBP_CONFIG_OPENJDK` variable, for example:

    ```text
    ibmcloud cf se myApp JBP_CONFIG_OPENJDK '{repository_root: "https://myHostingApp.ng.bluemix.net", version: 1.8.+}'
    ```
    {: pre}

The *repository_root* URL does not include `index.yml` in the URL. The *repository_root* URL points to the directory level that contains the `index.yml` file, not the file itself.

To set the JVM environment variable, issue the following command:

    ```text
    ibmcloud cf se myApp JVM 'openjdk'
    ```
    {: pre}

**Note**: Restage your app after setting the environment variables for the changes to take effect.

## Confirm
{: #confirmation}

To confirm that Liberty is using the expected JRE, check the staging log. Look for a message that indicates the server downloaded the buildpack from the location indicated in the `index.yml` file. See the following snippet for an example of the log output when Liberty successfully uses the expected JRE.

    ```text
    -----> Downloading OpenJdk 1.8.0_91 from
     https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz (6.2s)
    ```
    {: screen}


