---
title: "Функция BINARY_CHECKSUM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b84847f3efe7224c6fa0ad945b03f3afbc1381b9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="binarychecksum--transact-sql"></a>Функция BINARY_CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Возвращает двоичное значение контрольной суммы, вычисленное для строки таблицы или для списка выражений.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
BINARY_CHECKSUM ( * | expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>Аргументы  
*\**  
Указывает, что вычисление выполняется для всех столбцов таблицы. При выполнении функции BINARY_CHECKSUM столбцы с несопоставимыми типами данных игнорируются. Несопоставимыми типами данных включают **текст**, **ntext**, **изображения**, **курсор**, **xml**, и несопоставимыми типами среды CLR (CLR) определяемой пользователем.
  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа. При выполнении функции BINARY_CHECKSUM выражения с несопоставимыми типами данных игнорируются.
  
## <a name="remarks"></a>Замечания  
Результат, возвращаемый функцией BINARY_CHECKSUM(*) для строки таблицы, изменяется только при изменении указанной строки. Функция BINARY_CHECKSUM удовлетворяет свойствам хэш-функции: двух любых списков выражений функция BINARY_CHECKSUM возвращает то же значение, если соответствующие элементы двух списков имеют одинаковый тип и равны, по сравнению с оператором равенства (=). Для данного определения значения NULL указанного типа рассматриваются при сравнении как равные. Если одно из значений в списке выражений меняется, то обычно меняется и контрольная сумма этого списка. Однако существует небольшая вероятность того, что контрольная сумма не изменится. По этой причине не рекомендуется использовать BINARY_CHECKSUM, чтобы определить, были ли изменены значения, если приложение допускает отсутствия изменения. Рекомендуется использовать HashBytes. Если указан алгоритм хэширования MD5, вероятность HashBytes, возвращая один и тот же результат для двух различных входных параметров намного меньше, чем, Функция BINARY_CHECKSUM.
  
Функция BINARY_CHECKSUM может применяться к списку выражений, причем ее результаты для данного списка совпадают. Функция BINARY_CHECKSUM вернет одинаковый результат для двух любых списков выражений в том случае, если тип и байтовое представление соответствующих друг другу элементов списков совпадают. В данном случае значения NULL одинакового типа рассматриваются как значения с одинаковым байтовым представлением.
  
Функция BINARY_CHECKSUM и CHECKSUM, аналогичные функции: они могут использоваться для вычисления контрольной суммы списка выражений, а также порядок выражений влияет на результирующее значение. Порядок следования столбцов, используемый функцией BINARY_CHECKSUM(*), соответствует порядку столбцов в определении таблицы или представления. Это касается и вычисляемых столбцов.
  
Функции CHECKSUM и BINARY_CHECKSUM возвращают различные значения для строковых типов данных, в которых из-за локали строки с различными представлениями могут оказаться эквивалентными. Строковыми типами данных являются **char**, **varchar**, **nchar**, **nvarchar**, или **sql_variant** (если базовый тип **sql_variant** является строковым типом данных). Например, функция BINARY_CHECKSUM возвращает различные результаты для строк McCavity и Mccavity. Однако при использовании функции CHECKSUM на сервере, нечувствительном к регистру, результаты для данных строк совпадают. Не следует сравнивать результаты выполнения функций CHECKSUM и BINARY_CHECKSUM.
 
Функция BINARY_CHECKSUM поддерживает до 8 000 символов типа **varbinary(max)** и не более 255 символов типа **nvarchar(max)**.
  
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
  
## <a name="see-also"></a>См. также:
[Агрегатные функции &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[Контрольная сумма &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-transact-sql.md)  
[CHECKSUM_AGG &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-agg-transact-sql.md)
  
  

