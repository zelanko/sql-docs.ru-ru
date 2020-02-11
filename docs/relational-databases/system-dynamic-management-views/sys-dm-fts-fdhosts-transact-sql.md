---
title: sys. dm_fts_fdhosts (Transact-SQL) | Документация Майкрософт
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
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 77bf96ee1cea4356e26d33fab9ab519e99ae0a60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265964"
---
# <a name="sysdm_fts_fdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о текущем действии узла управляющей программы фильтрации или узлов на экземпляре сервера.  
  
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|Идентификатор узла управляющей программы фильтрации.|  
|**fdhost_name**|**nvarchar (120)**|Имя узла управляющей программы фильтрации.|  
|**fdhost_process_id**|**int**|Идентификатор процесса Windows узла управляющей программы фильтрации.|  
|**fdhost_type**|**nvarchar (120)**|Тип документа, обрабатываемого узлом управляющей программы фильтрации, — один из следующих.<br /><br /> Одиночный поток.<br /><br /> Многопоточный.<br /><br /> Огромный документ.|  
|**max_thread**|**int**|Максимальное количество потоков в узле управляющей программы фильтрации.|  
|**batch_count**|**int**|Количество пакетов, обрабатываемых в узле управляющей программы фильтрации.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="examples"></a>Примеры  
 В следующем примере возвращается имя узла управляющей программы фильтрации и максимальное число потоков в ней. Также отслеживается текущее количество пакетов, одновременно обрабатываемых в управляющей программе фильтрации. Эти сведения могут использоваться для диагностики производительности.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
