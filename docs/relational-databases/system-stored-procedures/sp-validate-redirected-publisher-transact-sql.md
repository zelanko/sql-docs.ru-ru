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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56e490fa3a860b3fc4e18e72d674c70d29130f5b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527306"
---
# <a name="spvalidateredirectedpublisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
`[ @original_publisher = ] 'original_publisher'` Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , первоначально опубликовавшего базу данных. *original_publisher* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` Цель перенаправления указываться, если **sp_redirect_publisher** был вызван для пары «издатель/база данных». *redirected_publisher* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Если не существует запись для издателя и базы данных публикации, **sp_validate_redirected_publisher** возвращает значение null в выходном параметре *@redirected_publisher*. Если запись существует, происходит ее возврат в выходном параметре как в случае успеха, так и в случае неудачи.  
  
 Если проверка прошла успешно, **sp_validate_redirected_publisher** Возвращает указание на успех.  
  
 Если проверка завершается неудачно, формируются ошибки, описывающие неудачу.  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть либо членом **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа публикации для определенной публикации связанные с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
