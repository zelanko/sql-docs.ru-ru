---
title: sql_variant (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- sql_variant
- sql_variant_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sql_variant comparisons
- storing data [SQL Server], sql_variant
- sql_variant data type
- storage [SQL Server], sql_variant
ms.assetid: 01229779-8bc1-4c7d-890a-8246d4899250
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a417d8240bb3360a13367230f0017762b51d659
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000503"
---
# <a name="sqlvariant-transact-sql"></a>sql_variant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип данных, хранящий значения различных типов данных, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
sql_variant  
```  
  
## <a name="remarks"></a>Remarks  
**sql_variant** может использоваться в столбцах, параметрах, переменных и значениях, возвращаемых определяемыми пользователем функциями. **sql_variant** позволяет этим объектам баз данных поддерживать значения других типов данных.
  
Столбец типа **sql_variant** может содержать строки различных типов данных. Например, в столбце, определенном как **sql_variant**, могут храниться значения **int**, **binary** и **char**.
  
Максимальная длина значения типа данных **sql_variant** составляет 8016 байт. Сюда входят сведения о базовом типе и значение базового типа. Максимальная длина значения соответствующего базового типа составляет 8 000 байт.
  
Перед тем как задействовать тип данных **sql_variant** в таких операциях, как сложение и вычитание, его нужно привести к значению базового типа данных.
  
Типу данных **sql_variant** может быть присвоено значение по умолчанию. Этот тип данных в качестве значения может содержать значение NULL, однако значению NULL не будет соответствовать базовый тип. Кроме того, тип данных **sql_variant** не может в качестве базового иметь другой тип данных **sql_variant**.
  
Уникальный, первичный или внешний ключ может содержать столбцы типа **sql_variant**, но общая длина значений данных, составляющих ключ определенной строки, не должна превышать максимальную длину индекса. Эта длина составляет 900 байт.
  
Таблица может иметь любое количество столбцов типа **sql_variant**.
  
Тип **sql_variant** нельзя использовать в инструкциях CONTAINSTABLE и FREETEXTTABLE.
  
Протокол ODBC поддерживает тип **sql_variant** не полностью. Поэтому столбцы типа **sql_variant**, запрашиваемые через поставщик Microsoft OLE DB для ODBC (MSDASQL), возвращаются в виде двоичных данных. Например, столбец типа **sql_variant**, содержащий строку "PS2091", возвращается в виде 0x505332303931.
  
## <a name="comparing-sqlvariant-values"></a>Сравнение значений sql_variant  
Тип **sql_variant** находится на вершине иерархического списка преобразования типов данных. Для сравнения данных типа **sql_variant** иерархия типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разбивается на семейства типов.
  
|Иерархия типов данных|Семейство типов данных|  
|---|---|
|**sql_variant**|sql_variant |  
|**datetime2**|Дата и время|  
|**datetimeoffset**|Дата и время|  
|**datetime**|Дата и время|  
|**smalldatetime**|Дата и время|  
|**date**|Дата и время|  
|**time**|Дата и время|  
|**float**|Приблизительное числовое значение|  
|**real**|Приблизительное числовое значение|  
|**decimal**|Точное числовое значение|  
|**money**|Точное числовое значение|  
|**smallmoney**|Точное числовое значение|  
|**bigint**|Точное числовое значение|  
|**int**|Точное числовое значение|  
|**smallint**|Точное числовое значение|  
|**tinyint**|Точное числовое значение|  
|**bit**|Точное числовое значение|  
|**nvarchar**|Юникод|  
|**nchar**|Юникод|  
|**varchar**|Юникод|  
|**char**|Юникод|  
|**varbinary**|Двоичный|  
|**binary**|Двоичный|  
|**uniqueidentifier**|Уникальный идентификатор |  
  
К сравнениям типов **sql_variant** применяются указанные ниже правила.
-   При сравнении значений **sql_variant** различных базовых типов данных, находящихся в разных семействах типов данных, большим из двух значений считается то, семейство типа данных которого находится выше в иерархии.  
-   При сравнении значений **sql_variant** различных базовых типов данных, находящихся в одном семействе типов данных, значение, базовый тип данных которого находится ниже в иерархии, неявно приводится к другому типу данных, после чего производится сравнение.  
-   При сравнении значений **sql_variant** с типами данных **char**, **varchar**, **nchar** или **nvarchar** их параметры сортировки сначала сравниваются на основе следующих критериев: код языка, версия кода языка, флаги сравнения и идентификатор сортировки. Каждый из этих критериев сравнивается как целочисленное значение в приведенном порядке. Если все эти критерии равны, то сами строковые значения сравниваются в соответствии с параметрами сортировки.  
  
## <a name="converting-sqlvariant-data"></a>Преобразование данных типа sql_variant  
При обработке типа **sql_variant** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает неявное преобразование объектов других типов данных в тип **sql_variant**. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает неявные преобразования типа **sql_variant** в объекты с другим типом данных.
  
## <a name="restrictions"></a>Ограничения  
В приведенной ниже таблице перечислены типы значений, которые не могут сохраняться с помощью типа данных **sql_variant**.
  
|||  
|-|-|  
|**varchar(max)**|**varbinary(max)**|  
|**nvarchar(max)**|**xml**|  
|**text**|**ntext**|  
|**image**|**rowversion** (**timestamp**)|  
|**sql_variant**|**geography**|  
|**hierarchyid**|**geometry**|  
|Определяемые пользователем типы|**datetimeoffset**<sup>1</sup>| 

<sup>1</sup> SQL Server 2012 и более поздней версии не ограничивает **datetimeoffset**.

## <a name="examples"></a>Примеры  

### <a name="a-using-a-sqlvariant-in-a-table"></a>A. Использование sql_variant в таблице  
 В приведенном ниже примере создается таблица с типом данных sql_variant. Затем извлекаются сведения `SQL_VARIANT_PROPERTY` о значении `colA` `46279.1`, где `colB` =`1689`, при условии, что `tableA` имеет `colA` типа `sql_variant` и `colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)] Обратите внимание на то, что каждое из этих трех значений имеет тип **sql_variant**.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>Б. Использование типа sql_variant в качестве переменной   
 В приведенном ниже примере создается переменная с помощью типа данных sql_variant, а затем извлекаются сведения `SQL_VARIANT_PROPERTY` о переменной с именем @v1.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```    


## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[SQL_VARIANT_PROPERTY (Transact-SQL)](../../t-sql/functions/sql-variant-property-transact-sql.md)
  
  
