---
title: APPROX_COUNT_DISTINCT (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/23/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- APPROX_COUNT_DISTINCT
dev_langs:
- TSQL
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1978f22adf54f13d04df0b103ebe5f37a4eac7b4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077574"
---
# <a name="approxcountdistinct-transact-sql"></a>APPROX_COUNT_DISTINCT (Transact-SQL)
[!INCLUDE[appliesto-xx-asdb-asdw-pdw-md](../../includes/appliesto-xx-asdb-asdw-pdw-md.md)]

Эта функция возвращает приблизительное количество уникальных значений, не равных NULL, в группе. 
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

> [!NOTE]
> APPROX_COUNT_DISTINCT — эта функция предоставляется в режиме общедоступной предварительной версии.  
  
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

`APPROX_COUNT_DISTINCT` использует меньше памяти, чем длительная операция COUNT DISTINCT.  Если сравнивать с точной операцией COUNT DISTINCT, то с учетом меньшего объема используемой памяти уменьшается и вероятность того, что `APPROX_COUNT_DISTINCT` память будет выгружаться на диск. 

> [!NOTE]
> С помощью строк, зависимых от параметров сортировки, общедоступная предварительная версия APPROX_COUNT_DISTINCT использует совпадение двоичных значений и предоставляет результаты, которые могли быть созданы при наличии параметров сортировки BIN, но не BIN2. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-approxcountdistinct"></a>A. Использование функции APPROX_COUNT_DISTINCT 
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
  
### <a name="b-using-approxcountdistinct-with-group-by"></a>Б. Использование функции APPROX_COUNT_DISTINCT с фильтром GROUP BY 
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
