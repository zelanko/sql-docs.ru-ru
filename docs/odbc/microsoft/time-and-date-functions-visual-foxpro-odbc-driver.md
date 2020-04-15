---
title: Функции времени и даты (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86260f8e7245bed15122d4dbfc4649131674e17f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303065"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Функции даты и времени (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены функции времени и даты ODBC, поддерживаемые Visual FoxPro ODBC Driver; когда грамматика Visual FoxPro для той же функции отличается от синтаксиса ODBC, в списке указан эквивалент Visual FoxPro.  
  
|Грамматика ODBC|Визуальная грамматика FoxPro|  
|------------------|---------------------------|  
|КУРДАТ *()*|ДАТА *( )*|  
|КУРТАЙМ *( )*|ВРЕМЯ *()*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH *(date_exp)*|ДЕНЬ *( )*|  
|ЧАС *(time_exp)*||  
|МИНУТА *(time_exp)*||  
|МЕСЯЦ *(time_exp)*||  
|МЕСЯЦАМ *(date_exp)*|CMONTH *(date_exp)*|  
|ТЕПЕРЬ *()*|ДАТА *( )*|  
|ВТОРОЙ *(TIME_EXP)*|SEC *(time_exp)*|  
|НЕДЕЛЯ *(date_exp)*||  
|ГОД *(date_exp)*||  
  
 Функции времени и даты не поддерживаются:  
  
 DAYOFYEAR *(date_exp)*  
  
 КВАРТЕР *(date_exp)*  
  
 TIMESTAMPADD *(интервал, integer_exp, timestamp_exp)*  
  
 TIMESTAMPDIFF *(интервал, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Escape-последовательности ODBC  
 Драйвер также поддерживает последовательность побега ODBC для данных даты и метки времени. Синтаксис оговорки о побеге заключается в следующем:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 В этом синтаксисе, **d** указывает, что *значение* является датой в формате *yyyy-mm-dd,* а **ts** указывает на то, что *значение* является меткой времени в *yyyy-mm-dd hhh:mm:ss.** f...* Формат. Краткое синтаксис для данных о дате и метке времени следующим образом:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Например, каждое из следующих утверждений обновляет таблицу ALLTYPES, используя синтаксис с датаю и временной меткой в поддерживаемой команде ОБНОВЛЕНИЕ S'L UPDATE:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Remarks  
 Для получения дополнительной информации о последовательности побега, [см. Побег последовательности в ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) в *справке ПРОГРАММИСТа ODBC*.
