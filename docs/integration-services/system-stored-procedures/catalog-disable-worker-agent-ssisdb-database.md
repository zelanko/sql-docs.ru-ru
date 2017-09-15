---
title: "Catalog.disable_worker_agent (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: aab83dd2f179c8e6b90ad9ff7a212597a51038de
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="catalogdisableworkeragent-ssisdb-database"></a>Catalog.disable_worker_agent (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отключить работника Out масштабирования для масштабирования Out Master работу с этим [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] каталога.

## <a name="syntax"></a>Синтаксис

```tsql
disable_worker_agent [@WorkerAgentId = ] WorkerAgentId
```
## <a name="arguments"></a>Аргументы
[ @WorkerAgentId =] *WorkerAgentId* идентификатор работника агента масштабирования ожидания рабочего процесса. *WorkerAgentId* — **uniqueidentifier**.

## <a name="example"></a>Пример
В этом примере отключается работника Out шкалы на неисправного.
```tsql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера 

## <a name="errors-and-warnings"></a>Ошибки и предупреждения
Хранимая процедура возвращает ошибку, если идентификатор работника агента не является допустимым.

