---
title: ПОСЛЕДОВАТЕЛЬНОСТИ (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SEQUENCES
- SEQUENCES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SEQUENCES view
- INFORMATION_SCHEMA.SEQUENCES view
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ff8490824c6a0ccb45b383535e830cabff83407
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "77479352"
---
# <a name="sequences-transact-sql"></a>ПОСЛЕДОВАТЕЛЬНОСТИ (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает по одной строке для каждой последовательности, к которой может получить доступ текущий пользователь в текущей базе данных.

Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA**_. view_name_.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|
|**SEQUENCE_CATALOG**|**nvarchar(128)**|Квалификатор последовательности|
|**SEQUENCE_SCHEMA**|**nvarchar (** 128) * *|Имя схемы, содержащей последовательность|
|**SEQUENCE_NAME**|**nvarchar(128)**|Имя последовательности|
|**DATA_TYPE**|**nvarchar (** 128 **)**|Тип данных Sequence|
|**NUMERIC_PRECISION**|**tinyint**|Точность последовательности|
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|
|**NUMERIC_SCALE**|**int**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|
|**START_VALUE**|**int**|Первое значение, возвращаемое объектом последовательности.|
|**MINIMUM_VALUE**|**int**|Границы для объекта последовательности. По умолчанию минимальным значением для нового объекта последовательности служит минимальное значение для типа данных объекта последовательности. Для типа данных tinyint это ноль, для всех остальных типов данных — отрицательное число.|
|**MAXIMUM_VALUE**|**int**|Границы для объекта последовательности. По умолчанию максимальным значением для нового объекта последовательности служит максимальное значение для типа данных объекта последовательности.|
|**ПРОИЗВОДИМ**|**int**|Значение, на которое увеличивается (или уменьшается, если оно отрицательное) значение объекта последовательности при каждом вызове функции NEXT VALUE FOR. Если значение приращения отрицательно, то объект последовательности убывает, в противном случае — возрастает. Приращение не может быть равно 0. По умолчанию для нового объекта последовательности используется приращение 1.
|**CYCLE_OPTION**|**int**|Свойство, которое указывает, перезапускается объект последовательности с минимального значения (или максимального для объектов убывающих последовательностей) или вызывает исключение, когда достигнуто максимальное (или максимальное) значение. По умолчанию для новых объектов последовательности используется параметр цикличности NO CYCLE.
|**DECLARED_DATA_TYPE**|**int**|Тип данных для определяемого пользователем типа данных.|
|**DECLARED_DATA_PRECISION**|**int**|Точность для определяемого пользователем типа данных.|
|**DECLARED_NUJMERIC_SCALE**|**int**|Числовой масштаб определяемого пользователем типа данных.|

**Пример** В следующем примере возвращаются сведения о схемах в тестовой базе данных:

```sql
SELECT * FROM test.INFORMATION_SCHEMA.SEQUENCES;
```

## <a name="see-also"></a>См. также:

- [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [sys.sequences (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)
