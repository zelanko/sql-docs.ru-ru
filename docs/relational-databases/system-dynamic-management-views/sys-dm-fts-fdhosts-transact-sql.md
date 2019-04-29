---
title: sys.dm_fts_fdhosts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: faa79f48a4f3b8ac70984c3b02c8863d7d37e8ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026719"
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о текущем действии узла управляющей программы фильтрации или узлов на экземпляре сервера.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|Идентификатор узла управляющей программы фильтрации.|  
|**fdhost_name**|**nvarchar(120)**|Имя узла управляющей программы фильтрации.|  
|**fdhost_process_id**|**int**|Идентификатор процесса Windows узла управляющей программы фильтрации.|  
|**fdhost_type**|**nvarchar(120)**|Тип документа, обрабатываемого узлом управляющей программы фильтрации, — один из следующих.<br /><br /> Одиночный поток.<br /><br /> Многопоточный.<br /><br /> Огромный документ.|  
|**max_thread**|**int**|Максимальное количество потоков в узле управляющей программы фильтрации.|  
|**batch_count**|**int**|Количество пакетов, обрабатываемых в узле управляющей программы фильтрации.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="examples"></a>Примеры  
 В следующем примере возвращается имя узла управляющей программы фильтрации и максимальное число потоков в ней. Также отслеживается текущее количество пакетов, одновременно обрабатываемых в управляющей программе фильтрации. Эти сведения могут использоваться для диагностики производительности.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
