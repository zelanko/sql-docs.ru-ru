---
title: sp_audit_write (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5c387759745c7fa2776f202d29c3214125417813
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spauditwrite-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет событие определяемой пользователем аудита **USER_DEFINED_AUDIT_GROUP**. Если **USER_DEFINED_AUDIT_GROUP** не включена, **sp_audit_write** учитывается.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_audit_write [ @user_defined_event_id =  ] user_defined_event_id ,   
        [ @succeeded =  succeeded   
    [ , [ @user_defined_information =  ] 'user_defined_information' ]   
    [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **@user_defined_event_id**  
 Определяемый пользователем параметр, записываются в **user_defined_event_id** столбца журнала аудита. *@user_defined_event_id* Тип **smallint**.  
  
 **@succeeded**  
 Параметр, переданный пользователем с целью указания, было ли событие успешным или нет. Содержится в столбце успеха журнала аудита. *@succeeded* — **бит**.  
  
 **@user_defined_information**  
 Определяемый пользователем текст, который заносится в новый столбец user_defined_event_id журнала аудита. *@user_defined_information* — **nvarchar(4000)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
 Ошибки вызваны неверными входными параметрами или ошибкой записи в целевой журнал аудита.  
  
## <a name="remarks"></a>Замечания  
 Когда **USER_DEFINED_AUDIT_GROUP** добавляется в спецификацию аудита сервера или спецификацию аудита базы данных, событие, вызванное **sp_audit_write** будут включены в журнал аудита.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **открытый** роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>A. Создание пользовательского события аудита с информативным текстом  
 В следующем примере создается событие аудита с идентификатором 27, успешным значением 0, включающее дополнительный информативный текст.  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>Б.  Создание пользовательского события аудита без информативного текста  
 В следующем примере создается событие аудита с идентификатором 27, успешным значением 0, не содержащее дополнительный информативный текст.  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
