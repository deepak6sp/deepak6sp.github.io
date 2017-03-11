---
layout: post
title:  "Getting started with Jenkins and Git integration"
date:   2017-01-24 22:21:57 +1100
categories: DevOps
---
To get started, go to https://jenkins.io/index.html. Under LTS release, just click the build button, which will start downloading .war format.

Make sure you have java runtime installed. You can check this by typing
<pre>java -version</pre>

Now, go to folder where jenkins.war file is downloaded. Then, in command line, type
<pre>java -jar jenkins.war</pre>
This will start installing Jenkins.

Jenkins is initially configured to be secure on first launch. Jenkins can no longer be accessed without a username and password and open ports are limited.

While jenkins is getting installed, note down the password displayed. This is the admin password for initial setup.

Open any browser and go to
<pre>http://localhost:8080</pre>

You can see Jenkins page is running. Please use the password saved before and click <strong>continue</strong>.

On the next screen, select install <strong>suggested</strong> plugins. You could select <strong>none</strong> for now as we will install relevant plugins when needed, in future.

Jenkins will start installing plugins, if you still like to proceed, and this could take few minutes. After installation, you will be directed to new admin user create page.

You could either start as new user or click <strong>continue as admin</strong> at the bottom of the page.

Thus, Jenkins installation is completed.

Now, we will start integrating Git with Jenkins, Click create <strong>New Item</strong> and enter item name. For example, “Demo”. Select “Freestyle Project” and click ok.

In the next page, select “Source Code Management” tab, and select 'Git' option.

If you can’t find git options, please install git plugin, by going back to

<strong>managejenkins -> manage plugins -> available</strong>,

then in filter by type “git plugin”. Select and install.

Then, go to <strong>Build triggers</strong> tab and select <strong>Poll SCM</strong>. Type <strong>* * * * \*</strong> to check your git repo every second for changes.

Then , in the <strong>Build</strong> tab , from the dropdown,  select <strong>Execute shell</strong if you are on mac or linux else select <strong>Execute Windows batch command</strong>, if you are on windows.

Type command you are intended to run in the textarea. Finally, click <strong>save and apply</strong>.

However, polling git for changes every second is inefficient. So, in order to poll only when there is commit to GitHub, install <strong>github plugin<strong>.

Now, if you go back to <strong>build triggers</strong> tab, you will see a new option.
<strong>GitHub hook trigger for GITScm polling</strong>.

Select, click <strong>apply and save</strong>.

Now, we need to activate Jenkins GitHub Plugin which can automatically trigger build jobs when pushes are made to GitHub. So, in github website, go to <strong>settings</strong> of the repository.
On left tab section,  select <strong>integration and services</strong> tab. Click <strong>add service</strong> and from dropdown, select <strong>Jenkins(GitHub plugin)</strong>.

Provide <strong>Jenkins hook url</strong>, which is the jerkin server address you are running
<pre>http://jenkins-domain-name:8080/github-webhook/</pre>


Finally, click <strong>Add service</strong>.
