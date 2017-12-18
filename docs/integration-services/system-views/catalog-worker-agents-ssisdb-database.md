---
title: "catalog.worker_agents (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a74c1d81b2defff8b3d5566c221e1df102c136e2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogworkeragents-ssisdb-database"></a>catalog.worker_agents (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает сведения для рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|Идентификатор агента рабочей роли для рабочей роли Scale Out.|
|IsEnabled|**bit**|Указывает, включена ли рабочая роль Scale Out.|
|DisplayName|**nvarchar(256)**|Отображаемое имя рабочей роли Scale Out.|
|Description|**nvarchar(256)**|Описание рабочей роли Scale Out.|
|MachineName|**nvarchar(256)**|Имя компьютера рабочей роли Scale Out.|
|Теги|**nvarchar(max)**|Теги рабочей роли Scale Out.|
|UserAccount|**nvarchar(256)**|Учетная запись, под которой выполняется служба рабочей роли Scale Out.|
|LastOnlineTime|**datetimeoffset(7)**|Время последнего подключения рабочей роли Scale Out.|

## <a name="remarks"></a>Замечания
В этом представлении отображается строка для каждой рабочей роли Scale Out, которая подключается к мастеру Scale Out, работающему с каталогом SSISDB.

## <a name="permissions"></a>Permissions
Это представление требует применения одного из следующих разрешений:

- Членство в роли базы данных **ssis_admin**

- Членство в роли базы данных **ssis_cluster_executor**

- Членство в роли сервера **sysadmin**
