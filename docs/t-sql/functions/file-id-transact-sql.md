---
title: "File_id (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1b2025ee9fdc5ca0aaf4967305db40cb65d038c
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает идентификатор (ID) файла, соответствующий заданному логическому имени файла в текущей базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_файла*  
 Является выражением типа **sysname** , представляющий имя файла, для которого необходимо вернуть идентификатор файла  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **smallint**  
  
## <a name="remarks"></a>Remarks  
 *имя_файла* соответствующее логическое имя файла в столбце имени в представлениях каталога sys.master_files или sys.database_files.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификационный номер файла, присваиваемый полнотекстовому каталогу, больше чем 32767. Так как тип возвращаемого значения функции FILE_ID является **smallint**, эта функция не может использоваться для полнотекстовых файлов. Используйте [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) вместо него.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает идентификатор файла `AdventureWorks_Data`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Имя_файла &#40; Transact-SQL &#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
