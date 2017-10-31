---
title: "FILE_IDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 9a65a49a1e6d8c23a28b117fc90b0276ce185556
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="fileidex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Возвращает номер идентификатора файла (ID) для указанного логического имени файла данных, файла журнала, или полнотекстового файла в текущей базе данных.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_файла*  
 Является выражением типа **sysname** , представляющий имя файла, для которого необходимо вернуть идентификатор файла  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
 **Значение NULL,** при возникновении ошибки  
  
## <a name="remarks"></a>Замечания  
 *имя_файла* соответствующее логическое имя файла в **имя** столбца в [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) или [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) представления каталога.  
  
 Функция FILE_IDEX может быть использована в списке выбора, в предложении WHERE или в любом другом месте, где допускаются выражения. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>A. Получение идентификатора для указанного файла  
Следующий пример возвращает идентификатор файла `AdventureWorks_Data`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>Б. Получение идентификатора файла, имя которого неизвестно  
В следующем примере возвращается идентификатор `AdventureWorks` файла журнала, выбрав логическое имя файла из `sys.database_files` представление, где тип файла равен каталога `1` (журнал).  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>В. Получение идентификатора файла полнотекстового файла каталога  
В следующем примере возвращается идентификатор файла полнотекстового файла, выбрав логическое имя файла из `sys.database_files` представление, где тип файла равен каталога `4` (полнотекстовой). Этот пример возвращает значение NULL, если полнотекстовый каталог не существует.  
  
```tsql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

