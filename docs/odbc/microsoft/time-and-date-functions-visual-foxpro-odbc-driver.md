---
title: Функции даты и времени (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.openlocfilehash: 537af13edf943e27a634d3a8ba4f0f85c645251f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912405"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Функции даты и времени (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены функции времени и даты ODBC, поддерживаемые драйвером ODBC для Visual FoxPro. Если грамматика Visual FoxPro для той же функции отличается от синтаксиса ODBC, в списке отображается эквивалент Visual FoxPro.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|CURDATE *()*|DATE *()*|  
|КУРТИМЕ *()*|ВРЕМЯ *()*|  
|ДАЙНАМЕ *(date_exp)*|КДОВ *(date_exp)*|  
|DAYOFMONTH (*date_exp)*|DAY *()*|  
|ЧАС *(time_exp)*||  
|МИНУТа *(time_exp)*||  
|МЕСЯЦ *(time_exp)*||  
|MONTHNAME *(date_exp)*|КМОНС *(date_exp)*|  
|NOW *()*|DATETIME *()*|  
|Второе *(time_exp)*|С *(time_exp)*|  
|WEEK *(date_exp)*||  
|YEAR *(date_exp)*||  
  
 Следующие функции даты и времени не поддерживаются:  
  
 DAYOFYEAR *(date_exp)*  
  
 КВАРТАЛ *(date_exp)*  
  
 ТИМЕСТАМПАДД *(интервал, integer_exp, timestamp_exp)*  
  
 ТИМЕСТАМПДИФФ *(интервал, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Escape-последовательности ODBC  
 Драйвер также поддерживает escape-последовательность ODBC для данных даты и отметок времени. Синтаксис предложения escape выглядит следующим образом:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 В этом синтаксисе **d** указывает, что *значение* является датой в формате *гггг-мм-дд* , а **TS** указывает, что это *значение* является меткой времени в *гггг-мм-дд чч: мм: СС*[.* f...*] формат. Ниже приведен краткий синтаксис для данных даты и отметок времени.  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Например, каждая из следующих инструкций обновляет таблицу АЛЛТИПЕС с помощью краткого синтаксиса Date и timestamp в поддерживаемой команде SQL UPDATE:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о escape-последовательностям см. в разделе [escape-последовательности в ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) в *справочнике программиста ODBC*.
