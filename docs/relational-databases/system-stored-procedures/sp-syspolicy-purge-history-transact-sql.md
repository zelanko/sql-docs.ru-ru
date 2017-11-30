---
title: "процедура sp_syspolicy_purge_history (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_purge_history_TSQL
- sp_syspolicy_purge_history
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_purge_history
ms.assetid: 6db414e7-4946-4bd2-8264-6b490810b306
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c2ced3e442d1b930e18e677e5e1961f19d3796ac
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicypurgehistory-transact-sql"></a>sp_syspolicy_purge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет журнал выполнения политик в соответствии с параметром интервала хранения журнала.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_purge_history  
```  
  
## <a name="arguments"></a>Аргументы  
 Данная хранимая процедура не имеет параметров.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_syspolicy_purge_history должна выполняться в контексте системной базы данных msdb.  
  
 Чтобы просмотреть интервал хранения журнала, можно использовать следующий запрос:  
  
```  
SELECT current_value  
FROM msdb.dbo.syspolicy_configuration  
WHERE name = N'HistoryRetentionInDays';  
GO  
```  
  
> [!NOTE]  
>  Если интервал хранения журнала имеет значение 0, журнал выполнения политик не будет удаляться.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможно повышение учетных данных: пользователи в роли PolicyAdministratorRole могут создавать триггеры сервера и планировать выполнение политик, влияющих на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется журнал выполнения политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_history;  
  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление на основе политик хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [процедура sp_syspolicy_set_config_history_retention &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [процедура sp_syspolicy_delete_policy_execution_history &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-execution-history-transact-sql.md)  
  
  
