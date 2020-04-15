---
title: Внешнее соединение Побег последовательность (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37ce446328d263f492cdfd369f6e8f9f64fe6dfc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303615"
---
# <a name="outer-join-escape-sequence"></a>Escape-последовательность внешнего соединения
ODBC использует последовательности побега для внешних соединений. Синтаксис этой последовательности побега заключается в следующем:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Remarks  
 В обозначении BNF синтаксис заключается следующим образом:  
  
 *ODBC-внешний-выход::*  
  
 *ODBC-esc-инициатор* oj *внешний-присоединиться ODBC-эск-терминатор*  
  
 *внешнее соединение* ::» *название таблицы* и*корреляция-&#124;*&#124; имя  
  
 АУТЕР СИОНЕ-*имя таблицы* -*корреляция-имя*- &#124; *внешнее соединение*- ON  
  
 *поиск-*  
  
 *Состояние*  
  
 *корреляция-имя* ::» *пользователь-определенное имя*  
  
 *ODBC-esc-инициатор* :::  
  
 *ODBC-esc-терминатор* :::  
  
 Чтобы определить, какие части этого оператора поддерживаются, приложение вызывает **s'LGetInfo** с SQL_OJ_CAPABILITIES типом информации. Для внешних соединений *условие поиска* должно содержать только условие соединения между указанными *именами таблиц.*
