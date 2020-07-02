---
title: sp_syspolicy_delete_policy_execution_history (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 276ad7c1fd04b377dd71daf7e0f15298dd8c80e3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773811"
---
# <a name="sp_syspolicy_delete_policy_execution_history-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Удаляет журнал выполнения для политик в управлении на основе политик. Эта хранимая процедура используется для удаления журнала выполнения для заданной политики или для всех политик, а также для удаления журнала выполнения до определенной даты.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @policy_id = ] policy_id`Идентификатор политики, для которой необходимо удалить журнал выполнения. *policy_id* имеет **тип int**и является обязательным. Может иметь значение NULL.  
  
`[ @oldest_date = ] 'oldest_date'`Самая старая Дата, для которой необходимо синхронизировать журнал выполнения политик. Все данные журнала выполнения до этой даты удаляются. *oldest_date* имеет тип **DateTime**и является обязательным. Может иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_syspolicy_delete_policy_execution_history должна выполняться в контексте системной базы данных msdb.  
  
 Чтобы получить значения для *policy_id*, а также для просмотра дат журнала выполнения, можно использовать следующий запрос:  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 Если для одного или обоих параметров указано значение NULL, применяются следующие правила.  
  
-   Чтобы удалить весь журнал выполнения политики, укажите значение NULL как для *policy_id* , так и для *oldest_date*.  
  
-   Чтобы удалить все журналы выполнения политик для конкретной политики, укажите идентификатор политики для *policy_id*и укажите значение NULL в качестве *oldest_date*.  
  
-   Чтобы удалить журнал выполнения политики для всех политик до определенной даты, укажите значение NULL для *policy_id*и укажите дату для *oldest_date*.  
  
 Чтобы поместить журнал выполнения политик в архив, можно открыть журнал политик в обозревателе объектов и экспортировать журнал выполнения в файл. Чтобы получить доступ к журналу политики, разверните узел **Управление**, щелкните правой кнопкой мыши элемент **Управление политиками**и выберите пункт **Просмотр журнала**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможное повышение уровня учетных данных. пользователи в роли PolicyAdministratorRole могут создавать серверные триггеры и планировать выполнение политик, которые могут повлиять на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется журнал выполнения для политики с идентификатором 7 до определенной даты.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры управления на основе политик &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
