---
title: "Catalog.add_execution_worker (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8ce83f2678a1f3dcae6539f33beb33070b8e771b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>Catalog.add_execution_worker (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Добавляет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы ожидания рабочий процесс, для экземпляра выполнения в масштабное развертывание.

## <a name="syntax"></a>Синтаксис

```tsql
add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Аргументы
[ @execution_id =] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. *Execution_id* — **bigint**.  
 
[@workeragent_id =] *workeragent_id*  
Идентификатор агента работника работника Out шкалы. *Workeragent_id* — **uniqueIdentifier**.

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и MODIFY на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
 
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
 
- Пользователь не имеет соответствующих разрешений.

- Недопустимый идентификатор выполнения.

- Недопустимый идентификатор агента работника.

- Выполнение не находится в масштабное развертывание.

## <a name="see-also"></a>См. также:
[Выполнение пакетов в масштабное развертывание](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).


