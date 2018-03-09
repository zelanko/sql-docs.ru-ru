---
title: "процедура sp_showpendingchanges (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a80816191ac9ad2cd9a210c59268b23f4ea3a093
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
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
 [ @destination_server  **=**  ] **"***destination_server***"**  
 Имя сервера, на котором применяются реплицированные изменения. *destination_server* — **sysname**, и значение по умолчанию NULL.  
  
 [ @publication  **=**  ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию NULL. Когда *публикации* указан, результаты ограничены только указанной публикацией.  
  
 [ @article  **=**  ] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, значение по умолчанию NULL. Когда *статьи* указан, результаты ограничены только указанной статьи.  
  
 [ @show_rows  **=**  ] *show_rows*  
 Указывает, содержит ли результирующий набор более конкретные сведения об ожидающих изменениях со значением по умолчанию **0**. Если значение **1** указан, то результирующий набор содержит столбцы is_delete и rowguid.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|Имя сервера, на который реплицируются изменения.|  
|pub_name|**sysname**|Имя публикации.|  
|destination_db_name|**sysname**|Название базы данных, к которой реплицируются изменения.|  
|is_dest_subscriber|**bit**|Свидетельствует об изменениях, реплицируемых на подписчика. Значение **1** указывает, что изменения реплицируются на подписчик. **0** означает, что изменения реплицируются на издателя.|  
|article_name|**sysname**|Название статьи для таблицы, где были произведены изменения.|  
|pending_deletes|**int**|Число удалений, ожидающих репликации.|  
|pending_ins_and_upd|**int**|Число вставок и обновлений, ожидающих репликации.|  
|is_delete|**bit**|Указывает, является ли ожидающее изменение удалением. Значение **1** указывает, что изменение является удалением. Должно иметь значение **1** для @show_rows.|  
|rowguid|**uniqueidentifier**|Идентификатор GUID, который определяет измененную строку. Должно иметь значение **1** для @show_rows.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_showpendingchanges используется при репликации слиянием.  
  
 Процедура sp_showpendingchanges используется при диагностике и устранении неполадок в репликации слиянием.  
  
 Результат выполнения процедуры sp_showpendingchanges не включает строки в поколении 0.  
  
 Если статья, указанная для *статьи* не принадлежит к публикации, указанной в *публикации,* возвращаются при значении 0 для pending_deletes и pending_ins_and_upd.  
  
## <a name="permissions"></a>Permissions  
 Только члены предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner могут выполнять процедуру sp_showpendingchanges.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
