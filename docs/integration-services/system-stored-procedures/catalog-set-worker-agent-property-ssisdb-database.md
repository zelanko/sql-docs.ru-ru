---
title: catalog.set_worker_agent_property (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 986807ab07a563fef1ae8a9231db194a4a5943e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038675"
---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Задает свойство рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

## <a name="syntax"></a>Синтаксис

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Аргументы
[@WorkerAgentId =] *WorkerAgentId*  
Идентификатор агента рабочей роли для рабочей роли Scale Out. Параметр *WorkerAgentId* имеет тип **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Имя свойства. Параметр *PropertyName* имеет тип **nvarchar(256)** .

[@PropertyValue =] *PropertyValue*  
Значение свойства. Параметр *PropertyValue* имеет тип **nvarchar(max)** .

## <a name="remarks"></a>Remarks
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
