---
title: sp_validate_redirected_publisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords:
- sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a38d4a197b5e86b41b8a7b791321d8a7ded7ab3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723028"
---
# <a name="sp_validate_redirected_publisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Проверяет, способен ли текущий экземпляр сервера для базы данных публикации поддерживать репликацию. Должна запускаться из базы данных распространителя. Эта процедура вызывается **sp_get_redirected_publisher**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @original_publisher = ] 'original_publisher'`Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который первоначально опубликовал базу данных. Аргумент *original_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя публикуемой базы данных. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'`Целевой объект перенаправления, указанный при вызове **sp_redirect_publisher** для пары "издатель — база данных". Аргумент *redirected_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Если для издателя и базы данных публикации не существует записи, **sp_validate_redirected_publisher** возвращает значение NULL в параметре OUTPUT * \@ redirected_publisher*. Если запись существует, происходит ее возврат в выходном параметре как в случае успеха, так и в случае неудачи.  
  
 Если проверка завершается успешно, **sp_validate_redirected_publisher** Возвращает индикатор успеха.  
  
 Если проверка завершается неудачно, формируются ошибки, описывающие неудачу.  
  
## <a name="permissions"></a>Разрешения  
 Участник должен быть членом предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа к публикации для определенной публикации, связанной с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
