---
title: "Контрольная сумма (Transact-SQL) | Документы Microsoft"
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
- CHECKSUM_TSQL
- CHECKSUM
dev_langs:
- TSQL
helpviewer_keywords:
- hash indexes
- CHECKSUM function
- checksum values
ms.assetid: e26d3339-845c-49c2-9d89-243376874c13
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: d41736f6ac216de0ecf755cbf7ca73ba34a697b8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="checksum-transact-sql"></a>CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Возвращает значение контрольной суммы, вычисленное для строки таблицы или для списка выражений. Функция CHECKSUM предназначена для построения хэш-индексов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CHECKSUM ( * | expression [ ,...n ] )  
```  
  
## <a name="arguments"></a>Аргументы  
\*  
Указывает на то, что вычисление производится по всем столбцам таблицы. Функция CHECKSUM возвращает ошибку, если какой-либо столбец содержит несопоставимый тип данных. Несопоставимыми типами данных являются **текст**, **ntext**, **изображения**, XML, и **курсор**и также **sql_variant**с одним из вышеперечисленных типов, как базовый тип.
  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа за исключением несопоставимого типа данных.
  
## <a name="return-types"></a>Возвращаемые типы
 **int**  
  
## <a name="remarks"></a>Замечания  
Функция CHECKSUM вычисляет хэш-значение, которое называется контрольной суммой, из списка своих аргументов. Хэш-значение предназначено для построения хэш-индексов. Если аргументы функции CHECKSUM являются столбцами, а индекс построен на рассчитанном значении CHECKSUM, то в результате получится хэш-индекс. Он может использоваться для поиска равенств в столбцах.
  
CHECKSUM удовлетворяет свойствам хэш-функции: Функция CHECKSUM, примененная к двум любым спискам выражений возвращает то же значение, если соответствующие элементы двух списков имеют одинаковый тип и равны, по сравнению с оператором равенства (=). Для данного определения значения NULL указанного типа рассматриваются при сравнении как равные. Если одно из значений в списке выражений меняется, то обычно меняется и контрольная сумма этого списка. Однако существует небольшая вероятность того, что контрольная сумма не изменится. По этой причине использование функции CHECKSUM для определения изменения значений не рекомендуется, если приложение не допускает отсутствия изменения. Рассмотрите возможность использования [HashBytes](../../t-sql/functions/hashbytes-transact-sql.md) вместо него. Когда указан алгоритм хэширования MD5, вероятность возвращения функцией HashBytes одного результата для двух различных входных параметров намного ниже, чем функцией CHECKSUM.
  
Порядок выражений влияет на результирующее значение CHECKSUM. Порядок столбцов, используемый с CHECKSUM(*), является порядком столбцов, указанным в таблице или определении представления. Он включает в себя вычисляемые столбцы.
  
Значение CHECKSUM зависит от параметров сортировки. Такое же значение, сохраненное с другими параметрами сортировки, возвратит другое значение CHECKSUM.
  
## <a name="examples"></a>Примеры  
Следующие примеры показывают, как нужно использовать `CHECKSUM` для построения хэш-индексов. Хэш-индекс строится в результате добавления столбца рассчитанной контрольной суммы к индексируемой таблице и последующего построения индекса по столбцу контрольной суммы.
  
```sql
-- Create a checksum index.  
SET ARITHABORT ON;  
USE AdventureWorks2012;   
GO  
ALTER TABLE Production.Product  
ADD cs_Pname AS CHECKSUM(Name);  
GO  
CREATE INDEX Pname_index ON Production.Product (cs_Pname);  
GO  
```  
  
Индекс контрольной суммы может быть использован как хэш-индекс, особенно для ускорения индексации, если индексируемый столбец представляет собой длинный символьный столбец. Индекс контрольной суммы может быть использован для поиска равенств.
  
```sql
/*Use the index in a SELECT query. Add a second search   
condition to catch stray cases where checksums match,   
but the values are not the same.*/  
SELECT *   
FROM Production.Product  
WHERE CHECKSUM(N'Bearing Ball') = cs_Pname  
AND Name = N'Bearing Ball';  
GO  
```  
  
Создание индекса по вычисляемому столбцу материализует столбец контрольной суммы, и любые изменения для значения `ProductName` будут распространены на столбец контрольной суммы. Иным способом индекс мог бы быть построен непосредственно по индексируемому столбцу. Однако если ключевые значения длинные, то обычный индекс вряд ли будет работать так же хорошо, как индекс контрольной суммы.
  
## <a name="see-also"></a>См. также:
[CHECKSUM_AGG &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[HASHBYTES &#40; Transact-SQL &#41;](../../t-sql/functions/hashbytes-transact-sql.md)  
[Функция BINARY_CHECKSUM &#40; Transact-SQL &#41;](../../t-sql/functions/binary-checksum-transact-sql.md)
  
  
