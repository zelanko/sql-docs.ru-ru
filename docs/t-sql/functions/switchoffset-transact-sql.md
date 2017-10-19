---
title: "SWITCHOFFSET (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/02/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 3c81153c233e68d12347dc47ae9c232f4a5ee030
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="switchoffset-transact-sql"></a>SWITCHOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает **datetimeoffset** значение, которое меняется с смещение часового пояса, хранимые на указанный новый смещение часового пояса.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SWITCHOFFSET ( DATETIMEOFFSET, time_zone )   
```  
  
## <a name="arguments"></a>Аргументы  
 *DATETIMEOFFSET*  
 Выражение, которое разрешается к **datetimeoffset(n)** значение.  
  
 *time_zone*  
 Символьная строка в формате [+|-]TZH:TZM или целочисленное значение со знаком (или минуты), представляющие смещение часового пояса. Предполагается, что оно настроено и учитывает переход на летнее время.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **DateTimeOffset** с точностью в долях *DATETIMEOFFSET* аргумент.  
  
## <a name="remarks"></a>Замечания  
 Switchoffset используется для выбора **datetimeoffset** значение смещения часового пояса, которое отличается от смещения часового пояса, которое было изначально сохранено. SWITCHOFFSET не обновляет хранимое *time_zone* значение.  
  
 SWITCHOFFSET может использоваться для обновления **datetimeoffset** столбца.  
  
 Использование SWITCHOFFSET с функцией GETDATE() может привести к тому, что запрос будет выполняться медленно. Это происходит потому, что оптимизатор запросов не может получить точные оценки количества элементов для значений даты и времени. Чтобы устранить эту проблему, используйте указание запроса OPTION (RECOMPILE), чтобы заставить оптимизатор запросов перекомпилировать план запроса при следующем выполнении этого же запроса. Он будет иметь точные оценки количества элементов и сформирует более эффективный план запроса. Дополнительные сведения об указании запроса RECOMPILE см. в разделе [указания запросов &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-query.md).  
  
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
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



