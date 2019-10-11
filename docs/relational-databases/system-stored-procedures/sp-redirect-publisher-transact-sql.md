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
ms.openlocfilehash: 6062522ca6c5c3a311ba2f2c796f791c47e874ab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252114"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Указывает перенаправленного издателя для существующей пары «издатель/база данных». Если база данных издателя принадлежит к Always On группе доступности, перенаправленный издатель является именем прослушивателя группы доступности, связанным с группой доступности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @original_publisher = ] 'original_publisher'` имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который первоначально опубликовал базу данных. *original_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` имя публикуемой базы данных. *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` — имя прослушивателя группы доступности, связанного с группой доступности, который будет новым издателем. *redirected_publisher* имеет тип **sysname**и не имеет значения по умолчанию. Когда прослушивателю группы доступности задан порт, отличный от порта по умолчанию, указывайте номер порта вместе с именем прослушивателя, например `'Listenername,51433'`  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_redirect_publisher** используется, чтобы разрешить перенаправление издателя репликации в текущий первичный объект группы доступности Always on, связав пару издателя и базы данных с прослушивателем группы доступности. Выполните **sp_redirect_publisher** после настройки прослушивателя AG для группы доступности, содержащей опубликованную базу данных.  
  
 Если база данных публикации на исходном издателе удаляется из группы доступности на первичной реплике, выполните **sp_redirect_publisher** без указания значения для параметра *\@redirected_publisher* , чтобы удалить перенаправление для пары "издатель — база данных". Дополнительные сведения о перенаправлении издателя в см. в разделе [обслуживание базы данных &#40;&#41;публикации AlwaysOn SQL Server](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Участник должен быть членом предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** для базы данных распространителя или членом списка доступа к публикации для определенной публикации, связанной с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
