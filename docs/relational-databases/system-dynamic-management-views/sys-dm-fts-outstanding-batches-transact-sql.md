---
title: "sys.dm_fts_outstanding_batches (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs:
- TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06490fd099957c3636f05dcfe4e8f0ba9deab8d3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsoutstandingbatches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает данные о каждом пакете полнотекстового индексирования.  
  
  |Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|  
|catalog_id|**int**|Идентификатор полнотекстового каталога.|  
|table_id|**int**|Идентификатор идентификатора таблицы, в которой содержится полнотекстовый индекс.|  
|batch_id|**int**|Идентификатор пакета|  
|memory_address|**varbinary(8)**|Адрес памяти пакетного объекта.|  
|crawl_memory_address|**varbinary(8)**|Адрес памяти объекта сканирования (родительского объекта).|  
|memregion_memory_address|**varbinary(8)**|Адрес области памяти исходящей общей памяти узла управляющей программы фильтрации (fdhost.exe).|  
|hr_batch|**int**|Самый последний код ошибки для пакета.|  
|is_retry_batch|**бит**|Обозначает, является ли пакет повторно передаваемым:<br /><br /> 0 = нет<br /><br /> 1 = да|  
|retry_hints|**int**|Тип повторной попытки, нужный для пакета:<br /><br /> 0 = нет повторения;<br /><br /> 1 = многопоточное повторение;<br /><br /> 2 = однопоточное повторение;<br /><br /> 3 = однопоточное и многопоточное повторение;<br /><br /> 5 = многопоточное окончательное повторение;<br /><br /> 6 = однопоточное окончательное повторение;<br /><br /> 7 = однопоточное и многопоточное окончательное повторение.|  
|retry_hints_description|**nvarchar(120)**|Описание типа необходимой повторной попытки:<br /><br /> НЕТ ПОВТОРЕНИЯ;<br /><br /> МНОГОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ И МНОГОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> МНОГОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ И МНОГОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ.|  
|doc_failed|**bigint**|Количество отказавших документов в пакете.|  
|batch_timestamp|**timestamp**|Значение timestamp, полученное при создании пакета.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 
## <a name="examples"></a>Примеры  
 В следующем примере выясняется, сколько пакетов обрабатывается в данный момент для каждой таблицы для экземпляра сервера.  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
