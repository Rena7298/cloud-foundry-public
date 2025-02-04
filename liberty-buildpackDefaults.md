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


# Liberty for Java buildpack defaults
{: #buildpack_defauts}

The Liberty buildpack is updated frequently in {{site.data.keyword.cloud}}. Each release might contain security fixes or feature enhancements.

The buildpack has default values for settings such as the Java version or Liberty feature set for WAR or EAR apps. Some of the default values might change between the buildpack release, which might adversely impact the app. To prevent the app from being affected by the change in buildpack defaults, take steps to configure your app to avoid relying on the buildpack defaults.

## Liberty versions
{: #liberty_versions}

The buildpack provides two versions of the Liberty runtime:
1. A long-term stable release
    * It is the default Liberty runtime.
    * It does not provide any [beta features](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_beta_features).
    * Typically updated on a quarterly basis.

2. The monthly release
    * It must be explicitly enabled by setting the **JBP_CONFIG_LIBERTY** environment variable with the **"version: +"** value and the **IBM_LIBERTY_MONTHLY** environment variable with **true**.
    * It provides [monthly features](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime).
    * Typically updated every 4 weeks.

## Liberty features
{: #default_liberty_features}

When you deploy WAR or EAR files, the buildpack provides a configuration for the app with a default set of Liberty features. Although rare, that default set of Liberty features might change between the buildpack releases. The change in the default feature set might adversely affect the app. There are options to ensure that the app is not affected by the change in the feature defaults.

* Set the JBP_CONFIG_LIBERTY environment variable to explicitly specify a list of enabled features for the app. For more information, see [Stand-alone Apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps).
* Deploy your app as a [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or a [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server). Provide a custom `server.xml` file that specifies the exact set of features that are needed by your app.

Apps that are deployed as a server directory or a packaged server are unaffected by the change in the Liberty features default.

## Java version
{: #java_version}

The buildpack provides a default JRE for the app. The major or minor version of the JRE might change between the buildpack releases. The minor version of the JRE might be updated frequently while the major version is rarely updated. The change in the major version of the JRE might adversely affect the app.

To ensure that the app is not affected by the major version change, set the environment variable with the appropriate JRE version as described in [Customizing the JRE](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre). For best results, adopt Java 8 for your apps.


