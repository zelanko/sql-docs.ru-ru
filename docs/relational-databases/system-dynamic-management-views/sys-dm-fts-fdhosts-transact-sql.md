---
title: "sys.dm_fts_fdhosts (Transact-SQL) | Документы Microsoft"
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9866da01d5ef108e9665c0d04ac3e89ee8cc30be
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
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
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  

## <a name="examples"></a>Примеры  
 В следующем примере возвращается имя узла управляющей программы фильтрации и максимальное число потоков в ней. Также отслеживается текущее количество пакетов, одновременно обрабатываемых в управляющей программе фильтрации. Эти сведения могут использоваться для диагностики производительности.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
