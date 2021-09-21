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


# Design the structure of your environment
{: #bpimplementation}



Instead of the traditional, strictly defined development, test, and production methodology, you can implement an environment where developers and testers can collaborate along with other team members. If you design the way you want to develop and deliver your apps, create spaces to fulfill that methodology. Instead of designing your environment from the organization level down, consider designing your environment from the space level up.
{: shortdesc}

Consider the scale and scope of the apps you plan to develop and deploy. A Cloud Foundry space can be used as a development environment for one or more apps that are tightly connected or defined. Apart from a development space, for example, you can create spaces for unit testing, performance testing, and integration testing. Spaces can also be defined for build, staging, and production. Each of the spaces that you create can be shared with different team members within the same organization.

Create separate Cloud Foundry organizations when you have people working on different business areas and where their activities do not overlap. If there are two independent groups, then creating an organization for each defines clear boundaries for the delivery and management of team players and resources. You can define an API to communicate between the organizations.

Cloud Foundry organizations can be created to match how you want to work rather than the structure within a company. Typically, company organizations can change but the development and maintenance of an app continues regardless. Design your instance for the lifetime of the apps and not on your company organization structure.

Iterative development and deployment can result in apps that expand quickly. Your delivery process design must be able to scale up quickly and easily. You want continuous development with a fast deployment rate. Having your development and production spaces in the same organization provides access to the same resources. Managing different spaces within a single organization reduces the administration workload. The development, test, and operations personnel can collaborate easily if they are working within the same organization.

Implement a naming standard to clearly identify the organization and space usage. For example, you might include the type of cloud, the geographical region, the usage type (such as development, test, production), the app name, and the version or revision number. The organizations and spaces can then be easily identified for administration and access purposes.  

The number of spaces can multiply rapidly because of iterative development. You can define as many spaces as you need within an organization. If you plan to define many spaces, you might want to create an app to help manage the spaces. When the number of spaces exceeds sixty, you might want to consider defining another organization.

Have one person create and manage an organization, define the spaces, and grant team member access. A second person can be given the same access to maintain the environment when the organization manager is disabled.  

Identify all of the people who need access to each space and organization. Determine their role. The job role of a team member determines their authority. For example, a senior developer needs the authority to view and update the entire development environment. However, a junior developer is limited as to what they can view and update.


