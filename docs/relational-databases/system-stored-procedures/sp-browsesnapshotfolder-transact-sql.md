---
title: sp_browsesnapshotfolder (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2ace8d02997b7c0647be0b7abe26ff098849905
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494006"
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает полный путь к последнему моментальному снимку, созданному для данной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, которая содержит статью. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Полный путь к каталогу моментальных снимков.|  
  
## <a name="remarks"></a>Примечания  
 **sp_browsesnapshotfolder** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если *подписчика* и *subscriber_db* поля содержат значение NULL, хранимая процедура возвращает последний моментальный снимок для публикации его можно найти папку с моментальным снимком. Если *подписчика* и *subscriber_db* поля указаны, хранимая процедура возвращает папки моментальных снимков для указанной подписки. Если для данной публикации не был создан моментальный снимок, то возвращается пустой результирующий набор.  
  
 Если публикация настроена так, что моментальные снимки создаются и в рабочем каталоге издателя, и в папке моментальных снимков, то результирующий набор состоит из двух строк. Первая строка содержит папку моментальных снимков публикации, а вторая — рабочий каталог издателя. **sp_browsesnapshotfolder** полезно для определения каталога, в котором формируются файлы моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_browsesnapshotfolder**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
