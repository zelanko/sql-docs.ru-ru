---
title: SWITCHOFFSET (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SWITCHTZ
- SWITCHTZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- functions [SQL Server], time
- functions [SQL Server], date and time
- SWITCHOFFSET function [SQL Server]
- time [SQL Server], functions
- date and time [SQL Server], SWITCHOFFSET
- time zones [SQL Server]
ms.assetid: 32a48e36-0aa4-4260-9fe9-cae9197d16c5
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e268bb90bae03cc83953e23960d1c650db51f92c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074597"
---
# <a name="switchoffset-transact-sql"></a>SWITCHOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение смещения часового пояса с типом данных **datetimeoffset**, изменившееся с хранящегося на новое заданное смещение часового пояса.  
  
 Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SWITCHOFFSET ( DATETIMEOFFSET, time_zone )   
```  
  
## <a name="arguments"></a>Аргументы  
 *DATETIMEOFFSET*  
 Выражение, которое можно привести к значению типа **datetimeoffset(n)**.  
  
 *time_zone*  
 Символьная строка в формате [+|-]TZH:TZM или целочисленное значение со знаком (или минуты), представляющие смещение часового пояса. Предполагается, что оно настроено и учитывает переход на летнее время.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Значение **datetimeoffset** с точностью в долях секунд, заданной в аргументе *DATETIMEOFFSET*.  
  
## <a name="remarks"></a>Remarks  
 SWITCHOFFSET используется для выбора значения **datetimeoffset** в смещении часового пояса, отличающегося от первоначально сохраненного смещения часового пояса. SWITCHOFFSET не обновляет хранимое значение *time_zone*.  
  
 Функция SWITCHOFFSET может использоваться для обновления столбца **datetimeoffset**.  
  
 Использование SWITCHOFFSET с функцией GETDATE() может привести к тому, что запрос будет выполняться медленно. Это происходит потому, что оптимизатор запросов не может получить точные оценки количества элементов для значений даты и времени. Чтобы устранить эту проблему, используйте указание запроса OPTION (RECOMPILE), чтобы заставить оптимизатор запросов перекомпилировать план запроса при следующем выполнении этого же запроса. Он будет иметь точные оценки количества элементов и сформирует более эффективный план запроса. Дополнительные сведения об указании запроса RECOMPILE см. в статье [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `SWITCHOFFSET` используется для вывода смещения часового пояса, отличающегося от значения, которое хранится в базе данных.  
  
```  
CREATE TABLE dbo.test   
    (  
    ColDatetimeoffset datetimeoffset  
    );  
GO  
INSERT INTO dbo.test   
VALUES ('1998-09-20 7:45:50.71345 -5:00');  
GO  
SELECT SWITCHOFFSET (ColDatetimeoffset, '-08:00')   
FROM dbo.test;  
GO  
--Returns: 1998-09-20 04:45:50.7134500 -08:00  
SELECT ColDatetimeoffset  
FROM dbo.test;  
--Returns: 1998-09-20 07:45:50.7134500 -05:00  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [AT TIME ZONE (Transact-SQL)](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


