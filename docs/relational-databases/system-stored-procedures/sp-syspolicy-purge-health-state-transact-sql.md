---
title: sp_syspolicy_purge_health_state (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_purge_health_state_TSQL
- sp_syspolicy_purge_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_purge_health_state
ms.assetid: 4ba4aa91-4c19-41c7-b70d-5fd9d0e89a5e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9049340483674969a6ab4730d54794957c67aac9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67997318"
---
# <a name="sp_syspolicy_purge_health_state-transact-sql"></a>sp_syspolicy_purge_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет состояния работоспособности политик в управлении на основе политик. Состояния работоспособности политик — это визуальные индикаторы (символ прокрутки с красным знаком X) в обозревателе объектов, которые позволяют определить, для каких узлов не выполнена политика.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_purge_health_state [ @target_tree_root_with_id = ] 'target_tree_root_with_id'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @target_tree_root_with_id = ] 'target_tree_root_with_id'`Представляет узел в обозревателе объектов, в котором необходимо очистить состояние работоспособности. *target_tree_root_with_id* имеет тип **nvarchar (400)** и значение по умолчанию NULL.  
  
 Можно указывать значения из столбца target_query_expression_with_id системного представления msdb.dbo.syspolicy_system_health_state.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_syspolicy_purge_health_state должна выполняться в контексте системной базы данных msdb.  
  
 Если запустить эту хранимую процедуру, не указывая параметров, то состояние работоспособности системы будет удалено для всех узлов в обозревателе объектов.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможное повышение уровня учетных данных. пользователи в роли PolicyAdministratorRole могут создавать серверные триггеры и планировать выполнение политик, которые могут повлиять на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются состояния работоспособности для заданного узла в обозревателе объектов.  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_health_state @target_tree_root_with_id = 'Server/Database[@ID=7]';  
  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры управления на основе политик &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
