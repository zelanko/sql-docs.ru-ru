---
title: sp_help_publication_access (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 803b5d26fa2294a9e53d3afb597a232384dfd38d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036189"
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, к которой осуществляется обращение. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@return_granted=**] **"***return_granted***"**  
 Идентификатор входа. *return_granted* — **бит**, значение по умолчанию 1. Если **0** указан и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется проверка подлинности, возвращаются доступные имена входа, которые отображаются на издателе, но не на распространителе. Если **0** указывается и используется проверка подлинности Windows, имена входа, не специально отказано в доступе на издателе или распространителе возвращаются.  
  
 [  **@login=**] **"***входа***"**  
 Идентификатор стандартного защищенного имени входа. *Имя входа* — **sysname**, значение по умолчанию **%**.  
  
 [  **@initial_list =**] *initial_list*  
 Указывает, должен ли быть возвращен список всех элементов с правом доступа к публикации или только тех из них, которые имели право доступа до того, как были добавлены к списку новые элементы. *initial_list* имеет тип bit и значение по умолчанию **0**.  
  
 **1** возвращает сведения обо всех членах **sysadmin** предопределенной роли сервера с действительными именами входа на распространителе, которые существовали на момент создания публикации, а также текущего имени входа.  
  
 **0** возвращает сведения обо всех членах **sysadmin** предопределенной роли сервера с действительными именами входа на распространителе, которые существовали на момент создания публикации также обо всех пользователях в списке доступа к публикации, которые не принадлежит **sysadmin** предопределенной роли сервера.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**nvarchar(256)**|Фактическое имя входа.|  
|**Isntname**|**int**|**0** = имя входа не является пользователем Windows.<br /><br /> **1** = имя входа принадлежит пользователю Windows.|  
|**Isntgroup**|**int**|**0** = имя входа не является группой Windows.<br /><br /> **1** = имя входа принадлежит группе Windows.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_help_publication_access** используется во всех типах репликации.  
  
 Когда оба **Isntname** и **Isntgroup** в результирующий набор, **0**, предполагается, что имя входа является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_help_publication_access**.  
  
## <a name="see-also"></a>См. также  
 [sp_grant_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
