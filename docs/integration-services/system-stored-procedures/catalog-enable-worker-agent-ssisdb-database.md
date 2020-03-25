---
title: catalog.enable_worker_agent (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c6e5266b-c32d-49ff-aa69-f09664009fb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fd9d387d84836ca35c1b0bfb9fd564e2efd4a48
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71281026"
---
# <a name="catalogenable_worker_agent-ssisdb-database"></a>catalog.enable_worker_agent (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Включает рабочую роль Scale Out для мастера Scale Out, работающего с этим каталогом [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

## <a name="syntax"></a>Синтаксис

```sql
catalog.enable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>Аргументы
[@WorkerAgentId =] *WorkerAgentId* Идентификатор агента рабочей роли для рабочей роли Scale Out. Параметр *WorkerAgentId* имеет тип **uniqueidentifier**.

## <a name="example"></a>Пример
В этом примере рабочая роль горизонтального увеличения масштаба включается на компьютере MachineA.

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
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin** 

## <a name="errors-and-warnings"></a>Ошибки и предупреждения
Если идентификатор агента рабочей роли недействителен, хранимая процедура возвращает ошибку.
