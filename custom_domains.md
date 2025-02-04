---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-21"

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


# Adding and using a custom domain
{: #custom-domains}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. Custom domains direct requests for your apps to a URL that you own. A custom domain can be a shared domain, a shared subdomain, or a shared domain and host. Unless a custom domain is specified, {{site.data.keyword.cloud_notm}} uses a default shared domain in the route to your app. You can create and use a custom domain by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface.
{: shortdesc}

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use. For more information about migrating to `appdomain.cloud`, see [Updating your domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

To use a custom domain, you must register the custom domain on a public DNS server, and then configure the custom domain in {{site.data.keyword.cloud_notm}}. Next, you must map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your app in {{site.data.keyword.cloud_notm}}.

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} console
{: #custom-domain-console}

Complete these steps to add a custom domain for your org by using the console:

1. Go to **Manage > Account**, and select **Cloud Foundry orgs**.

2. Click the name of the org for which you're creating a custom domain.

3. Click the **Domains** tab to view a list of available domains.

4. Click **Add a domain**, enter your domain name, and select the region.

5. Confirm your updates, and click **Add**.

## Adding the route with the custom domain to an app

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and select **Resource List**.

2. On the **Resource List** page, click **Cloud Foundry Apps**.

3. Click the app that you want to add the route to. The app's **Overview** page is displayed.

4. Select the **Routes** menu, and select **Edit routes**.

5. Click **Add route**, and specify the route that you want to use for the app.

6. Confirm your updates by clicking **Save**.

As an example, you can use `*.mycompany.com` to associate the route `www.mybluemix.net` to your app. You can also use `example.mycompany.com` to associate the route `www.example.bluemix.net` to your app.
{: tip}

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} command-line interface
{: #custom-domain-cli}

1. For Cloud Foundry apps, connect to your targeted Cloud Foundry API endpoint by typing the following command:

    ```text
    ibmcloud target --cf-api <CF_ENDPOINT>
    ```
    {: pre}

    **Cloud Foundry API endpoints:**
    * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
    * US-EAST - `api.us-east.cf.cloud.ibm.com`
    * EU-DE - `api.eu-de.cf.cloud.ibm.com`
    * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
    * AU-SYD - `api.au-syd.cf.cloud.ibm.com`

2. Create a custom domain for your organization by typing the following command:
   
    ```text
    ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
    ```
    {: pre}

3. Add the route with the custom domain to an app.

    For Cloud Foundry apps, run the following command:
   
    ```text
    ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
    ```
    {: pre}

## Mapping the custom domain to the system domain
{: #mapcustomdomain}

After you configure the custom domain in {{site.data.keyword.cloud_notm}}, map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on your registered DNS server:

1. Set up a 'CNAME' record for the custom domain name on your DNS server. Steps for setting up the CNAME record vary depending on your DNS provider. For example, if you use GoDaddy, you follow the [Domains Help](https://www.godaddy.com/help/add-a-cname-record-19236){: external} guidance from GoDaddy.

2. Map the custom domain name to the secure endpoint for the {{site.data.keyword.cloud_notm}} region where your app is running. Use the following region endpoints to provide the URL route that is allocated to your organization in {{site.data.keyword.cloud_notm}}. For example, point your CNAME to `custom-domain.us-east.cf.cloud.ibm.com.`

    **Cloud Foundry endpoints:**
   
    * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
    * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
    * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
    * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
    * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Accessing your app
{: #access-app}

In a browser, enter the following URL to access your app, where `hostname` is your host name, and `mydomain` is your domain name:

```text
http://hostname.mydomain
```
{: codeblock}

## Removing an orphaned route
{: #remove-orphaned-route}

To remove an orphaned route, run the following command:

```text
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: pre}

In that example, `MY_DOMAIN` is the name of your domain, and `MY_HOSTNAME` is the host name of the route for your app. For more information about the `ibmcloud app route-delete` command, enter the command `ibmcloud app route-delete -h`.


