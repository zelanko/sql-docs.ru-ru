---
description: FILEPROPERTYEX (Transact-SQL)
title: FILEPROPERTYEX (Transact-SQL) | Документация Майкрософт
ms.date: 07/23/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEPROPERTYEX_TSQL
- FILEPROPERTYEX
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTYEX function
- file names [SQL Server], FILEPROPERTYEX
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4fca1a10c6e0fce286854b96ac673e602744cdb6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479670"
---
# <a name="filepropertyex-transact-sql"></a>FILEPROPERTYEX (Transact-SQL)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Возвращает указанное значение расширенного свойства файла, если указываются имя файла текущей базы данных и имя свойства. Возвращает значение NULL для файлов, которые отсутствуют в текущей базе данных, или для несуществующих расширенных свойств файла. В настоящее время расширенные свойства файла применяются только к базам данных, которые находятся в хранилище BLOB-объектов Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FILEPROPERTYEX ( name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *name*  
 Выражение, которое содержит имя файла, связанного с текущей базой данных, для которого нужно возвратить сведения о свойстве. Аргумент *file_name* имеет тип **nchar(128)**.  
  
 *property*  
 Выражение, которое содержит имя свойства файла, которое нужно возвратить. Аргумент *property* имеет тип **varchar(128)** и может принимать одно из перечисленных ниже значений.  


  
|Значение|Описание|
|-----------|-----------------|  
|**BlobTier**|Уровень целевого страничного BLOB-объекта Azure. Применяется только к базам данных категорий "Стандартный" или "Общего назначения", использующим хранилище страничных BLOB-объектов Azure.|
|**AccountType**|Тип учетной записи хранения, указывающий, является ли она учетной записью хранения BLOB-объектов или файлов, а также является ли она учетной записью хранения класса Premium или Standard.|
|**IsInferredTier**|Указывает, является ли уровень неявным (выводимым), размер которого может увеличиваться с ростом данных, или явным (фиксированным).|
|**IsPageBlob**|Указывает, является ли целевой BLOB-объект страничным.|
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **sql_variant**  
  
## <a name="remarks"></a>Remarks  
 Аргумент *file_name* соответствует столбцу **name** в представлении каталога **sys.master_files** или **sys.database_files**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан возврат параметра для файлов базы данных.
```sql
SELECT s.file_id,
       s.type_desc,
       s.name,
       FILEPROPERTYEX(s.name, 'BlobTier') AS BlobTier,
       FILEPROPERTYEX(s.name, 'AccountType') AS AccountType,
       FILEPROPERTYEX(s.name, 'IsInferredTier') AS IsInferredTier,
       FILEPROPERTYEX(s.name, 'IsPageBlob') AS IsPageBlob
FROM sys.database_files AS s
WHERE s.type_desc IN ('ROWS', 'LOG');
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
file_id  type_desc  name  BlobTier  AccountType  IsInferredTier  IsPageBlob
--------------------------------------------------------------------------------------
1     ROWS      data_0  P30  PremiumBlobStorage  0   1
2     LOG       log     P30  PremiumBlobStorage  0   1

(2 rows affected)
```  
  
## <a name="see-also"></a>См. также  
 [FILEGROUPPROPERTY (Transact-SQL)](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
