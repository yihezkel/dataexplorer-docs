---
title: include file
description: include file
author: orspod
ms.service: data-explorer
ms.topic: include
ms.date: 07/13/2020
ms.author: orspodek
ms.reviewer: alexefro
ms.custom: include file
---
## Limitations

* [Database cursors](../kusto/management/databasecursor.md) aren't supported for a database if the database itself or any of its tables have the [Streaming ingestion policy](../kusto/management/streamingingestionpolicy.md) defined and enabled.
* [Data mappings](../kusto/management/mappings.md) must be [pre-created](../kusto/management/create-ingestion-mapping-command.md) for use in streaming ingestion. Individual streaming ingestion requests don't accommodate inline data mappings.
* Streaming ingestion performance and capacity scales with increased VM and cluster sizes. The number of concurrent ingestion requests is limited to six per core. For example, for 16 core SKUs, such as D14 and L16, the maximal supported load is 96 concurrent ingestion requests. For two core SKUs, such as D11, the maximal supported load is 12 concurrent ingestion requests.
* The data size limit for streaming ingestion request is 4 MB.
* Schema updates, such as creation and modification of tables and ingestion mappings, may take up to five minutes for the streaming ingestion service. For more information see [Streaming ingestion and schema changes](../kusto/management/data-ingestion/streaming-ingestion-schema-changes.md).
* Enabling streaming ingestion on a cluster, even when data isn't ingested via streaming, uses part of the local SSD disk of the cluster machines for streaming ingestion data and reduces the storage available for hot cache.
* [Extent tags](../kusto/management/extents-overview.md#extent-tagging) can't be set on the streaming ingestion data.
* If streaming ingestion is used on any of the tables of the database, this database cannot be used as leader for [follower databases](../follower.md) or as a [data provider](../data-share.md#data-provider---share-data) for Azure Data Share.
