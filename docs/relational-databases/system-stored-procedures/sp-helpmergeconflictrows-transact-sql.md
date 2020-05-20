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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b6963d3a2b28ba103c731f015fd352ff105cfb95
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828948"
---
# <a name="sp_helpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию **%** . Если указана публикация, возвращаются все конфликты, определенные этой публикацией. Например, если таблица **MSmerge_conflict_Customers** содержит конфликтующие строки для публикаций **WA** и **CA** , передача имени публикации **ЦС** извлекает конфликты, относящиеся к публикации **ЦС** .  
  
`[ @conflict_table = ] 'conflict_table'`Имя таблицы конфликтов. Аргумент *conflict_table* имеет тип **sysname**и не имеет значения по умолчанию. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях таблицы с конфликтами именуются с помощью **MSmerge_conflict \_ _публикации \_ _** с одной таблицей для каждой опубликованной статьи.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @logical_record_conflicts = ] logical_record_conflicts`Указывает, содержит ли результирующий набор сведения о конфликтах логических записей. *logical_record_conflicts* имеет **тип int**и значение по умолчанию 0. **1** означает, что возвращаются сведения о конфликте логических записей.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_helpmergeconflictrows** возвращает результирующий набор, состоящий из базовой структуры таблицы и этих дополнительных столбцов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar (255)**|Источник конфликта.|  
|**conflict_type**|**int**|Код, указывающий тип конфликта.<br /><br /> **1** = конфликт обновления: конфликт обнаружен на уровне строк.<br /><br /> **2** = конфликт обновления столбца: конфликт обнаружен на уровне столбцов.<br /><br /> **3** = конфликт при удалении обновления WINS: Удаление побеждает в конфликте.<br /><br /> **4** = обновить конфликт удаления WINS. в этой таблице записывается удаленный идентификатор rowguid, который потерял конфликт.<br /><br /> **5** = ошибка при передаче вставки: не удалось применить вставку с подписчика на издателе.<br /><br /> **6** = ошибка загрузки при скачивании: не удалось применить вставку из издателя на подписчике.<br /><br /> **7** = ошибка отправки при удалении: не удалось отправить на издатель подписчика.<br /><br /> **8** = ошибка загрузки при удалении: не удалось загрузить удаление на стороне издателя на подписчик.<br /><br /> **9** = ошибка отправки обновления: не удалось применить обновление на подписчике на издателе.<br /><br /> **10** = ошибка загрузки обновления: не удалось применить обновление на стороне издателя к подписчику.<br /><br /> **12** = Обновление логической записи WINS Delete: в этой таблице записана удаленная логическая запись, которая потеряла конфликт.<br /><br /> **13** = конфликт логической записи при вставке обновления: Вставка в логическую запись конфликтует с обновлением.<br /><br /> **14** = Удаление логической записи: конфликт обновления WINS. в этой таблице записана обновленная логическая запись, которая потеряла конфликт.|  
|**reason_code**|**int**|Код ошибки, который может зависеть от контекста.|  
|**reason_text**|**varchar (720)**|Описание ошибки, которое может зависеть от контекста.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время, когда были добавлены сведения о конфликте.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergeconflictrows** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных и роли **replmonitor** в базе данных распространителя могут выполнять **sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр сведений о конфликтах для публикаций слиянием &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
