---
title: "FILEPROPERTY (Transact-SQL) | Документы Microsoft"
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
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7078fecb77bad44fd6aa4c3ce0baf9565f1d6d3f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает указанное значение свойства имени файла, если указываются имя файла текущей базы данных и имя свойства. Возвращает значение NULL для файлов, которые не находятся в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_файла*  
 Выражение, которое содержит имя файла, связанного с текущей базой данных, для которого нужно возвратить сведения о свойстве. *имя_файла* — **nchar(128)**.  
  
 *Свойство*  
 Выражение, которое содержит имя свойства файла, которое нужно возвратить. *Свойство* — **varchar(128)**, и может принимать одно из следующих значений.  
  
|Значение|Description|Возвращенное значение|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Файловая группа доступна только для чтения.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsPrimaryFile**|Файл является первичным файлом.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsLogFile**|Файл является файлом журнала.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**SpaceUsed**|Объем пространства, используемого указанным файлом.|Число страниц, выделенных для файла.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 *имя_файла* соответствует **имя** столбца в **sys.master_files** или **sys.database_files** представления каталога.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается параметр для свойства `IsPrimaryFile` имени файла `AdventureWorks_Data` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [FILEGROUPPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

