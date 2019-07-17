---
title: sp_redirect_publisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
author: stevestein
ms.author: sstein
ms.openlocfilehash: cde6f00d16bcff4ee56513f515cf2ecac93a1b5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002511"
---
# <a name="spredirectpublisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Указывает перенаправленного издателя для существующей пары «издатель/база данных». Если база данных издателя принадлежит к группе доступности AlwaysOn, перенаправленный издатель — имя прослушивателя группы доступности, связанное с группой доступности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @original_publisher = ] 'original_publisher'` Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , первоначально опубликовавшего базу данных. *original_publisher* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` Имя прослушивателя доступности группы, связанное с группой доступности, который будет новым издателем. *redirected_publisher* — **sysname**, не имеет значения по умолчанию. Когда прослушивателю группы доступности задан порт, отличный от порта по умолчанию, указывайте номер порта вместе с именем прослушивателя, например `'Listenername,51433'`  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_redirect_publisher** используется для разрешения является издателем репликации перенаправляться в текущей первичной группы доступности AlwaysOn, связав пару издатель/база данных с помощью прослушивателя группы доступности. Выполнение **sp_redirect_publisher** после настройки прослушивателя группы Доступности для группы доступности, которая содержит опубликованную базу данных.  
  
 Если базе данных публикации на первоначальном издателе удаляется из группы доступности на первичной реплике, выполнение **sp_redirect_publisher** без указания значения для *@redirected_publisher* параметр, чтобы удалить перенаправление для пары «издатель/база данных». Дополнительные сведения о перенаправлении издателя, см. в разделе [обслуживание базы данных публикации AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть либо членом **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа публикации для определенной публикации связанные с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
