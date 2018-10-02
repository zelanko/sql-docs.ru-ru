---
title: FILEGROUPPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ffe6718eca0e385941e102801e218acc8680711f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695702"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Эта функция возвращает значение свойства файловой группы по указанному имени и значению этой группы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FILEGROUPPROPERTY ( filegroup_name, property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *filegroup_name*  
Выражение типа **sysname**, представляющее имя файловой группы, для которой `FILEGROUPPROPERTY` возвращает сведения об именованном свойстве.  
  
 *property*  
Выражение типа **varchar(128)**, которое возвращает имя свойства файловой группы. Аргумент *property* может иметь одно из следующих значений:  
  
|Значение|Описание|Возвращенное значение|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Файловая группа доступна только для чтения.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: недопустимые входные данные|  
|**IsUserDefinedFG**|Файловая группа является пользовательской.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: недопустимые входные данные|  
|**IsDefault**|Файловая группа является файловой группой по умолчанию.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: недопустимые входные данные|  
  
## <a name="return-types"></a>Типы возвращаемых данных  
**int**  
  
## <a name="remarks"></a>Remarks  
Аргумент *filegroup_name* соответствует столбцу **name** в представлении каталога **sys.filegroups**.  
  
## <a name="examples"></a>Примеры  
Этот пример возвращает значение параметра `IsDefault` для первичной файловой группы в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [FILEGROUP_ID (Transact-SQL)](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME (Transact-SQL)](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
