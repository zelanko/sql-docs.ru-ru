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
ms.openlocfilehash: f2678853d13436811b53b40473a04191625535db
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295137"
---
# <a name="catalogworker_agents-ssisdb-database"></a>catalog.worker_agents (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

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
