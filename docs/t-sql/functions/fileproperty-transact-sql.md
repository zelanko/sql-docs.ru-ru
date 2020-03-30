---
title: FILEPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79be8af32c13b9e910b94b40bd3c1bf9b2c0e2c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68071398"
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает указанное значение свойства имени файла, если указываются имя файла текущей базы данных и имя свойства. Возвращает значение NULL для файлов, которые не находятся в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *file_name*  
 Выражение, которое содержит имя файла, связанного с текущей базой данных, для которого нужно возвратить сведения о свойстве. Аргумент *file_name* имеет тип **nchar(128)** .  
  
 *property*  
 Выражение, которое содержит имя свойства файла, которое нужно возвратить. Аргумент *property* имеет тип **varchar(128)** и может принимать одно из перечисленных ниже значений.  
  
|Значение|Description|Возвращенное значение|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Файловая группа доступна только для чтения.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsPrimaryFile**|Файл является первичным файлом.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsLogFile**|Файл является файлом журнала.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**SpaceUsed**|Объем пространства, используемого указанным файлом.|Число страниц, выделенных для файла.|  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Аргумент *file_name* соответствует столбцу **name** в представлении каталога **sys.master_files** или **sys.database_files**.  
  
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
 [FILEGROUPPROPERTY (Transact-SQL)](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
