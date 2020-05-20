---
title: sp_audit_write (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba751e5872f4f6fa4973674170d54a0dbc75f75a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833435"
---
# <a name="sp_audit_write-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет определенное пользователем событие аудита в **USER_DEFINED_AUDIT_GROUP**. Если **USER_DEFINED_AUDIT_GROUP** не включено, **sp_audit_write** игнорируется.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_audit_write [ @user_defined_event_id = ] user_defined_event_id
    [ , [ @succeeded = ] succeeded ]
    [ , [ @user_defined_information = ] 'user_defined_information' ]
    [ ; ]
```  
  
## <a name="arguments"></a>Аргументы  
 `[ @user_defined_event_id = ] user_defined_event_id`  
 Параметр, определяемый пользователем и записываемый в столбец **user_defined_event_id** журнала аудита. * \@ user_defined_event_id* имеет тип **smallint**.  
  
 `[ @succeeded = ] succeeded`  
 Параметр, переданный пользователем с целью указания, было ли событие успешным или нет. Содержится в столбце успеха журнала аудита. `@succeeded`**бит**.  
  
 `[ @user_defined_information = ] 'user_defined_information'`  
 Определяемый пользователем текст, который заносится в новый столбец user_defined_event_id журнала аудита. `@user_defined_information`имеет тип **nvarchar (4000)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
 Ошибки вызваны неверными входными параметрами или ошибкой записи в целевой журнал аудита.  
  
## <a name="remarks"></a>Remarks  
 Когда **USER_DEFINED_AUDIT_GROUP** добавляется в спецификацию аудита сервера или в спецификацию аудита базы данных, событие, запускаемое **sp_audit_write** , будет включено в журнал аудита.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **Public** .  
  
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
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [Создание ПОЛЬЗОВАТЕЛЬСКОГО &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
