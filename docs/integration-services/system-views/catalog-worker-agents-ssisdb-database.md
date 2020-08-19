---
description: catalog.worker_agents (база данных SSISDB)
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
ms.openlocfilehash: 9048a56959de62791b0f952aff086ae513098be2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421948"
---
# <a name="catalogworker_agents-ssisdb-database"></a>catalog.worker_agents (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Отображает сведения для рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|Идентификатор агента рабочей роли для рабочей роли Scale Out.|
|IsEnabled|**bit**|Указывает, включена ли рабочая роль Scale Out.|
|DisplayName|**nvarchar(256)**|Отображаемое имя рабочей роли Scale Out.|
|Описание|**nvarchar(256)**|Описание рабочей роли Scale Out.|
|MachineName|**nvarchar(256)**|Имя компьютера рабочей роли Scale Out.|
|Теги|**nvarchar(max)**|Теги рабочей роли Scale Out.|
|UserAccount|**nvarchar(256)**|Учетная запись, под которой выполняется служба рабочей роли Scale Out.|
|LastOnlineTime|**datetimeoffset(7)**|Время последнего подключения рабочей роли Scale Out.|

## <a name="remarks"></a>Комментарии
В этом представлении отображается строка для каждой рабочей роли Scale Out, которая подключается к мастеру Scale Out, работающему с каталогом SSISDB.

## <a name="permissions"></a>Разрешения
Это представление требует применения одного из следующих разрешений:

- Членство в роли базы данных **ssis_admin**

- Членство в роли базы данных **ssis_cluster_executor**

- Членство в роли сервера **sysadmin**
