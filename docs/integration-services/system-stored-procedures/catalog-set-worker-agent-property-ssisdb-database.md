---
description: catalog.set_worker_agent_property (база данных SSISDB)
title: catalog.set_worker_agent_property (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5981431210ba98c950b56b7621f3f9cc50586c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422118"
---
# <a name="catalogset_worker_agent_property-ssisdb-database"></a>catalog.set_worker_agent_property (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Задает свойство рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

## <a name="syntax"></a>Синтаксис

```sql
catalog.set_worker_agent_property [ @WorkerAgentId = ] WorkerAgentId
    , [ @PropertyName = ] PropertyName
    , [ @PropertyValue = ] PropertyValue 
```

## <a name="arguments"></a>Аргументы
[@WorkerAgentId =] *WorkerAgentId*  
Идентификатор агента рабочей роли для рабочей роли Scale Out. Параметр *WorkerAgentId* имеет тип **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Имя свойства. Параметр *PropertyName* имеет тип **nvarchar(256)**.

[@PropertyValue =] *PropertyValue*  
Значение свойства. Параметр *PropertyValue* имеет тип **nvarchar(max)** .

## <a name="remarks"></a>Примечания
Допустимыми именами свойств являются **DisplayName**, **Description**, **Tags**.

## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**

## <a name="errors-and-warnings"></a>Ошибки и предупреждения
  Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений 

-   Недопустимый идентификатор агента рабочей роли.

-   Недопустимое имя свойства.

-   Недопустимое значение свойства.  
