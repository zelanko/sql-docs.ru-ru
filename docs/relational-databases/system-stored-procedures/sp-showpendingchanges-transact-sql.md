---
title: sp_showpendingchanges (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b09069cb5289e28d978a4f3b3483e14e63cebb2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73632748"
---
# <a name="sp_showpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор, который показывает изменения, ожидающие репликации. Эта хранимая процедура выполняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  Эта процедура предоставляет приблизительное число изменений и строк, затронутых этими изменениями. Например, процедура получает сведения из издателя или подписчика, но не из обоих одновременно. Данные, которые хранятся в другом узле, могут привести к меньшему набору измерений для синхронизации, чем было рассчитано процедурой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @destination_server = ] 'destination_server'`Имя сервера, на котором применяются реплицированные изменения. Аргумент *destination_server* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL. Если указан параметр *publication* , результаты ограничиваются только указанной публикацией.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и значение по умолчанию NULL. Если указана *статья* , результаты ограничиваются только указанной статьей.  
  
`[ @show_rows = ] 'show_rows'`Указывает, содержит ли результирующий набор более конкретные сведения о ожидающих изменениях, со значением по умолчанию **0**. Если указано значение **1** , то результирующий набор содержит столбцы is_delete и ROWGUID.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|Имя сервера, на который реплицируются изменения.|  
|pub_name|**sysname**|Имя публикации.|  
|destination_db_name|**sysname**|Название базы данных, к которой реплицируются изменения.|  
|is_dest_subscriber|**bit**|Свидетельствует об изменениях, реплицируемых на подписчика. Значение **1** указывает, что изменения реплицируются на подписчик. значение **0** означает, что изменения реплицируются на издатель.|  
|article_name|**sysname**|Название статьи для таблицы, где были произведены изменения.|  
|pending_deletes|**int**|Число удалений, ожидающих репликации.|  
|pending_ins_and_upd|**int**|Число вставок и обновлений, ожидающих репликации.|  
|is_delete|**bit**|Указывает, является ли ожидающее изменение удалением. Значение **1** указывает на то, что изменение является удалением. Требуется значение **1** в параметре @show_rows.|  
|rowguid|**uniqueidentifier**|Идентификатор GUID, который определяет измененную строку. Требуется значение **1** в параметре @show_rows.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_showpendingchanges используется при репликации слиянием.  
  
 Процедура sp_showpendingchanges используется при диагностике и устранении неполадок в репликации слиянием.  
  
 Результат выполнения процедуры sp_showpendingchanges не включает строки в поколении 0.  
  
 Если статья, указанная для *статьи* , не принадлежит публикации, указанной для *публикации,* то для pending_deletes и pending_ins_and_upd возвращается число 0.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner могут выполнять процедуру sp_showpendingchanges.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
