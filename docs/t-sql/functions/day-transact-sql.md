---
title: DAY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a58ac7e29f6a7c41fd0b8e617a04b9a52368fd15
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011376"
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Эта функция возвращает целое число, представляющее дату (день месяца) указанного значения типа *date*.
  
Обзор всех типов данных и функций даты и времени в языке [ см. в статье ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)Типы данных и функции даты и времени (Transact-SQL)[!INCLUDE[tsql](../../includes/tsql-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Аргументы  
*date*  
Выражение, которое разрешается в один из следующих типов данных:

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Для *date*`DAY` будет принимать столбец выражения, выражение, строковый литерал или определяемую пользователем переменную.
  
## <a name="return-type"></a>Тип возвращаемых данных  
**int**
  
## <a name="return-value"></a>Возвращаемое значение  
Функция DAY возвращает то же значение, что и [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Если дата *date* содержит только компонент времени, функция `DAY` возвращает значение, равное 1, базовому дню.
  
## <a name="examples"></a>Примеры  
Приведенная ниже инструкция возвращает `30`, номер самого дня.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
Эта инструкция возвращает `1900, 1, 1`. Аргумент *date* имеет числовое значение `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


