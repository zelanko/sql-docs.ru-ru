---
title: sp_changemergefilter (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 52694eb358be44c4e798f49daa6e7b4aa83d009d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article=** ] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@filtername=** ] **"***filtername***"**  
 Текущее имя фильтра. *FilterName* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@property=** ] **"***свойство***"**  
 Имя свойства, которое необходимо изменить. *Свойство* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@value=**] **"***значение***"**  
 Новое значение для указанного свойства. *значение*— **nvarchar(1000)**, не имеет значения по умолчанию.  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|property|Значение|Описание|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Фильтр соединения.<br /><br /> Этот параметр необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Связь логических записей.|  
||**3**|Фильтр соединения также является связью логических записей.|  
|**FilterName**||Имя фильтра.|  
|**join_articlename**||Имя статьи соединения.|  
|**join_filterclause**||Предложение фильтра.|  
|**join_unique_key**|**true**|Соединение находится в уникальном ключе.|  
||**false**|Соединение не находится в уникальном ключе.|  
  
 [  **@force_invalidate_snapshot =** ] *подписки потребуют*  
 Подтверждает, что действие, выполненное этой хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 **1** означает, что изменения статьи слияния могут привести к недействительности моментального снимка, и если существующие подписки потребуют нового моментального снимка, дает разрешение существующий моментальный снимок помечается как устаревшего и создание нового моментального снимка.  
  
 [  **@force_reinit_subscription =** ] *этот*  
 Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит** значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не вызывают повторной инициализации подписки. Если хранимая процедура определяет, что изменения потребуют повторной инициализации подписок, возникает ошибка, и изменения не выполняются.  
  
 **1** означает, что изменения в статье слияния приведут повторную инициализацию подписок и дает разрешение произвести повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changemergefilter** используется в репликации слиянием.  
  
 Изменения фильтра для статьи слияния требует создания моментального снимка; если таковой уже существует, необходимо его повторное создание. Это выполняется путем задания **@force_invalidate_snapshot** для **1**. Кроме того, если на статью имеются подписки, то необходима их повторная инициализация. Это можно сделать, настроив **@force_reinit_subscription** для **1**.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_changemergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Хранимая процедура sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
