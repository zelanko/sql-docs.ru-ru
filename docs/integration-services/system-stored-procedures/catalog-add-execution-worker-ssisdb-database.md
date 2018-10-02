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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 826f1df93be48bfa5a7adf92f06811fa327cedf3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651311"
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

