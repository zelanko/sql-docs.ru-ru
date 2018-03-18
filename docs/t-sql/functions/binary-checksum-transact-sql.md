---
title: "BINARY_CHECKSUM (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BINARY_CHECKSUM
- BINARY_CHECKSUM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- BINARY_CHECKSUM function
- binary [SQL Server], checksum values
ms.assetid: 07fece4d-58e3-446e-a3b5-92fe24d2d1fb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c5fd777c7ce4ecc4530c47a2e8eb8bb1e14ce2d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="binarychecksum--transact-sql"></a>BINARY_CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Возвращает двоичное значение контрольной суммы, вычисленное для строки таблицы или для списка выражений.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
BINARY_CHECKSUM ( * | expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>Аргументы  
*\**  
Указывает, что вычисление выполняется для всех столбцов таблицы. При выполнении функции BINARY_CHECKSUM столбцы с несопоставимыми типами данных игнорируются. К несопоставимым типам данных относятся **text**, **ntext**, **image**, **cursor**, **xml**, а также несопоставимые пользовательские типы среды CLR.
  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных. При выполнении функции BINARY_CHECKSUM выражения с несопоставимыми типами данных игнорируются.
  
## <a name="remarks"></a>Remarks  
Результат, возвращаемый функцией BINARY_CHECKSUM(*) для строки таблицы, изменяется только при изменении указанной строки. BINARY_CHECKSUM удовлетворяет свойствам хэш-функции. Функция BINARY_CHECKSUM, примененная к любым двум спискам выражений, возвращает одинаковое значение, если при сравнении оператором равенства (=) соответствующие элементы двух списков имеют одинаковый тип и равны. Для данного определения значения NULL указанного типа рассматриваются при сравнении как равные. Если одно из значений в списке выражений меняется, то обычно меняется и контрольная сумма этого списка. Однако существует небольшая вероятность того, что контрольная сумма не изменится. По этой причине использование функции BINARY_CHECKSUM для определения изменения значений не рекомендуется, если приложение не допускает отсутствия изменения. Попробуйте вместо этого использовать функцию HashBytes. Когда указан хэш-алгоритм MD5, вероятность возвращения функцией HashBytes одинакового результата для двух различных входных параметров намного ниже, чем функцией BINARY_CHECKSUM.
  
Функция BINARY_CHECKSUM может применяться к списку выражений, причем ее результаты для данного списка совпадают. Функция BINARY_CHECKSUM вернет одинаковый результат для двух любых списков выражений в том случае, если тип и байтовое представление соответствующих друг другу элементов списков совпадают. В данном случае значения NULL одинакового типа рассматриваются как значения с одинаковым байтовым представлением.
  
Функции BINARY_CHECKSUM и CHECKSUM похожи. Они могут быть использованы для вычисления контрольной суммы списка выражений, при этом порядок следования выражений влияет на значение результата. Порядок следования столбцов, используемый функцией BINARY_CHECKSUM(*), соответствует порядку столбцов в определении таблицы или представления. Это касается и вычисляемых столбцов.
  
Функции CHECKSUM и BINARY_CHECKSUM возвращают различные значения для строковых типов данных, в которых из-за локали строки с различными представлениями могут оказаться эквивалентными. Строковыми типами данных являются **char**, **varchar**, **nchar**, **nvarchar** и **sql_variant** (если базовый тип **sql_variant** — это строковый тип данных). Например, функция BINARY_CHECKSUM возвращает различные результаты для строк McCavity и Mccavity. Однако при использовании функции CHECKSUM на сервере, нечувствительном к регистру, результаты для данных строк совпадают. Не следует сравнивать результаты выполнения функций CHECKSUM и BINARY_CHECKSUM.
 
Функция BINARY_CHECKSUM поддерживает до 8000 символов типа **varbinary(max)** и до 255 символов типа **nvarchar(max)**.
  
## <a name="examples"></a>Примеры  
В следующем примере для выявления изменений в строке таблицы используется функция `BINARY_CHECKSUM`.
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable (column1 int, column2 varchar(256));  
GO  
INSERT INTO myTable VALUES (1, 'test');  
GO  
SELECT BINARY_CHECKSUM(*) from myTable;  
GO  
UPDATE myTable set column2 = 'TEST';  
GO  
SELECT BINARY_CHECKSUM(*) from myTable;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[CHECKSUM (Transact-SQL)](../../t-sql/functions/checksum-transact-sql.md)  
[CHECKSUM_AGG (Transact-SQL)](../../t-sql/functions/checksum-agg-transact-sql.md)
  
  
