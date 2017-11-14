---
title: "Время и функции даты (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bab52b29d54416dca84d18cb0cd2b832da1b4d63
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Время и функции даты (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены ODBC функций даты и времени поддерживаются драйвером Visual FoxPro ODBC; Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, отображается Visual FoxPro эквивалент.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ФУНКЦИЯ CURDATE*)*|ДАТА*)*|  
|CURTIME*)*|ВРЕМЯ*)*|  
|DAYNAME*(выражение_даты)*|CDOW*(выражение_даты)*|  
|DAYOFMONTH (*выражение_даты)*|ДЕНЬ*)*|  
|ЧАС*(выражение_времени)*||  
|МИНУТЫ*(выражение_времени)*||  
|МЕСЯЦ*(выражение_времени)*||  
|Функция MONTHNAME*(выражение_даты)*|CMONTH*(выражение_даты)*|  
|ТЕПЕРЬ*)*|DATETIME*)*|  
|ВТОРОЙ*(выражение_времени)*|СЕК*(выражение_времени)*|  
|НЕДЕЛИ*(выражение_даты)*||  
|ГОД*(выражение_даты)*||  
  
 Не поддерживаются следующие функции даты и времени:  
  
 DAYOFYEAR *(выражение_даты)*  
  
 КВАРТАЛ *(выражение_даты)*  
  
 TIMESTAMPADD *(интервал, целое_выражение, timestamp_exp)*  
  
 TIMESTAMPDIFF *(интервал, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Escape-последовательности ODBC  
 Драйвер также поддерживает escape-последовательность ODBC для данных date и timestamp. Синтаксис предложения escape выглядит следующим образом:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)—  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)—  
```  
  
 В этом синтаксисе **d** указывает, что *значение* является датой в *гггг мм дд* формат и **служб терминалов** указывает, что *значение*  представляет собой метку времени в *гггг мм дд чч*[. *f...* ] формата. Сокращенный синтаксис для данных date и timestamp выглядит следующим образом:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Например каждая из следующих инструкций обновляет эту таблицу ALLTYPES с помощью сокращенный синтаксис date и timestamp в поддерживаемых команде SQL UPDATE:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения об escape-последовательностях см. в разделе [Escape-последовательности ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) в *справочнике программиста ODBC*.

