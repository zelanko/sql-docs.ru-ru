---
title: IDENT_SEED (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_SEED_TSQL
- IDENT_SEED
dev_langs:
- TSQL
helpviewer_keywords:
- identity columns [SQL Server], IDENT_SEED function
- seed values [SQL Server]
- IDENT_SEED function
ms.assetid: e4cb8eb8-affb-4810-a8a9-0110af3c247a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4682d0ecd3b1eeeac2b92d5e76beb0ca2355f3f4
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113468"
---
# <a name="ident_seed-transact-sql"></a>IDENT_SEED (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает исходное начальное значение, указанное при создании столбца идентификаторов в таблице или представлении. Изменение текущего значения столбца идентификаторов с помощью инструкции DBCC CHECKIDENT не изменяет значение, возвращаемое этой функцией.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDENT_SEED ( 'table_or_view' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **'** *table_or_view* **'**  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md), указывающее таблицу или представление, в которых проверяется начальное значение идентификатора. Аргумент *table_or_view* может быть строковой константой, заключенной в кавычки, переменной, функцией или именем столбца. Аргумент *table_or_view* имеет тип **char**, **nchar**, **varchar** или **nvarchar**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
**numeric**([@@MAXPRECISION](../../t-sql/functions/max-precision-transact-sql.md),0))  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если вызывающий объект не имеет разрешений для просмотра текущего объекта.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему предоставлены разрешения. Эта мера безопасности означает, что встроенные функции, создающие метаданные, такие как IDENT_SEED, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-seed-value-from-a-specified-table"></a>A. Возврат начального значения из указанной таблицы  
 Следующий пример возвращает начальное значение для таблицы `Person.Address` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT IDENT_SEED('Person.Address') AS Identity_Seed;  
GO  
```  
  
### <a name="b-returning-the-seed-value-from-multiple-tables"></a>Б. Возврат начального значения из нескольких таблиц  
 В следующем примере возвращаются таблицы базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] со столбцом идентификаторов, заполненным начальными значениями.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT TABLE_SCHEMA, TABLE_NAME,   
   IDENT_SEED(TABLE_SCHEMA + '.' + TABLE_NAME) AS IDENT_SEED  
FROM INFORMATION_SCHEMA.TABLES  
WHERE IDENT_SEED(TABLE_SCHEMA + '.' + TABLE_NAME) IS NOT NULL;  
GO  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
 TABLE_SCHEMA       TABLE_NAME                   IDENT_SEED  
------------       ---------------------------  -----------  
Person             Address                                1  
Production         ProductReview                          1  
Production         TransactionHistory                100000  
Person             AddressType                            1  
Production         ProductSubcategory                     1  
Person             vAdditionalContactInfo                 1  
dbo                AWBuildVersion                         1
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENT_INCR (Transact-SQL)](../../t-sql/functions/ident-incr-transact-sql.md)   
 [DBCC CHECKIDENT (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [sys.identity_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
