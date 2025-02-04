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


# Troubleshooting for runtimes
{: #runtimes}

You might experience problems when you use {{site.data.keyword.cloud}} runtimes. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## General troubleshooting
{: #ts_all}

### Obsolete buildpack used when an app is pushed
{: #ts_loading_bp}

You might not be able to use the latest buildpack components when you push an app. You can use buildpacks that have built-in mechanisms to prevent loading obsolete components, or you can delete the contents in your app's cache directory before you push or restage the app.

When you push or restage an app after the buildpack is updated, the latest buildpack components aren't loaded automatically. As a result, your app uses the obsolete buildpack components from the cache. Updates that were applied to the buildpack since the last time you pushed the app aren't implemented.
{: tsSymptoms}

Some buildpacks aren't configured to automatically download all updated components from the internet to ensure that you always use the latest version.
{: tsCauses}

You can use buildpacks that have built-in mechanisms to avoid loading obsolete components, for example, the following buildpacks:
{: tsResolve}

* [Cloud Foundry Java buildpack](https://github.com/cloudfoundry/java-buildpack){: external}. This buildpack has a built-in mechanism to ensure that the latest version of the buildpack is used. For more information about how this mechanism works, see [extending-caches.md](https://github.com/cloudfoundry/java-buildpack/blob/main/docs/extending-caches.md){: external}.

* [Cloud Foundry Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack){: external}. This buildpack provides similar functions by using environment variables. To enable the Node.js buildpack to download node modules from the internet every time, type the following command in the {{site.data.keyword.cloud_notm}} command-line interface: 	

    ```text
    set NODE_MODULES_CACHE=false
    ```
    {: codeblock}

If the buildpack that you are using doesn't provide a mechanism to load the latest components automatically, you can manually delete the contents in the cache directory and push your app again. Use the following steps:

1. Check out a branch of a null buildpack, for example, https://github.com/ryandotsmith/null-buildpack. For information about how to check out a branch, see [Git Basics - Getting a Git Repository](http://www.git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository){: external}.

2. Add the following line to the `null-buildpack/bin/compile` file and commit the changes. For information about how to commit changes, see [Git Basics - Recording Changes to the Repository](http://www.git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository){: external}.
 
    ```text
    rm -rfv $2/*
    ```
    {: pre}

3. Push your app with the null buildpack that was modified to delete the cache by using the following command. After you complete this step, all contents in the cache directory of your app are deleted.

    ```text
    ibmcloud cf push appname -p app_path -b <modified_null_buildpack>
    ```
    {: pre}

4. Push your app with the latest buildpack that you want to use by using the following command:

    ```text
    ibmcloud cf push appname -p app_path -b <latest_buildpack>
    ```
    {: pre}

### The app continues to restart
{: #ts_apprestart}

The app continues to crash and restart.
{: tsSymptoms}

The app container lifecycle, such as evacuation and shut down, can impact your app functions.  
{: tsCauses}

Identify which step of the app container lifecycle is causing errors in app deployment. Learn more about the [Cloud Foundry app lifecycle](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#evacuation){: external}.
{: tsResolve}

### The Actions button on the Instance Details page is disabled (Deprecated)
{: #ts_actionsbutton}

The Actions button on the Instance Details page is unavailable.
{: tsSymptoms}

This problem occurs for the following reasons:
{: tsCauses}

* The app isn't deployed with the embedded Liberty buildpack.

* The app was deployed with an early version of Liberty buildpack.

If the problem is caused by an early version of Liberty buildpack, redeploy the app in {{site.data.keyword.cloud_notm}}. Otherwise, you can provide the following client app log files to the support team:
{: tsResolve}

* `logs/messages.log`

* `logs/stdout.log`

* `logs/stderr.log`


### Credentials are required to open a trace or memory dump window (Deprecated)
{: #ts_username}

A user name and password are required to open the trace or memory dump window.
{: tsSymptoms}

This problem occurs because of the login session timeout.
{: tsCauses}

Enter the user name and password again.
{: tsResolve}


### Error occurs when trace or memory dump operations are running (Deprecated)
{: #ts_target}

An error message is displayed while the trace or memory dump operations are running. The message indicates that a target instance for an app isn't in the running state:
{: tsSymptoms}

```text
Instance 0: Trace specification is set successfully
Instance 2: Trace specification is set successfully
Instance 1: Target instance 1 for app abcd is not in the running state.
Instance 3: Trace specification is set successfully
Instance 4: Trace specification is set successfully
```
{: screen}

This problem occurs for the following reasons:
{: tsCauses}

* The trace or dump management capabilities are only for app instances that are running. Trace or dump operations can't be used on app instances that are stopped, starting, or crashed.

* The status of the app instance is changing when the trace or dump dialog is opened.

Close the window, then open it again.
{: tsResolve}


### Instances have different `traceSpecification` configurations (Deprecated)
{: #ts_different_config}

For different instances of one app, you might see different `traceSpecification` configurations.
{: tsSymptoms}

This behavior occurs for the following reasons:
{: tsCauses}

* You changed the configuration for one or more instances previously. If you change the `traceSpecification` configuration for one instance, the change doesn't apply to other instances of the same app. For example, your app uses log4j and you have 2 instances for this app. You can change the log level of instance 0 from info to debug, but the log level of instance 1 remains as info.

No action is required. This behavior is expected.
{: tsResolve}


### Disk quota exceeded
{: #ts_diskquota}

You might see, in your app log, that your disk quota is exceeded.

You see the `Disk quota exceeded` error message in the log of your app.
{: tsSymptoms}

This problem occurs for one of the following reasons:
{: tsCauses}

* The dump files are generated with the running app instances, and the files use up the allocated disk quota. By default, the disk quota for one app instance is 1 GB. You can check your disk usage by clicking **Dashboard > Application > App Runtime**. The following example shows the runtime information, including disk usage, for two instances of an app:

```text
      Instance	State	CPU	Memory Usage	Disk Usage

  	0		Running	1.0%	344.8MB/512MB	236.8MB/1GB
  	2		Running	2.3%	361.2MB/512MB	235.7MB/1GB
```
{: screen}

* The disk quota is limited by the current organization quota.

Use one of the following methods:
{: tsResolve}

* Delete dump files after they are downloaded.

* Redeploy the app with a bigger disk quota by including the following entry in the deployment manifest:

    ```text
    disk_quota: 2048
    ```
    {: codeblock}

## Liberty for Java
{: #ts_liberty}

### App fails to start accepting connections
{: #health_check_timeout}

A Liberty app fails to start with a "_Failed to start accepting connections_" error. For example, the error in the logs might look like the following:
{: tsSymptoms}

```text
   2016-11-14T14:44:58.45+0000 [API/0]      OUT App instance exited with guid 21ac63eb-9595-428a-94c7-b0b02aaf77cc payload: {"cc_partition"=>"default", "droplet"=>"21ac63eb-9595-428a-94c7-b0b02aaf77cc", "version"=>"b2772438-92de-4d47-b680-ea772ac2288a", "instance"=>"f4799c8c89214bbd8067883c3ffe23e0", "index"=>0, "reason"=>"CRASHED", "exit_status"=>255, "exit_description"=>"failed to accept connections within health check timeout", "crash_timestamp"=>1479134698}
   2016-11-14T14:45:07.50+0000 [DEA/4]      ERR Instance (index 0) failed to start accepting connections
```
{: screen}

{{site.data.keyword.cloud_notm}} performs a health check on the app to see whether it has successfully started. The health check tests if the app is listening on the port that is assigned to the app. The default timeout for this check is 60 seconds and some apps might take longer than 60 seconds to start. There are a number of reasons why the app might take longer to start. For example, binding services such as [New Relic](/docs/cloud-foundry-public?topic=cloud-foundry-public-new_relic) will increase the start-up time. The app might also perform initialization steps that might take a long time to finish.
{: tsCauses}

First, examine the logs for any obvious errors that might cause the Liberty app to fail. If no obvious errors are found, then try the following solutions:
{: tsResolve}

#### Increase the health check timeout

* When you deploy the app by using the `ibmcloud cf push` command, specify a longer app start timeout by using the `-t` option. For example:

    ```text
  	ibmcloud cf push myApp -t 180
    ```
    {: pre}

* The health check timeout can also be specified in the manifest.yml file. For example:

    ```text
       ---
           ...
           timeout: 180
    ```
    {: codeblock}

#### Disable the `appstate` feature

The `appstate` feature integrates with the {{site.data.keyword.cloud_notm}} health check process to ensure that the Liberty app is fully initialized before the app can receive HTTP requests. After the app is fully initialized the `appstate` feature has no more effect.  The side effect of this feature is that some apps might take longer to start up. To disable the `appstate` feature, set the following environment property on your app and restage the app:

```text
ibmcloud cf set-env myApp JBP_CONFIG_LIBERTY "app_state: false"
```
{: pre}

#### Consider re-factoring the app

If your app takes a long time to initialize, you might have to re-factor the app to do lazy and/or asynchronous initialization.

#### Deploy with the "no-route" option

1. Deploy your app with "--no-route" option. This will disable the port health check. For example:

    ```text
  	ibmcloud cf push myApp –no-route
    ```
    {: pre}

2. Once the app is initialized, map a route to the app. For example:

    ```text
    ibmcloud cf map-route myApp mybluemix.net
    ```
    {: pre}

### SSL errors with IBM's gateway
{: #ssl_handshake_failure}


The following errors are visible in the logs and the app may fail to start:
{: tsSymptoms}

```text
2016-11-03T12:32:44.82-0200 [App/0]      ERR java.security.cert.CertPathValidatorException: Certificate chaining error
2016-11-03T12:32:44.83-0200 [App/0]      ERR [ERROR   ] CWPKI0022E: SSL HANDSHAKE FAILURE:  A signer with SubjectDN CN=*.gateway.prd.na.ca.ibmserviceengage.com, O=International Business Machines Corp., L=Armonk, ST=New York, C=US was sent from the target host.  The signer might need to be added to local trust store /home/vcap/app/wlp/usr/servers/defaultServer/resources/security/key.jks, located in SSL configuration alias defaultSSLConfig.  The extended error message from the SSL handshake exception is: PKIX path building failed: java.security.cert.CertPathBuilderException: PKIXCertPathBuilderImpl could not build a valid CertPath.; internal cause is:
2016-11-03T12:32:44.83-0200 [App/0]      ERR java.security.cert.CertPathValidatorException: The certificate issued by CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US is not trusted; internal cause is:
2016-11-03T12:32:44.83-0200 [App/0]      ERR java.security.cert.CertPathValidatorException: Certificate chaining error
```
{: screen}

The errors can be generated when a secure service is bound to a Liberty app and the Liberty app was deployed as a server directory or packaged server that contains a `server.xml` file that configures the Liberty `ssl-1.0` feature. Binding the secure service to the Liberty app causes the runtime to connect to the service over a secure connection. That secure connection is established by using the default SSL settings. Because the default SSL settings are specified in the Liberty `server.xml` file, the configured trust store might not trust the certificate that is used by the secure service.
{: tsCauses}

Modify configuration to use the JVM's trust store with one of the options that follow.  Be sure to restage your app after making the change.
{: tsResolve}

#### Update the Liberty `server.xml` file

Update the `server.xml` file to use the JVM `cacerts` file as the trust store. Add the following to your `server.xml` file:

```text
        <ssl id="defaultSSLConfig" trustStoreRef="defaultTrustStore"/>
        <keyStore id="defaultTrustStoretore" location="${java.home}/lib/security/cacerts"/>
```
{: codeblock}

#### Update the configured trust store

Modify the configured trust store to trust the DigiCert ROOT CA.

1. Download the DigiCert Root CA from `https://cacerts.digicert.com/DigiCertGlobalRootCA.crt`.

2. Assuming the `resources/security/key.jks` is used as the trust store, import the CA into the key using the Java `keytool` utility:

    ```text
    keytool -importcert --storepass <keyStorePassword> -keystore &lt;path&gt;/resources/security/key.jks -file DigiCertGlobalRootCA.crt
    ```
    {: pre}


## SDK for Node.js
{: #ts_nodejs}

### App fails to start: General troubleshooting

For the {{site.data.keyword.runtime_nodejs_notm}} buildpack V3.23 or later, try packaging the dependencies in the same source files as your app. This can resolve various errors that can occur when dependencies assume that they are in the same base directory as the app.

1. From your app root directory, install dependencies by running the following command.

    ```text
    npm install
    ```
    {: pre}

2. Ensure that your `.cfignore` file does not include the following line:

    ```text
    node_modules/
    ```
    {: codeblock}

Now when you deploy your app with the  `ibmcloud cf push` command, instead of downloading your dependencies to a separate location, the dependencies are copied into the same directory as the rest of the app.

### App fails to start with a "No space left on device" error
{: #no_space_left_on_device}


A Node.js app fails to start with a "No space left on device" error. For example, the error in the logs might look like the following:
{: tsSymptoms}

```text
   2017-01-16T14:25:14.61-0500 [CELL/0]     ERR tar: ./app/node_modules/pm2/node_modules/cron/node_modules/moment-timezone/LICENSE: Cannot write: No space left on device

```
{: screen}

Node.js apps using NPM versions prior to version 3 consume more space downloading dependencies.
{: tsCauses}

Modify the package.json file for your app to use an NPM version 3 or greater.
{: tsResolve}

```text
{
  "name": "myapp",
  "description": "this is my app",
  "version": "0.1",
  "engines": {
     "node": "4.2.4",
     "npm": "3.10.10"
  }
}
```
{: codeblock}

### App restarts due to memory constraints
{: #oom}

Node.js does not know how much memory is available to the app, so the garbage collector might not run before memory is exhausted.

```text
2017-09-01T11:00:42.19-0400 [APP/PROC/WEB/0]OUT Exit status 137
2017-09-01T11:00:42.23-0400 [CELL/0]     OUT Exit status 0
2017-09-01T11:00:42.27-0400 [CELL/0]     OUT Destroying container
2017-09-01T11:00:42.34-0400 [API/0]      OUT Process has crashed with type: "web"
2017-09-01T11:00:42.36-0400 [API/0]      OUT App instance exited with guid eecfba3b-430c-4a6b-b71f-ac72816fe152 payload: {"instance"=>"77dbb981-16d0-3a05-3235-9a4b", "index"=>0, "reason"=>"CRASHED", "exit_description"=>"2 error(s) occurred:\n\n* 2 error(s) occurred:\n\n* Exited with status 137 (out of memory)\n* cancelled\n* cancelled", "crash_count"=>1, "crash_timestamp"=>1504278042244633291, "version"=>"6497b5b5-67d4-4c5a-b1af-362e522a029d"}
2017-09-01T11:00:43.35-0400 [CELL/0]     OUT Successfully destroyed container
```
{: screen}

A possible solution is to set the `--max_old_space_size` option on the app's start command in the package.json file. This option represents part of the app's memory footprint and should be set to a value less than the total memory available to the app. Read about [Large memory spikes and Heroku](https://github.com/nodejs/node/issues/3370){: external} for a more in-depth discussion of this topic.

```text
  "scripts": {
    "start": "node --max_old_space_size=800 server.js"
  }
```
{: codeblock}

## ASP.NET Core
{: #ts_dotnet}

The app fails to deploy with the message: `API/0App instance exited ... payload: {... "reason"=>"CRASHED", "exit_status"=>-1, ...}`.
{: tsSymptoms}

If you receive a similar message when you push your ASP.net app, it is most likely because your app exceeds either the memory or disk quota limits.  Increase the quotas for memory or disk space for your app.
{: tsCauses}

The app fails to deploy with the message: `Failed to compress droplet: signal: broken pipe` or `No space left on device`.  How can I fix this?
{: tsSymptoms}

Projects pushed from source code that contains a large number of NuGet package dependencies can sometimes cause this error when the NuGet package cache is enabled.  Set the `CACHE_NUGET_PACKAGES` environment variable to `false` to disable the cache.
{: tsCauses}

### Helpful links

* [NuGet](https://docs.microsoft.com/en-us/nuget/consume-packages/overview-and-workflow){: external}

* [ASP.NET Core Overview](http://docs.asp.net/en/latest/conceptual-overview/aspnet.html){: external}

## PHP
{: #ts_PHP}

### NOTICE messages from the PHP buildpack
{: #ts_phplog}

You might see messages that contain NOTICE from the logs. You can stop the logging of these messages by changing the logging level.

When you push an app to {{site.data.keyword.cloud_notm}} by using a PHP buildpack, you might see messages that contain `NOTICE`:
{: tsSymptoms}

```text
• 2015-01-26T15:00:59.70+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: [pool www] 'user' directive is ignored when FPM is not running as root
• 2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: [pool www] 'user' directive is ignored when FPM is not running as root
• 2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: fpm is running, pid 93
• 2015-01-26T15:01:00.63+0100 [App/0] ERR [26-Jan-2015 14:00:59] NOTICE: ready to handle connections
```
{: screen}

In the PHP buildpack, the error_log option defines the logging level. By default, the value of the `error_log` option is `stderr notice`. The following example shows the default logging level configuration in the `nginx-defaults.conf` file of the PHP buildpack that Cloud Foundry provides. For more information, see [cloudfoundry/php-buildpack](https://github.com/cloudfoundry/php-buildpack/blob/ff71ea41d00c1226d339e83cf2c7d6dda6c590ef/defaults/config/nginx/1.5.x/nginx-defaults.conf){: external}.
{: tsCauses}

```text
daemon off;
error_log stderr notice;
pid @{HOME}/nginx/logs/nginx.pid;
```
{: codeblock}

The `NOTICE` messages are for information and might not indicate a problem. You can stop the logging of these messages by changing the logging level from `stderr notice` to `stderr error` in the `nginx-defaults.conf` file in  your buildpack. For example: 	
{: tsResolve}

```text
daemon off;
error_log stderr error;
pid @{HOME}/nginx/logs/nginx.pid;
```
{: codeblock}

For more information about how to change the default logging configuration, see [error_log](http://nginx.org/en/docs/ngx_core_module.html#error_log){: external}.


## Python
{: #ts_python}

### Can't import a third-party Python library into {{site.data.keyword.cloud_notm}}
{: #ts_importpylib}

You might not be able to import a third-party Python library into {{site.data.keyword.cloud_notm}}. To resolve the problem, add configuration files to the root directory of your python app.

When you try to import a third-party Python library, such as the `web.py` library, the `ibmcloud cf push` command fails.
{: tsSymptoms}

Configuration information for the Python app is missing.
{: tsCauses}

Add a `requirements.txt` file and a `Procfile` file to the root directory of your Python app. The following information assumes that you are importing the `web.py` library:
{: tsResolve}

 1. Add a `requirements.txt` file to the root directory of your Python app.

     The `requirements.txt` file specifies the library packages that are required for your Python app and the version of the packages. The following example shows the content of the `requirements.txt` file, where `web.py==0.37` indicates the version of the `web.py` library that will be downloaded is 0.37, and `wsgiref==0.1.2` indicates the version of the web server gateway interface that is required by the web.py library is 0.1.2.
	 
    ```text
	  web.py==0.37
      wsgiref==0.1.2
	  ```
    {: codeblock}

	  For more information about how to configure the `requirements.txt` file, see [Requirements files](https://pip.pypa.io/en/stable/user_guide/?highlight=requirements.txt#requirements-files){: external}.

 2. Add a `Procfile` file to the root directory of your Python app.
 The `Procfile` file must contain the start command for your Python app. In the following command, `<yourappname>` is the name of your Python app, and *PORT* is the port number that your Python app must use to receive requests from users of the app. *$PORT* is optional. If you don't specify PORT in the start command, the port number under the `VCAP_APP_PORT` environment variable that is inside the app is used.

    ```text
    web: python <yourappname>.py $PORT
    ```
    {: codeblock}

You can now import the third-party Python library into {{site.data.keyword.cloud_notm}}.



