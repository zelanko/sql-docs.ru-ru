---
title: catalog.add_execution_worker (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
author: janinezhang
ms.author: janinez
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 84d1e12e873fe85d950a4ba4644f18a79278c641
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279674"
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Добавляет рабочую роль [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out в экземпляр выполнения в Scale Out.

## <a name="syntax"></a>Синтаксис

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Аргументы
[ @execution_id = ] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. Параметр *execution_id* имеет тип **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
Идентификатор агента рабочей роли для рабочей роли Scale Out. Параметр *workeragent_id* имеет тип **uniqueIdentifier**.

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и MODIFY на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
 
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
 
- Пользователь не имеет соответствующих разрешений.

- Недопустимый идентификатор выполнения.

- Недопустимый идентификатор агента рабочей роли.

- Выполнение не относится к Scale Out.

## <a name="see-also"></a>См. также:
[Выполнение пакетов в масштабном развертывании](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

