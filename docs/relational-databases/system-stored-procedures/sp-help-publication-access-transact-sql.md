---
title: sp_help_publication_access (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7c562c039b65f99f1d3d9915f0dd00b93dc95860
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68770993"
---
# <a name="sp_help_publication_access-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает список всех предоставленных имен входа для публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, к которой осуществляется доступ. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @return_granted = ] 'return_granted'`Идентификатор входа. *return_granted* имеет **бит**и значение по умолчанию 1. Если указано значение **0** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется проверка подлинности, то возвращаются доступные имена входа, которые отображаются на издателе, но не на распространителе. Если указано значение **0** и используется проверка подлинности Windows, то возвращаются имена входа, не запрещающие доступ на издателе или распространителе.  
  
`[ @login = ] 'login'`— Это идентификатор стандартной учетной записи безопасности. Аргумент *Login* имеет тип **sysname**и значение по **%** умолчанию.  
  
`[ @initial_list = ] initial_list`Указывает, следует ли возвращать всех членов с доступом к публикации или только тем, кто имел доступ до добавления новых участников в список. *initial_list* имеет бит и значение по умолчанию **0**.  
  
 **1** возвращает сведения для всех членов предопределенной роли сервера **sysadmin** с действительными именами входа на распространителе, существовавшими при создании публикации, а также с текущим именем входа.  
  
 **0** возвращает сведения обо всех членах предопределенной роли сервера **sysadmin** с допустимыми именами входа на распространителе, существовавшими при создании публикации, а также всех пользователей в списке доступа к публикации, которые не принадлежат предопределенной роли сервера **sysadmin** .  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**nvarchar(256)**|Фактическое имя входа.|  
|**иснтнаме**|**int**|**0** = имя входа не является пользователем Windows.<br /><br /> **1** = имя входа является пользователем Windows.|  
|**Isntgroup**|**int**|**0** = имя входа не является группой Windows.<br /><br /> **1** = имя входа является группой Windows.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_help_publication_access** используется во всех типах репликации.  
  
 Если оба **иснтнаме** и **иснтграуп** в результирующем наборе равны **0**, предполагается, что имя входа является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именем входа.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_help_publication_access**.  
  
## <a name="see-also"></a>См. также:  
 [sp_grant_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
