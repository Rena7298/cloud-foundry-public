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


# Use the beta features
{: #using_beta_features}

**Important**:  Starting with Liberty for Java buildpack v3.28, the beta runtime is no longer included.  

The Liberty beta features provide early access to new functionality and programming models that might be included in a future Liberty release. Most of the beta features can also be used in apps deployed to {{site.data.keyword.cloud}}.

**Important**: The beta features are for development and test purposes only and cannot be used in production. For the complete terms of use, see the [beta license agreement](http://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/beta/lafiles/en.html){: external}.

| Features |
| ------ |
| `jdbc-4.3` |
| `logstashCollector-1.1` |
| `validator-1.0` |
{: caption="Table 1. Liberty Beta features available in Liberty for Java in {{site.data.keyword.cloud_notm}}" caption-side="top"}

To use the Liberty beta features in {{site.data.keyword.cloud_notm}}, you will need to do the following:

1. [Deploy a server directory or a packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing) with one or more beta features enabled in the `server.xml` file as in the example that follows:

    ```text
    <server>
        <featureManager>
            <feature>jdbc-4.3</feature>
        </featureManager>
    </server>
    ```
    {: .codeblock}

2.  Set the `IBM_LIBERTY_BETA` environment variable to `true`. This variable directs the Liberty buildpack to install and enable the beta features for your app.  For example:
   
    * Using the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli):
    
        ```text
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_BETA true
        ```
        {: .pre}

    * Or, using the `manifest.yml` file:
    
        ```yaml
          env:
              IBM_LIBERTY_BETA: "true"
        ```
        {: .codeblock}

3. Set the `JBP_CONFIG_LIBERTY` environment variable to `"version: +"`. This variable enables the [Liberty monthly runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_defauts#liberty_versions), which supports beta features. For example:
    
    * Using the {{site.data.keyword.cloud_notm}} CLI tool:
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ```
        {: .pre}

    * Or, using the `manifest.yml` file:
    
        ```yaml
          env:
              JBP_CONFIG_LIBERTY: "version: +"
        ```
        {: .codeblock}

If you are enabling the beta features on an existing app, don't forget to re-stage your app after you set the environment variables.


