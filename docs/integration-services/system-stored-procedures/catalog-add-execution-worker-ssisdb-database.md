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
author: chugugrace
ms.author: chugu
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: c5c53af690df29c17012e19267debfe2273b4193
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71281389"
---
# <a name="catalogadd_execution_worker-ssisdb-database"></a>catalog.add_execution_worker (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
Идентификатор агента рабочей роли для рабочей роли горизонтального увеличения масштаба. Параметр *workeragent_id* имеет тип **uniqueIdentifier**.

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

- Выполнение не относится к развертыванию с горизонтальным увеличением масштаба.

## <a name="see-also"></a>См. также:
[Выполнение пакетов в масштабном развертывании](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

