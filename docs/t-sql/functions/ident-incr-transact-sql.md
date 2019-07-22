---
title: IDENT_INCR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_INCR
- IDENT_INCR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- incremental values [SQL Server]
- IDENT_INCR function
- identity columns [SQL Server], IDENT_INCR function
ms.assetid: e13b491f-4f1f-4cb6-8b63-5084120f98cf
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c3d601df6b045347a46010b422308cabc43188c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024380"
---
# <a name="identincr-transact-sql"></a>IDENT_INCR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает значение приращения (вида **numeric** ( **@@** MAXPRECISION, 0)), указанное при создании столбца идентификаторов в таблице или представлении.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IDENT_INCR ( 'table_or_view' )  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *table_or_view* **'**  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md), указывающее таблицу или представление для проверки на наличие допустимого значения шага приращения идентификатора. Аргумент *table_or_view* может быть константой строки символов, заключенной в кавычки. Он также может быть переменной, функцией или именем столбца. Аргумент *table_or_view* имеет тип **char**, **nchar**, **varchar** или **nvarchar**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **numeric**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если вызывающий объект не имеет разрешений для просмотра текущего объекта.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или для которых у него есть разрешения. Если у пользователя нет разрешений на объект, встроенная функция, создающая метаданные, например IDENT_INCR, может вернуть значение NULL. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-increment-value-for-a-specified-table"></a>A. Возврат значения приращения для указанной таблицы  
 Следующий пример возвращает значение приращения для таблицы `Person.Address` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENT_INCR('Person.Address') AS Identity_Increment;  
GO  
```  
  
### <a name="b-returning-the-increment-value-from-multiple-tables"></a>Б. Возврат значения приращения из нескольких таблиц  
 В следующем примере функция возвращает таблицы базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], содержащей столбец идентификаторов со значением приращения.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TABLE_SCHEMA, TABLE_NAME,   
   IDENT_INCR(TABLE_SCHEMA + '.' + TABLE_NAME) AS IDENT_INCR  
FROM INFORMATION_SCHEMA.TABLES  
WHERE IDENT_INCR(TABLE_SCHEMA + '.' + TABLE_NAME) IS NOT NULL;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
 TABLE_SCHEMA        TABLE_NAME                IDENT_INCR  
------------        ------------------------  ----------  
Person              Address                            1  
Production          ProductReview                      1  
Production          TransactionHistory                 1  
Person              AddressType                        1  
Production          ProductSubcategory                 1  
Person              vAdditionalContactInfo             1  
dbo                 AWBuildVersion                     1  
Production          BillOfMaterials                    1
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENT_SEED (Transact-SQL)](../../t-sql/functions/ident-seed-transact-sql.md)   
 [DBCC CHECKIDENT (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [sys.identity_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
  
