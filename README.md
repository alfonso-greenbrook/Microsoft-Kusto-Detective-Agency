# Microsoft Kusto Detective Agency

The Microsoft Kusto Detective Agency Contest is a fun and engaging game that challenges participants to solve data mysteries using KQL, the query language of Azure Data Explorer. It aims to showcase the capabilities of Azure Data Explorer and is open to anyone who wants to learn more about data exploration and analysis. Anyone can join the game by creating a Kusto free cluster, and then visiting the game website: https://detective.kusto.io/

## Kusto Query Language

KQL stands for Kusto Query Language, a powerful tool to explore and analyze data in Azure Data Explorer and other services that use KQL. KQL is a read-only, data-flow model that uses schema entities, query statements, and operators to process data and return results. You can use KQL to filter, search, sort, join, project, aggregate, and visualize data in various ways. For example, you can use KQL to find the number of events in a specific time range, group them by category, and display them in a chart.

>[!TIP]
> You can learn more about KQL from the following resources:  
> - [Kusto Query Language (KQL) overview](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/): A comprehensive introduction to KQL, its syntax, and its features.  
> - [KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/kql-quick-reference): A handy list of functions and their descriptions to help you write KQL queries.  
> - [Keyword Query Language (KQL) syntax reference](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference): A guide to the elements and operators of KQL for Search in SharePoint.  

## Free Azure Data Explorer cluster

A free Azure Data Explorer cluster is a way to use the fast and scalable data exploration service without needing an Azure subscription or a credit card. You can create a free cluster with a Microsoft account or a Microsoft Entra user identity, and use it for any purpose. You can ingest data, run queries, and create dashboards using the Kusto Query Language (KQL). A free cluster has some limitations in terms of storage, databases, and features compared to a full cluster. You can upgrade your free cluster to a full cluster at any time. A free cluster is provided as-is and isn’t subject to the Azure Data Explorer service level agreement. 

> [!NOTE]
> You can learn more about how to create and use a free cluster from this article: https://learn.microsoft.com/en-us/azure/data-explorer/start-for-free

## SANS Holiday Hack 2023!

Getting started:
```
.execute database script <|
.create table AuthenticationEvents (timestamp:datetime, hostname:string, src_ip:string, user_agent:string, username:string, result:string, password_hash:string, description:string)
.create table Email (timestamp:datetime, sender:string, reply_to:string, recipient:string, subject:string, verdict:string, link:string)
.create table Employees (hire_date:datetime, name:string, user_agent:string, ip_addr:string, email_addr:string, company_domain:string, username:string, role:string, hostname:string)
.create table FileCreationEvents (timestamp:datetime, hostname:string, username:string, sha256:string, path:string, filename:string, process_name:string)
.create table InboundNetworkEvents (timestamp:datetime, ['method']:string, src_ip:string, user_agent:string, url:string)
.create table OutboundNetworkEvents (timestamp:datetime, ['method']:string, src_ip:string, user_agent:string, url:string)
.create table PassiveDns (timestamp:datetime, ip:string, domain:string)
.create table ProcessEvents (timestamp:datetime, parent_process_name:string, parent_process_hash:string, process_commandline:string, process_name:string, process_hash:string, hostname:string, username:string)
.create table SecurityAlerts (timestamp:datetime, alert_type:string, severity:string, description:string, indicators:dynamic)
// Ingest data into tables
.ingest into table AuthenticationEvents ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/AuthenticationEvents.csv') with (ignoreFirstRecord = true)
.ingest into table Email ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/Email.csv') with (ignoreFirstRecord = true)
.ingest into table Employees ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/Employees.csv') with (ignoreFirstRecord = true)
.ingest into table FileCreationEvents ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/FileCreationEvents.csv') with (ignoreFirstRecord = true)
.ingest into table InboundNetworkEvents ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/InboundNetworkEvents.csv') with (ignoreFirstRecord = true)
.ingest into table OutboundNetworkEvents ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/OutboundNetworkEvents.csv') with (ignoreFirstRecord = true)
.ingest into table PassiveDns ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/PassiveDns.csv') with (ignoreFirstRecord = true)
.ingest into table ProcessEvents ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/ProcessEvents.csv') with (ignoreFirstRecord = true)
.ingest into table SecurityAlerts ('https://kustodetectiveagency.blob.core.windows.net/sans2023c0start/SecurityAlerts.csv') with (ignoreFirstRecord = true)
```
