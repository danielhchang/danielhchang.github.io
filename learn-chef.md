---
layout: default
title: Learning Chef
---
# [Learning Chef](https://www.chef.io/)

======
## What is Chef

Chef is a server configuration management system.  It falls into similar category as ansible and puppet.  It is used to automate and manage infrastructure and applications.  It's part of the "infrastructure as code" and it's used to predictably and repeatably configure servers for a particular application.  

Chef is built on ruby.  The Chef Development Kit (ChefDK) includes the chef-client, embedded ruby, rubygems, etc.  There's a Windows, Mac and Linux versions.

## Study Resources

* [Chef Fundamentals](https://www.udemy.com/chef-fundamentals-a-recipe-for-automating-infrastructure)

## Terminology/Glossary

chef
chef-client
knife
ohai = (system details)
berks
kitchen
foodcritic
cookstyle

## My notes

Installation https://downloads.chef.io/chefdk

Idempotency - This is a frequently used concept and refers to the behavior that repeated calls will still have the same result.  The operation will result in applying changes to the desired state.  If it is already in the desired state, the operation will do nothing.

Resources -
type of resource (e.g. package, service, file)
name of resource 'httpd' or 'ntp' or /etc/motd'
action/default action (e.g. :install, :enable, :start)
properties

```
package 'httpd' do
  action :install
end

service 'ntp' do
  action [ :enable, :start ]
end

file '/etc/motd' do
  content 'Message of the Day'
  action :create
end
```

Recipes are writing in ruby and they are an ordered list of resources.  They can include other recipes and can have dependencies.

Nodes are machines that are managed by Chef
There's node attributes that can be used (see ohai) -> node[`attribute`] is the way to reference it.

Cookbooks define a scenario and contains everthing that is required to support the scenario including metadata, recipes, attribute values, file distributions, templates, and extensions to chef (custom resources and libraries).  

There are shared Cookbooks, some maintained by Chef and others maintained by the Community.

Language Syntax
do/end blocks -

string interpolation (substituting values within strings) -- ``#{ }``
for instance we can do the #{node['memory'][`total`]} to get memory.

```
file '/var/www/html/index.html' do
        content "<h1>Hello, world!</h1>
        <h2>IPADDRESS: #{node['ipaddress']}</h2>
        <h2>HOSTNAME: #{node['hostname']}</h2>
"
end
```

ERB - Embedded Ruby Template - ruby expressions and statements are allowed within ERB tags.  

The ERB tag uses <% %>
Execute the ruby code but don't insert anything into the file.  This is for ruby logic.

There is a different tag <%= %> this will print the results into the template file.
This can be used within plain text files like /etc/motd, but it can also be used for code such as /var/www/html/index.html
