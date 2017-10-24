---
title: "Catalog.enable_worker_agent (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6e5266b-c32d-49ff-aa69-f09664009fb4
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3eb3f21b6a686c3013cdaaa3000038896edfbf94
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogenableworkeragent-ssisdb-database"></a>Catalog.enable_worker_agent (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Включить шкалы ожидания рабочий процесс для масштабирования ожидания базы данных Master работу с этим [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] каталога.

## <a name="syntax"></a>Синтаксис

```sql
catalog.enable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>Аргументы
[@WorkerAgentId =] *WorkerAgentId* агента работника идентификатор из шкалы Out рабочих. *WorkerAgentId* — **uniqueidentifier**.

## <a name="example"></a>Пример
В этом примере рабочая роль масштабного развертывания включается на компьютере MachineA.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
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
Если идентификатор работника агента не является допустимым, хранимая процедура возвращает ошибку.

