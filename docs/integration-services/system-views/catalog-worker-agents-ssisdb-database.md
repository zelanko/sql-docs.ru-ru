---
title: "Catalog.worker_agents (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d56af0ab150255c53746898a638a32112938755c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="catalogworkeragents-ssisdb-database"></a>Catalog.worker_agents (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает сведения по [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы Out работника.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|Агент рабочий идентификатор из шкалы Out работника.|
|IsEnabled|**bit**|Указывает, включена ли работник Out шкалы.|
|DisplayName|**nvarchar(256)**|Отображаемое имя шкалы ожидания рабочего процесса.|
|Description|**nvarchar(256)**|Описание масштабирования ожидания рабочего процесса.|
|MachineName|**nvarchar(256)**|Имя компьютера, для масштабирования ожидания рабочего процесса.|
|Теги|**nvarchar(max)**|Теги шкалы ожидания рабочего процесса.|
|Имя_учетной_записи|**nvarchar(256)**|Учетная запись пользователя, со службой шкалы Out работника.|
|LastOnlineTime|**DateTimeOffset(7)**|Время последнего работника Out шкалы находится в оперативном режиме.|

## <a name="remarks"></a>Замечания
В этом представлении отображается строка для каждого работника шкалы ожидания, который соединиться шкалы Out главного работа с каталогом SSISDB.

## <a name="permissions"></a>Permissions
Это представление требует применения одного из следующих разрешений:

- Членство в **ssis_admin** роли базы данных

- Членство в **ssis_cluster_executor** роли базы данных

- Членство в **sysadmin** роли сервера

