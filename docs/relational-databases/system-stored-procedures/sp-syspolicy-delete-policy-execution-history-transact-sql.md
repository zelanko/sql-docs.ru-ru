---
title: процедура sp_syspolicy_delete_policy_execution_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6660eba76675fbe261af33f647d60456ced839d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63002283"
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет журнал выполнения для политик в управлении на основе политик. Эта хранимая процедура используется для удаления журнала выполнения для заданной политики или для всех политик, а также для удаления журнала выполнения до определенной даты.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @policy_id = ] policy_id` — Идентификатор политики, для которого вы хотите удалить журнал выполнения. *policy_id* — **int**и является обязательным. Может иметь значение NULL.  
  
`[ @oldest_date = ] 'oldest_date'` Самая ранняя дата, для которого вы хотите сохранить журнал выполнения политик. Все данные журнала выполнения до этой даты удаляются. *oldest_date* — **datetime**и является обязательным. Может иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_syspolicy_delete_policy_execution_history должна выполняться в контексте системной базы данных msdb.  
  
 Чтобы получить значения для *policy_id*, чтобы просмотреть данные журнала выполнения, можно использовать следующий запрос:  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 Если для одного или обоих параметров указано значение NULL, применяются следующие правила.  
  
-   Чтобы удалить весь журнал выполнения, укажите значение NULL для обоих *policy_id* и *oldest_date*.  
  
-   Чтобы удалить весь журнал выполнения для конкретной политики, укажите идентификатор политики в параметре *policy_id*, и значение NULL в *oldest_date*.  
  
-   Чтобы удалить журнал выполнения для всех политик до определенной даты, укажите значение NULL для *policy_id*и укажите дату для *oldest_date*.  
  
 Чтобы поместить журнал выполнения политик в архив, можно открыть журнал политик в обозревателе объектов и экспортировать журнал выполнения в файл. Чтобы открыть журнал политик, разверните **управления**, щелкните правой кнопкой мыши **Управление политиками**, а затем нажмите кнопку **Просмотр журнала**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможно повышение учетных данных: Пользователи с ролью PolicyAdministratorRole могут создавать триггеры сервера и планировать выполнение политик, влияющих на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется журнал выполнения для политики с идентификатором 7 до определенной даты.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры управления на основе политик &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [процедура sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [процедура sp_syspolicy_purge_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
