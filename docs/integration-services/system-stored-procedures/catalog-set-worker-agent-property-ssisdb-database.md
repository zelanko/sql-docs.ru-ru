---
title: "Catalog.set_worker_agent_property (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: c1caf4a71e5802968d9471711b8206a26f9c28d5
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>Catalog.set_worker_agent_property (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Задает свойство [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы Out работника.

## <a name="syntax"></a>Синтаксис

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Аргументы
[@WorkerAgentId =] *WorkerAgentId*  
Агент рабочий идентификатор из шкалы Out работника. *WorkerAgentId* — **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Имя свойства. *PropertyName* — **nvarchar(256)**.

[@PropertyValue =] *PropertyValue*  
Значение свойства. *PropertyValue* — **nvarchar(max)**.

## <a name="remarks"></a>Замечания
Допустимые имена свойств являются **DisplayName**, **описание**, **теги**.

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера

## <a name="errors-and-warnings"></a>Ошибки и предупреждения
  Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений 

-   Недопустимый идентификатор агента работника.

-   Недопустимое имя свойства.

-   Недопустимое значение свойства.  

