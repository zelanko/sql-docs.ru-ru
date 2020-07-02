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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1f07445d119174ca441e7ed13be1851a6e2f058
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771487"
---
# <a name="sp_changemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'`Текущее имя фильтра. *filtername* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @property = ] 'property'`Имя изменяемого свойства. Аргумент *Property* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @value = ] 'value'`Новое значение для указанного свойства. *value*имеет тип **nvarchar (1000)** и не имеет значения по умолчанию.  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|Свойство.|Применение|Описание|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Фильтр соединения.<br /><br /> Этот параметр необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Связь логических записей.|  
||**3**|Фильтр соединения также является связью логических записей.|  
|**filtername**||Имя фильтра.|  
|**join_articlename**||Имя статьи соединения.|  
|**join_filterclause**||Предложение фильтра.|  
|**join_unique_key**|**true**|Соединение находится в уникальном ключе.|  
||**false**|Соединение не находится в уникальном ключе.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье слияния не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 **1** означает, что изменения в статье слияния могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. *force_reinit_subscription* является **битом** со значением по умолчанию **0**.  
  
 **0** указывает, что изменения в статье слияния не приводят к повторной инициализации подписки. Если хранимая процедура определяет, что изменения потребуют повторной инициализации подписок, возникает ошибка, и изменения не выполняются.  
  
 **1** означает, что изменения в статье слияния приведут к повторной инициализации существующих подписок и предоставляют разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_changemergefilter** используется в репликации слиянием.  
  
 Изменения фильтра для статьи слияния требует создания моментального снимка; если таковой уже существует, необходимо его повторное создание. Это выполняется путем установки ** \@ force_invalidate_snapshot** в значение **1**. Кроме того, если на статью имеются подписки, то необходима их повторная инициализация. Это можно сделать, задав для ** \@ force_reinit_subscription** значение **1**.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changemergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
