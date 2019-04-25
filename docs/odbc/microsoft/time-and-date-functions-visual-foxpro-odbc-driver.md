---
title: Функции даты (драйвер ODBC для Visual FoxPro) и времени | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf8e7552faf9567dab25ee3dc5b7b293034faef0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632774"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Функции даты и времени (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены ODBC функций даты и времени поддерживаются драйвером Visual FoxPro ODBC; Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, Visual FoxPro эквивалентное отображаются.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ФУНКЦИЯ CURDATE *)*|ДАТА *)*|  
|ФУНКЦИЯ CURTIME *)*|ВРЕМЯ *)*|  
|Функция DAYNAME *(выражение_даты)*|CDOW *(выражение_даты)*|  
|DAYOFMONTH (*выражения «выражение_даты»)*|ДЕНЬ *)*|  
|ЧАС *(выражение_времени)*||  
|MINUTE *(time_exp)*||  
|МЕСЯЦ *(выражение_времени)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|ТЕПЕРЬ *)*|DATETIME *)*|  
|ВТОРОЙ *(выражение_времени)*|SEC *(time_exp)*|  
|НЕДЕЛЯ *(выражение_даты)*||  
|ГОД *(выражение_даты)*||  
  
 Не поддерживаются следующие функции даты и времени:  
  
 DAYOFYEAR *(выражение_даты)*  
  
 КВАРТАЛ *(выражение_даты)*  
  
 TIMESTAMPADD *(интервал, целое_выражение, timestamp_exp)*  
  
 TIMESTAMPDIFF *(интервал, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Escape-последовательности ODBC  
 Драйвер также поддерживает escape-последовательность ODBC для данных date и timestamp. Синтаксис escape-предложении выглядит следующим образом:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 В этом синтаксисе **d** указывает, что *значение* является датой в *гггг мм дд* формат и **служб терминалов** указывает, что *значение*  представляет собой метку времени в *гггг мм дд чч: мм:*[.*f...*] формат. Сокращенный синтаксис для данных date и timestamp выглядит следующим образом:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Например каждый из следующих инструкций обновляет ALLTYPES таблицу с помощью сокращенный синтаксис date и timestamp в поддерживаемых команду SQL UPDATE:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об escape-последовательностях см. в разделе [escape-последовательности в ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) в *Справочник по программированию ODBC*.
