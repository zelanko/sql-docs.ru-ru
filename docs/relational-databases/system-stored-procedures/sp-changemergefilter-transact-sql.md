---
title: sp_changemergefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0c38af1089a1d59c9964e39aecca6b1773a8e22
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124885"
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет некоторые свойства фильтра слияния. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'` — Это имя текущего фильтра. *FilterName* — **sysname**, не имеет значения по умолчанию.  
  
`[ @property = ] 'property'` — Имя свойства, которое необходимо изменить. *Свойство* — **sysname**, не имеет значения по умолчанию.  
  
`[ @value = ] 'value'` — Это новое значение для указанного свойства. *значение*— **nvarchar(1000)** , не имеет значения по умолчанию.  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Фильтр соединения.<br /><br /> Этот параметр необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Связь логических записей.|  
||**3**|Фильтр соединения также является связью логических записей.|  
|**FilterName**||Имя фильтра.|  
|**join_articlename**||Имя статьи соединения.|  
|**join_filterclause**||Предложение фильтра.|  
|**join_unique_key**|**true**|Соединение находится в уникальном ключе.|  
||**false**|Соединение не находится в уникальном ключе.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 **1** означает, что изменения статьи слияния могут привести к недействительности моментального снимка, и если существующие подписки потребуют нового моментального снимка, дает разрешение существующий моментальный снимок помечается как устаревшего и создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит** значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приводят к повторной инициализации подписки. Если хранимая процедура определяет, что изменения потребуют повторной инициализации подписок, возникает ошибка, и изменения не выполняются.  
  
 **1** означает, что изменения статьи слияния приведет к повторной инициализации текущих подписок и дает разрешение произвести повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changemergefilter** используется в репликации слиянием.  
  
 Изменения фильтра для статьи слияния требует создания моментального снимка; если таковой уже существует, необходимо его повторное создание. Это выполняется путем задания **@force_invalidate_snapshot** для **1**. Кроме того, если на статью имеются подписки, то необходима их повторная инициализация. Это сделать, задав **@force_reinit_subscription** для **1**.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_changemergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
