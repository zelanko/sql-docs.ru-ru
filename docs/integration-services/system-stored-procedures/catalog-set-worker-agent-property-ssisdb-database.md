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
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d0476bbb67cff44a05aed1441a31d679882b4cb3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>Catalog.set_worker_agent_property (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Задает свойство [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы Out работника.

## <a name="syntax"></a>Синтаксис

```tsql
set_worker_agent_property [ @WorkerAgentId = ] WorkerAgentId, [ @PropertyName = ] PropertyName, [ @PropertyValue = ] PropertyValue 
```

## <a name="arguments"></a>Аргументы
[ @WorkerAgentId =] *WorkerAgentId*  
Идентификатор агента работника шкалы ожидания рабочего процесса. *WorkerAgentId* — **uniqueidentifier**.

[ @PropertyName =] *PropertyName*  
Имя свойства. *PropertyName* — **nvarchar(256)**.

[ @PropertyValue =] *PropertyValue*  
Значение свойства. *PropertyValue* — **nvarchar(max)**.

## <a name="remarks"></a>Замечания
Допустимые имена свойств **DisplayName**, **описание**, **теги**.

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера

## <a name="erros-and-warnings"></a>Erros и предупреждения
  Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений 

-   Недопустимый идентификатор агента работника.

-   Недопустимое имя свойства.

-   Значение свойства не vilid.  
