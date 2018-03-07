---
title: "SQL_VARIANT_PROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5947528f4e8959de1b8b4ee3679d4e3e058476d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sqlvariantproperty-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает базовый тип данных и другие сведения о **sql_variant** значение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Является выражением типа **sql_variant**.  
  
 *Свойство*  
 Содержит имя **sql_variant** свойства, для которого должны быть предоставлены сведения. *Свойство* — **varchar (**128**)**, и может принимать одно из следующих значений:  
  
|Значение|Description|Возвращаемый базовый тип sql_variant|  
|-----------|-----------------|----------------------------------------|  
|**Тип BaseType**|Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например:<br /><br /> **bigint**<br /><br /> **binary**<br /><br /> **char**<br /><br /> **date**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = Введенные значения недопустимы.|  
|**Точность**|Количество знаков числового базового типа данных:<br /><br /> **DateTime** = 23<br /><br /> **smalldatetime** = 16<br /><br /> **число с плавающей запятой** = 53<br /><br /> **реальные** = 24<br /><br /> **десятичное число** (p, s) и **числовое** (p, s) = p<br /><br /> **Money** = 19<br /><br /> **smallmoney** = 10<br /><br /> **bigint** = 19<br /><br /> **int** = 10<br /><br /> **smallint** = 5<br /><br /> **tinyint** = 3<br /><br /> **бит** = 1<br /><br /> Все остальные типы = 0|**int**<br /><br /> NULL = Введенные значения недопустимы.|  
|**Масштаб**|Количество знаков справа от десятичного разделителя числового базового типа данных:<br /><br /> **десятичное число** (p, s) и **числовое** (p, s) = s<br /><br /> **Money** и **smallmoney** = 4<br /><br /> **DateTime** = 3<br /><br /> все остальные типы = 0|**int**<br /><br /> NULL = Введенные значения недопустимы.|  
|**TotalBytes**|Число байтов, необходимое для хранения данных и метаданных значения. Эта информация может быть полезной при проверке максимального размера данных в **sql_variant** столбца. Если значение превышает 900, создание индекса завершается ошибкой.|**int**<br /><br /> NULL = Введенные значения недопустимы.|  
|**Параметры сортировки**|Представляет параметры сортировки конкретного **sql_variant** значение.|**sysname**<br /><br /> NULL = Введенные значения недопустимы.|  
|**MaxLength**|Максимальная длина типа данных, в байтах. Например **MaxLength** из **nvarchar (**50**)** равен 100, **MaxLength** из **int** — 4.|**int**<br /><br /> NULL = Введенные значения недопустимы.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **sql_variant**  
  
## <a name="examples"></a>Примеры  
### <a name="a-using-a-sqlvariant-in-a-table"></a>A. Использование sql_variant в таблице  
 В следующем примере извлекается `SQL_VARIANT_PROPERTY` сведения о `colA` значение `46279.1` где `colB`  = `1689`, учитывая, что `tableA` имеет `colA` типа `sql_variant` и `colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Обратите внимание, что каждое из этих трех значений **sql_variant**.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>Б. Использование в качестве переменной типа sql_variant   
 В следующем примере извлекается `SQL_VARIANT_PROPERTY` сведения о переменной с именем @v1.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>См. также:  
 [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  

