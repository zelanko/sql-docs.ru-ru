---
title: sp_get_redirected_publisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 49bffb24c5ddc45c1c6b88fb424ab419445819fb
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529972"
---
# <a name="spgetredirectedpublisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Используется агентами репликация для запроса распространителя, чтобы определить, был ли перенаправлен первоначальный издатель.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @original_publisher = ] 'original_publisher'` Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @bypass_publisher_validation = ] [0 | 1 ]` Используется для пропуска проверки перенаправленного издателя. Если значение равно 0, выполняется проверка. Если значение равно 1, проверка не выполнена. *bypass_publisher_validation* — **бит**, значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|Имя издателя после перенаправления.|  
|**error_number**|**int**|Номер ошибки проверки.|  
|**error_severity**|**int**|Серьезность ошибки проверки.|  
|**error_message**|**nvarchar(4000)**|Текст сообщения ошибки проверки.|  
  
## <a name="remarks"></a>Примечания  
 *redirected_publisher* возвращает имя текущего издателя. Возвращает значение null, если издатель и базы данных публикации не могут быть перенаправлены с использованием **sp_redirect_publisher**.  
  
 Если проверка не запрошена или не существует запись для издателя и базы данных публикации, *error_number* и *error_severity* возвращают 0 и *error_message* Возвращает значение null.  
  
 Если проверка запрошена, хранимая процедура проверки [sp_validate_redirected_publisher &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md) вызывается, чтобы убедиться, что целью перенаправления является подходящий узел для публикации База данных. Если проверка прошла успешно, **sp_get_redirected_publisher** возвращает имя перенаправленного издателя, 0 для *error_number* и *error_severity* столбцов и значений null в *error_message* столбца.  
  
 Если проверка запрошена и завершилась неудачей, имя перенаправленного издателя возвращается вместе с информацией об ошибке.  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть либо членом **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа публикации для определенной публикации связанные с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
