---
title: APPROX_COUNT_DISTINCT (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APPROX_COUNT_DISTINCT
dev_langs:
- TSQL
author: joesackmsft
ms.author: josack
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56485f088d375ceffaadb923999f27f794acb5c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "77568117"
---
# <a name="approx_count_distinct-transact-sql"></a>APPROX_COUNT_DISTINCT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает приблизительное количество уникальных значений, не равных NULL, в группе. 
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse  

APPROX_COUNT_DISTINCT ( expression )   
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа, кроме **image**, **sql_variant**, **ntext** и **text**. 

## <a name="return-types"></a>Типы возвращаемых данных
 **bigint**  
  
## <a name="remarks"></a>Remarks  
Функция `APPROX_COUNT_DISTINCT( expression )` вычисляет выражение для каждой строки в группе и возвращает приблизительное количество уникальных значений, не равных NULL, в группе. Эта функция предназначена для агрегирования в больших наборах данных, для которых скорость реагирования намного важнее абсолютной точности.  

Функция `APPROX_COUNT_DISTINCT` предназначена для использования в сценариях использования больших данных и оптимизирована для следующих условий:
- доступ из наборов данных, содержащих миллионы или более строк, *И*
- агрегирование данных одного или нескольких столбцов с большим количеством различных значений.

Реализация функции гарантирует до 2 % ошибок с вероятностью 97 %. 

`APPROX_COUNT_DISTINCT` использует меньше памяти, чем длительная операция COUNT DISTINCT.  Если сравнивать с точной операцией COUNT DISTINCT, то с учетом меньшего объема используемой памяти уменьшается и вероятность того, что `APPROX_COUNT_DISTINCT` память будет выгружаться на диск. См. дополнительные сведения о [HyperLogLog](https://en.wikipedia.org/wiki/HyperLogLog).

> [!NOTE]
> С помощью строк, зависимых от параметров сортировки, APPROX_COUNT_DISTINCT использует совпадение двоичных значений и предоставляет результаты, которые могли быть созданы при наличии параметров сортировки BIN, но не BIN2. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-approx_count_distinct"></a>A. Использование функции APPROX_COUNT_DISTINCT 
В этом примере функция возвращает приблизительное количество ключей различных заказов из таблицы "Заказы".
  
```sql
SELECT APPROX_COUNT_DISTINCT(O_OrderKey) AS Approx_Distinct_OrderKey
FROM dbo.Orders;
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Approx_Distinct_OrderKey
------------------------
15164704
```
  
### <a name="b-using-approx_count_distinct-with-group-by"></a>Б. Использование функции APPROX_COUNT_DISTINCT с фильтром GROUP BY 
В этом примере функция возвращает приблизительное количество ключей различных заказов, отфильтрованных по состоянию заказов из таблицы "Заказы". 
  
```sql
SELECT O_OrderStatus, APPROX_COUNT_DISTINCT(O_OrderKey) AS Approx_Distinct_OrderKey
FROM dbo.Orders
GROUP BY O_OrderStatus
ORDER BY O_OrderStatus; 
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
O_OrderStatus                                                    Approx_Distinct_OrderKey
---------------------------------------------------------------- ------------------------
F                                                                7397838
O                                                                7387803
P                                                                388036
```
    
## <a name="see-also"></a>См. также раздел
[Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT (Transact-SQL)](../../t-sql/functions/count-transact-sql.md) 
