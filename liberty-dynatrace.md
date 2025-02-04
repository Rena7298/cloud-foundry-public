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


# Use Dynatrace to monitor Liberty in {{site.data.keyword.cloud_notm}}
{: #using_dynatrace}

Dynatrace is a third-party service that provides monitoring for your app. You can integrate Dynatrace with your Liberty app, but {{site.data.keyword.IBM}} does not provide support for third-party services. See [Third-party services](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_support_statement#third-party) for more information.

For more information about Dynatrace and its licensing, see [Dynatrace Application Monitoring](https://www.dynatrace.com/solutions/application-monitoring/){: external}.

When your Liberty app is configured to use Dynatrace, the default behavior is that the
Liberty runtime will acquire a Dynatrace agent `.jar` file from a Dynatrace site and run
that Dynatrace agent with your app.  With that default behavior the minimal necessary
configuration to use Dynatrace is to create a user-provided service that points to
your Dynatrace collector.

## Creating a user-provided service that points to your Dynatrace collector

First, you'll need to set up a Dynatrace collector.  Then you must create a user-provided
service to pass information for the Dynatrace agent to connect with the Dynatrace collector. See [Dynatrace Architecture](https://community.dynatrace.com/community/display/DOCDT65/Architecture){: external} to better understand the relationship between Dynatrace components.

1. Set up a Dynatrace collector.
    * See the [Dynatrace community website](https://community.dynatrace.com/community/display/EVAL/Step+3+-+Connect+Agent+to+Dynatrace){: external} for instructions on downloading and setting up the Dynatrace collector.
    * Ensure that the collector is set up in a location that is accessible to the Dynatrace agent running with your app in {{site.data.keyword.cloud_notm}}.
2. Create a user-provided service that points to the running Dynatrace collector.

    **Note:** The name of the user-provided service must contain the string `dynatrace`. Case is ignored. For example, use the command that follows, where `my-dynatrace-collector` contains `dynatrace`:

    ```text
    ibmcloud cf cups my-dynatrace-collector -p '{"server":"DynatraceCollectorIPaddress","profile":"Monitoring"}'
    ```
    {: pre}

    In this example, `my-dynatrace-collector` is the name given to the service, `DynatraceCollectorIPaddress` is the IP address of the Dynatrace collector you have configured, and profile is the optional Dynatrace profile name associated with this monitored app. The default profile value is `Monitoring`. You can specify optional options as illustrated in the following example.

    ```text
    ibmcloud cf cups my-dynatrace-collector -p '{"server":"DynatraceCollectorIPaddress","profile":"Monitoring","options" : {"dynatrace-parameterr-1": "value", "dynatrace-parameter-2": "value"}}'
    ```
    {: pre}

    See the [_Agent Settings_ section of Agent Configuration](https://community.dynatrace.com/community/display/DOCDT65/Set+up+Agents){: external} at the Dynatrace community website for more information about available options. For example, by using the exclude option, you can exclude classes from being monitored by Dynatrace. See [Dynatrace Agent Framework](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/framework-dynatrace_one_agent.md){: external} for more details about configuring the user-provided service.

3. After you push your app to {{site.data.keyword.cloud_notm}}, bind the user-provided service that you created to the app. For example, use the following command:
 
    ```text
    ibmcloud cf bs myApp my-dynatrace-collector
    ```
    {: pre}

    **Note:** You must restage your app after binding the service.

## Optional configuration
{: #optional_configuration}

You may choose to acquire and host the Dynatrace agent `.jar` file yourself.  In that case the following additional configuration steps are needed.
1. Acquire and host the Dynatrace agent `.jar` file so that the Liberty buildpack can download it.
2. Configure your Liberty app so that it can download the Dynatrace agent.

### Hosting the Dynatrace agent
{: #hosting_dynatrace_agent}

The Dynatrace agent must be hosted on a web server, and the Liberty buildpack must be able to download the agent `.jar` file from that server. The server must be configured with an `index.yml` file that specifies details about the agent `.jar` file. Complete the steps that follow to set up the Dynatrace agent:
1. Download the Dynatrace agent `.jar` file. See [Dynatrace Server Platform Installers](https://community.dynatrace.com/community/display/EVAL/Step+1+-+Download+and+install+Dynatrace){: external} at the Dynatrace community website for instructions on downloading the Dynatrace agent `.jar` file. The appropriate agent `.jar` file for running on {{site.data.keyword.cloud_notm}} is the `dynatrace-agent-unix.jar` version `6.+`.
2. Host the agent `.jar` file in a location from which the Liberty buildpack can download it. You can host it on {{site.data.keyword.cloud_notm}} itself using any of the available server facilities, or you can host it on some publicly available location.
    
    * Ensure that you provide a `index.yml` file at the hosting location. The `index.yml` file must contain an entry consisting of the version ID of the agent `.jar` file follow by a colon and the complete URL of the location of that agent `.jar` file. For example:

        ```text
        6.3.0: https://my-dynatrace-agent.mybluemix.net/dynatrace-agent-6.3.0-unix.jar
        ```
        {: codeblock}

    * The `dynatrace-agent-6.3.0-unix.jar` file must be available at the location specified in the `index.yml` file. The location for both the `.jar` file and the `index.yml` can be the same directory.

### Configuring the Liberty app
{: #configuring_liberty_app}

The Liberty app you want to monitor must be configured to locate the server hosting the agent `.jar` file you previously set up. You can configure the app with the **JBP_CONFIG_DYNATRACEAPPMONAGENT** environment variable. The **JBP_CONFIG_DYNATRACEAPPMONAGENT** environment variable tells the buildpack where to download the Dynatrace agent from. To set the environment variable, complete these steps:

1. Set the variable **JBP_CONFIG_DYNATRACEAPPMONAGENT** so it has the value *"repository_root: URL_of_server_hosting_index.yml"*. For example, after pushing your app issue the following command:

    ```text
    ibmcloud cf se myApp JBP_CONFIG_DYNATRACEAPPMONAGENT 'repository_root: https://my-dynatrace-agent-host.mybluemix.net'
    ```
    {: pre}

    In this example, `my-dynatrace-agent-host.mybluemix.net` is the URL of the `index.yml` file hosted by the server that you previously configured.

2. After you set the environment variable, restage your app. Check the staging log for a message indicating successful download of the Dynatrace agent from your agent hosting server. For example:

    ```text
    Downloading dynatrace-agent-6.3.0-unix.jar 6.3.0 from https://my-dynatrace-agent-host.mybluemix.net/dynatrace-agent-6.3.0-unix.jar (17.8s)
    ```
    {: screen}


