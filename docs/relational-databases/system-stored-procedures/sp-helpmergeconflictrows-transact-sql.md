---
title: sp_helpmergeconflictrows (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1de46c12b0e05b592489e557a80138996ad9767f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528796"
---
# <a name="sphelpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строки в указанной таблице конфликтов. Эта хранимая процедура выполняется на том компьютере, где хранится таблица конфликтов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%**. Если указана публикация, возвращаются все конфликты, определенные этой публикацией. Например если **MSmerge_conflict_Customers** таблица имеет конфликтующие строки для **WA** и **ЦС** публикаций, передавая имя публикации в **ЦС**  извлечены конфликты, которые относятся к **ЦС** публикации.  
  
`[ @conflict_table = ] 'conflict_table'` — Имя таблицы конфликтов. *conflict_table* — **sysname**, не имеет значения по умолчанию. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях таблицам конфликтов присваиваются имена форматов с помощью **MSmerge_conflict\__публикации\_статье_**, с одна таблица для каждой опубликованной статьи.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
`[ @logical_record_conflicts = ] logical_record_conflicts` Указывает, содержит ли результирующий набор сведения о конфликтах логических записей. *logical_record_conflicts* — **int**, со значением по умолчанию 0. **1** означает, что возвращаются сведения о конфликтах логических записей.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_helpmergeconflictrows** возвращает результирующий набор, состоящий из структуры базовой таблицы и следующих дополнительных столбцов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|Источник конфликта.|  
|**conflict_type**|**int**|Код, указывающий тип конфликта.<br /><br /> **1** = конфликт обновления: конфликт обнаружен на уровне строки;<br /><br /> **2** = конфликт обновления столбца: конфликт обнаружен на уровне столбца;<br /><br /> **3** = удаление побеждает в конфликте обновления: конфликт разрешен удалением;<br /><br /> **4** = обновление побеждает в конфликте Delete: в этой таблице записан удаленный идентификатор rowguid, проигравший конфликт.<br /><br /> **5** = неудачная вставка при передаче: выполнение вставки со стороны подписчика на стороне издателя оказалось невозможным;<br /><br /> **6** = неудачная вставка при загрузке: выполнение вставки со стороны издателя на стороне подписчика оказалось невозможным;<br /><br /> **7** = неудачное удаление при передаче: передача удаления со стороны подписчика на сторону издателя оказалась невозможной;<br /><br /> **8** = неудачное удаление при загрузке: загрузка удаления со стороны издателя на сторону подписчика оказалась невозможной;<br /><br /> **9** = неудачное обновление при передаче: выполнение обновления со стороны подписчика на стороне издателя оказалось невозможным;<br /><br /> **10** = неудачное обновление при загрузке: выполнение обновления со стороны издателя на стороне подписчика оказалось невозможным;<br /><br /> **12** = обновление логической записи побеждает Delete: удаленная логическая запись, которая уступает в конфликте, записывается в данную таблицу;<br /><br /> **13** = вставки конфликтов логических записей обновления: вставка в логическую запись конфликтует с обновлением;<br /><br /> **14** = Удаление логической записи побеждает в конфликте с обновлением: обновленная логическая запись, которая уступает в конфликте, записывается в данную таблицу.|  
|**reason_code**|**int**|Код ошибки, который может зависеть от контекста.|  
|**reason_text**|**varchar(720)**|Описание ошибки, которое может зависеть от контекста.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время, когда были добавлены сведения о конфликте.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergeconflictrows** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных и **replmonitor** роли в базе данных распространителя могут выполнять процедуру **sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр сведений о конфликтах для публикаций слиянием &#40;программирование репликации Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
