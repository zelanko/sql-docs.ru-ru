---
title: sp_helpmergeconflictrows (Transact-SQL) | Документы Microsoft
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
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 60759dfe84d22e919cf14d6fb33454b2d11bae49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32998951"
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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%**. Если указана публикация, возвращаются все конфликты, определенные этой публикацией. Например если **MSmerge_conflict_Customers** таблица имеет конфликтующие строки для **WA** и **ЦС** публикаций, передав имя публикации **ЦС**  извлекает конфликты, которые относятся к **ЦС** публикации.  
  
 [  **@conflict_table=**] **"***conflict_table***"**  
 Имя таблицы конфликтов. *conflict_table* — **sysname**, не имеет значения по умолчанию. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях таблицам конфликтов присваиваются имена форматов с помощью **MSmerge_conflict_* публикации *_* статье *** с одной таблицей для каждой публикации статья.  
  
 [  **@publisher=**] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 — Это имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
 [  **@logical_record_conflicts=** ] *logical_record_conflicts*  
 Указывает, содержит ли результирующий набор сведения о конфликтах логических записей. *logical_record_conflicts* — **int**, значение по умолчанию 0. **1** означает, что возвращаются сведения конфликтов логических записей.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_helpmergeconflictrows** возвращает результирующий набор, состоящий из структуры базовой таблицы и следующих дополнительных столбцов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|Источник конфликта.|  
|**conflict_type**|**int**|Код, указывающий тип конфликта.<br /><br /> **1** = конфликт обновления: конфликт обнаружен на уровне строк.<br /><br /> **2** = конфликт обновления столбца: конфликт обнаружен на уровне столбца.<br /><br /> **3** = обновление удаление побеждает в конфликте с: конфликт разрешен удалением.<br /><br /> **4** = Wins удалить в конфликте с обновлением: удаленный идентификатор rowguid, которая уступает в конфликте, записывается в данную таблицу.<br /><br /> **5** = Вставка не удалось отправить: выполнение вставки со стороны подписчика не может быть применена на издателе.<br /><br /> **6** = Вставка не удалось загрузить: insert от издателя не может быть применена на подписчике.<br /><br /> **7** = удалить не удалось отправить: не удалось загрузить удаления со стороны подписчика на издатель.<br /><br /> **8** = удалить не удалось загрузить: не удалось загрузить удаления со стороны издателя на подписчик.<br /><br /> **9** = обновить не удалось отправить: обновления на подписчике не может быть применена на издателе.<br /><br /> **10** = обновить не удалось загрузить: обновления на стороне издателя оказалось невозможным подписчику.<br /><br /> **12** = логической записи обновления Wins Delete: удаленная логическая запись, которая уступает в конфликте, записывается в данную таблицу.<br /><br /> **13** = логической записи конфликтов вставить обновления: вставка в логическую запись конфликтует с обновлением.<br /><br /> **14** = логической записи удалить Wins в конфликте с обновлением: обновленная логическая запись, которая уступает в конфликте, записывается в данную таблицу.|  
|**reason_code**|**int**|Код ошибки, который может зависеть от контекста.|  
|**reason_text**|**varchar(720)**|Описание ошибки, которое может зависеть от контекста.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время, когда были добавлены сведения о конфликте.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpmergeconflictrows** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных и **replmonitor** в базе данных распространителя могут выполнять процедуру **sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр сведений о конфликтах для публикаций слиянием &#40;программирование репликации Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
