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


# Memory limits and the Liberty buildpack
{: #memory_limits}

A memory limit must be specified when you deploy an app with the Liberty buildpack.

## Memory limits and the Liberty buildpack
{: #memory_limits_and_liberty}


When you deploy an app with the Liberty buildpack, you are prompted for a "Memory Limit". The Liberty for Java buildpack sets a default heap memory size ratio to prevent your process from exceeding the memory limit. You can also specify the heap memory size or ratio by defining the `JVM_ARGS` or `JBP_CONFIG_IBMJDK` environmental variables. See [Heap memory options](#heap_memory_options) to learn more.

To determine what Memory Limit to specify, it is important to understand that you are not specifying the size of the Java app heap. You are specifying the amount of memory available for the Diego container to use. This amount includes the memory that is used by the following components:

* by the warden container.
* to map kernel extensions and system libraries into the process.
* for the JVM executables, JVM working heap, JIT space, and compressed references.
* for classes (app server and app), thread stacks, and direct I/O buffers.
* by the Java app heap.

More information on JVM memory usage can be found at the developerWorks article [Thanks for the memory](http://www.ibm.com/developerworks/library/j-nativememory-linux/){: external}

When you deploy an app, the memory usage of the entire process is monitored. If memory usage exceeds the memory limit that you specified when the app was deployed, the kernel stops the process. This action happens without warning and might be manifested in several ways.

If the Memory Limit is exceeded during app deployment, you receive a message that a failure occurred and you might see any the following.

* You might see that the app is flapping.
* You might see that the app attempted to start multiple times, always unsuccessfully.
* You might receive a message that indicates the app deployment failed.

If the Memory Limit is exceeded while the app is in service, the process stops and Cloud Foundry attempts to restart the app. The app might restart, but it is unavailable for some amount of time.

## Heap memory options
{: #heap_memory_options}

You can customize the maximum amount of heap memory your app is allocated in various ways including by using the `JVM_ARGS` environment variable, changing the `jvm.options` file, or setting the `JBP_CONFIG_IBMJDK` environment variable which controls the `heap_size_ratio`. If you do not specify any settings, the buildpack uses the default settings.

### Heap memory defaults
{: .#heap_memory_defaults}
To prevent errors that result from exceeding memory limits, the Liberty for Java buildpack sets a default heap size ratio depending on the memory limit that you specify when you deploy your app.

* Apps with memory limits of less than 512M have a heap size ratio of 50%
* Apps that have memory limits greater than or equal to 512M have a heap size ratio of 75%

When you specify the heap memory using environment variables, you override the default heap size ratios.

### Specifying Heap Memory
{: #specifying_heap_memory}

You can set the heap memory size by using environment variables or by changing the `jvm.options` file. When you use either the `JVM_ARGS` or `JBP_CONFIG_IBMJDK` environment variables, any changes will take effect when pushing your app to {{site.data.keyword.cloud_notm}}. By changing the `jvm.options` file, the effect to the heap size configuration can also be tested locally.

* Use the `JVM_ARGS` environment variable and the `-Xmx` argument. For example to set the maximum heap size to 512 M use the following command, then restage your app.

    ```text
    ibmcloud cf set-env myapp JVM_ARGS -Xmx512m
    ```
    {: codeblock}

* Specify the heap size ratio using the JBP_CONFIG_IBMJDK environment variable.  The heap_size_ratio is a floating point value which specifies how much of memory limit to allocate to the heap.  For example, to allocate half of the available memory to the heap (50% or 0.50), issue the following command and restage your app.

    ```text
    ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "heap_size_ratio: 0.50"
    ```
    {: codeblock}

* Specify the `-Xmx` argument in the `jvm.options` file if your app is a [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or a [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server). For more information about  using the `jvm.options` file with the Liberty runtime, see [Setting generic JVM](https://www.ibm.com/support/pages/node/476495){: external}.  


