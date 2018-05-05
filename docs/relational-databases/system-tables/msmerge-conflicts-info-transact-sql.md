---
title: MSmerge_conflicts_info (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f96edbd1cdd0fff2f5e6d7d0037156a9f2033329
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflicts_info** таблиц отслеживания конфликтов при синхронизации подписки на публикацию слиянием. При конфликтах данные строк проигравшей хранится в [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md) таблица для статьи, в которой возник конфликт. Эта таблица сохраняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**ROWGUID**|**uniqueidentifier**|Идентификатор конфликтной строки.|  
|**origin_datasource**|**nvarchar(255)**|Имя базы данных-источника конфликтного изменения.|  
|**conflict_type**|**int**|Тип возникшего конфликта может быть одним из следующих:<br /><br /> **1** = конфликт обновления: конфликт обнаружен на уровне строк.<br /><br /> **2** = конфликт обновления столбца: конфликт обнаружен на уровне столбца.<br /><br /> **3** = обновление удаление побеждает в конфликте с: конфликт разрешен удалением.<br /><br /> **4** = Wins удалить в конфликте с обновлением: удаленный идентификатор rowguid, которая уступает в конфликте, записывается в данную таблицу.<br /><br /> **5** = Вставка не удалось отправить: выполнение вставки со стороны подписчика не может быть применена на издателе.<br /><br /> **6** = Вставка не удалось загрузить: insert от издателя не может быть применена на подписчике.<br /><br /> **7** = удалить не удалось отправить: не удалось загрузить удаления со стороны подписчика на издатель.<br /><br /> **8** = удалить не удалось загрузить: не удалось загрузить удаления со стороны издателя на подписчик.<br /><br /> **9** = обновить не удалось отправить: обновления на подписчике не может быть применена на издателе.<br /><br /> **10** = обновить не удалось загрузить: обновления на стороне издателя оказалось невозможным подписчику.<br /><br /> **11** = разрешение<br /><br /> **12** = логической записи обновления Wins Delete: удаленная логическая запись, которая уступает в конфликте, записывается в данную таблицу.<br /><br /> **13** = логической записи конфликтов вставить обновления: вставка в логическую запись конфликтует с обновлением.<br /><br /> **14** = логической записи удалить Wins в конфликте с обновлением: обновленная логическая запись, которая уступает в конфликте, записывается в данную таблицу.|  
|**reason_code**|**int**|Код ошибки, который может зависеть от контекста. В случае конфликтов обновления и обновления и удаления, используемое для этого столбца значение совпадает со значением **conflict_type**. Однако в случае конфликтов, связанных с неудачными изменениями, код причины равен ошибке, которая не дала агенту слияния применить изменения. Например, если агент слияния не может применить вставку на подписчике из-за нарушения первичного ключа, он регистрирует **conflict_type** 6 («неудачная вставка при загрузке») и **reason_code** 627, которое является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутреннее сообщение об ошибке для нарушения первичного ключа: «нарушение %ls ограничения ' %. * ls. Невозможно вставить повторяющийся ключ в объект ' %. \*ls.»|  
|**reason_text**|**nvarchar(720)**|Описание кода ошибки, который может зависеть от контекста.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время возникновения конфликта.|  
|**origin_datasource_id**|**uniqueidentifier**|Идентификатор базы данных, откуда было произведено конфликтное изменение.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
