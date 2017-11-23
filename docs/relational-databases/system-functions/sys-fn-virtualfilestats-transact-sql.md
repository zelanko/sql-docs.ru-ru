---
title: "sys.fn_virtualfilestats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_virtualfilestats_TSQL
- fn_virtualfilestats
dev_langs: TSQL
helpviewer_keywords:
- I/O [SQL Server], statistics
- fn_virtualfilestats function
- sys.fn_virtualfilestats function
- statistical information [SQL Server], I/O
ms.assetid: 96b28abb-b059-48db-be2b-d60fe127f6aa
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 75af14c94dd17ae6caead3f6b5dee9e0bf0b257e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnvirtualfilestats-transact-sql"></a>sys.fn_virtualfilestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает статистику ввода-вывода для файлов базы данных, включая файлы журналов. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], эта информация также доступна из [sys.dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) динамическое административное представление.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_virtualfilestats ( { database_id | NULL } , { file_id | NULL } )  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_id* | ЗНАЧЕНИЕ NULL  
 Идентификатор базы данных. *database_id* — **int**, не имеет значения по умолчанию. Укажите значение NULL, чтобы вернуть сведения для всех баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *file_id* | ЗНАЧЕНИЕ NULL  
 Идентификатор файла. *file_id* — **int**, не имеет значения по умолчанию. Чтобы получить сведения обо всех файлах в базе данных, укажите значение NULL.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**DbId**|**smallint**|Идентификатор базы данных.|  
|**Идентификатор файла**|**smallint**|Идентификатор файла.|  
|**Отметка времени**|**bigint**|Отметка времени базы данных, указывающая, когда была получена информация. **int** в версиях до [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]. |  
|**Количество запросов на чтение**|**bigint**|Количество считываний для этого файла.|  
|**BytesRead**|**bigint**|Число считанных из файла байтов.|  
|**IoStallReadMS**|**bigint**|Общее количество времени, в миллисекундах, затраченного пользователями на ожидание выполнения операций чтения из файла.|  
|**Количество запросов на запись**|**bigint**|Количество операций записи для этого файла.|  
|**Записано байт**|**bigint**|Число байтов, записанных в файл.|  
|**IoStallWriteMS**|**bigint**|Общее количество времени, в миллисекундах, затраченного пользователями на ожидание выполнения операций записи в файл.|  
|**IoStallMS**|**bigint**|Сумма **IoStallReadMS** и **IoStallWriteMS**.|  
|**FileHandle**|**bigint**|Значение дескриптора файла.|  
|**BytesOnDisk**|**bigint**|Физический размер файла на диске (в байтах).<br /><br /> Для файлов базы данных, это то же значение, что **размер** в **sys.database_files**, но выражается в байтах, а не страницы.<br /><br /> Для разреженных файлов моментального снимка базы данных это пространство, используемое операционной системой для данного файла.|  
  
## <a name="remarks"></a>Замечания  
 **fn_virtualfilestats** — это система, табличная функция, которая дает статистическую информацию, например общее количество операций ввода-вывода, выполненных над файлом. Эту функцию можно использовать для контроля времени, затрачиваемого пользователями на ожидание выполнения чтения или записи в файл. Эта функция также помогает выявить файлы, над которыми выполняется много операций ввода-вывода.  
  
## <a name="permissions"></a>Permissions  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-statistical-information-for-a-database"></a>A. Просмотр статистической информации для базы данных  
 В следующем примере выводится статистическая информация для идентификатора файла 1 в базе данных с идентификатором `1`.  
  
```tsql  
SELECT *  
FROM fn_virtualfilestats(1, 1);  
GO  
```  
  
### <a name="b-displaying-statistical-information-for-a-named-database-and-file"></a>Б. Просмотр статистической информации для именованной базы данных и файла  
 В следующем примере выводятся статистические данные для файла журнала в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Системная функция `DB_ID` используется для указания *database_id* параметра.  
  
```tsql  
SELECT *  
FROM fn_virtualfilestats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="c-displaying-statistical-information-for-all-databases-and-files"></a>В. Просмотр статистической информации для всех баз данных и файлов  
 В следующем примере выводится статистическая информация для всех файлов во всех базах данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
SELECT *  
FROM fn_virtualfilestats(NULL,NULL);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DB_ID &#40; Transact-SQL &#41;](../../t-sql/functions/db-id-transact-sql.md)   
 [FILE_IDEX &#40; Transact-SQL &#41;](../../t-sql/functions/file-idex-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
