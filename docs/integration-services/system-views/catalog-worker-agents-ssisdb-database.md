---
title: catalog.worker_agents (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 057d97572962ae13354d43abafe7d3016eafde7d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045152"
---
# <a name="catalogworkeragents-ssisdb-database"></a>catalog.worker_agents (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

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

## <a name="remarks"></a>Remarks
В этом представлении отображается строка для каждой рабочей роли Scale Out, которая подключается к мастеру Scale Out, работающему с каталогом SSISDB.

## <a name="permissions"></a>Разрешения
Это представление требует применения одного из следующих разрешений:

- Членство в роли базы данных **ssis_admin**

- Членство в роли базы данных **ssis_cluster_executor**

- Членство в роли сервера **sysadmin**
