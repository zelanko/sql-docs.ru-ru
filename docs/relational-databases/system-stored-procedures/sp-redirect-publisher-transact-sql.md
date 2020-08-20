---
description: sp_redirect_publisher (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b3a2a07d2b1ca9d8b6d8cd35d3cf2361c50e36b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464088"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @original_publisher = ] 'original_publisher'` Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который первоначально опубликовал базу данных. Аргумент *original_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя публикуемой базы данных. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` Имя прослушивателя группы доступности, связанное с группой доступности, которое будет новым издателем. Аргумент *redirected_publisher* имеет тип **sysname**и не имеет значения по умолчанию. Когда прослушивателю группы доступности задан порт, отличный от порта по умолчанию, указывайте номер порта вместе с именем прослушивателя, например `'Listenername,51433'`  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_redirect_publisher** используется, чтобы разрешить перенаправление издателя репликации на текущий первичный ресурс группы доступности Always on, связав пару издателя и базы данных с прослушивателем группы доступности. Выполните **sp_redirect_publisher** после настройки прослушивателя AG для группы доступности, содержащей опубликованную базу данных.  
  
 Если база данных публикации на исходном издателе удаляется из группы доступности на первичной реплике, выполните **sp_redirect_publisher** без указания значения параметра * \@ redirected_publisher* , чтобы удалить перенаправление для пары "издатель — база данных". Дополнительные сведения о перенаправлении издателя в см. в разделе [обслуживание базы данных публикации AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Участник должен быть членом предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа к публикации для определенной публикации, связанной с базой данных издателя.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
