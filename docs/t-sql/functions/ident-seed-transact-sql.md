---
title: "IDENT_SEED (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f4a4fa1196b60cb7068afe10a246ab2e18bfcf94
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="identseed-transact-sql"></a>IDENT_SEED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает исходное начальное значение (возвращаются в виде **числовое**(**@@**MAXPRECISION, 0)), указанный при создании столбца идентификаторов в таблице или представлении. Изменение текущего значения столбца идентификаторов с помощью инструкции DBCC CHECKIDENT не изменяет значение, возвращаемое этой функцией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IDENT_SEED ( 'table_or_view' )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *таблица_или_представление* **"**  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) , указывающее таблицу или представление для проверки начальное значение идентификатора. *таблица_или_представление* может быть строковой константой, заключенной в кавычки, переменной, функции или имени столбца. *таблица_или_представление* — **char**, **nchar**, **varchar**, или **nvarchar**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **numeric**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как IDENT_SEED, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-seed-value-from-a-specified-table"></a>A. Возврат начального значения из указанной таблицы  
 Следующий пример возвращает начальное значение для таблицы `Person.Address` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENT_SEED('Person.Address') AS Identity_Seed;  
GO  
```  
  
### <a name="b-returning-the-seed-value-from-multiple-tables"></a>Б. Возврат начального значения из нескольких таблиц  
 В следующем примере функция возвращает таблицы базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], содержащие столбцы идентификаторов с начальным значением.  
  
```  
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
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [DBCC CHECKIDENT (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [sys.identity_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
  

