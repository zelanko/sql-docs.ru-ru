---
title: catalog.worker_agents (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f8c494e135764ddca11985f3036068c848f818b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912430"
---
# <a name="catalogworker_agents-ssisdb-database"></a>catalog.worker_agents (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Отображает сведения для рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] горизонтального увеличения масштаба.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|Идентификатор агента рабочей роли для рабочей роли горизонтального увеличения масштаба.|
|IsEnabled|**bit**|Указывает, включена ли рабочая роль горизонтального увеличения масштаба.|
|DisplayName|**nvarchar(256)**|Отображаемое имя рабочей роли горизонтального увеличения масштаба.|
|Description|**nvarchar(256)**|Описание рабочей роли горизонтального увеличения масштаба.|
|MachineName|**nvarchar(256)**|Имя компьютера рабочей роли горизонтального увеличения масштаба.|
|Теги|**nvarchar(max)**|Теги рабочей роли горизонтального увеличения масштаба.|
|UserAccount|**nvarchar(256)**|Учетная запись, под которой выполняется служба рабочей роли горизонтального увеличения масштаба.|
|LastOnlineTime|**datetimeoffset(7)**|Время последнего подключения рабочей роли горизонтального увеличения масштаба.|

## <a name="remarks"></a>Remarks
В этом представлении отображается строка для каждой рабочей роли горизонтального увеличения масштаба, которая подключается к мастеру горизонтального увеличения масштаба, работающему с каталогом SSISDB.

## <a name="permissions"></a>Разрешения
Это представление требует применения одного из следующих разрешений:

- Членство в роли базы данных **ssis_admin**

- Членство в роли базы данных **ssis_cluster_executor**

- Членство в роли сервера **sysadmin**
