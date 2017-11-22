---
title: "Числовые функции (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fa1e5111769f3c30b969e7a9176d7d92e9c870db
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Числовые функции (Visual FoxPro драйвер ODBC)
В следующей таблице описаны числовые функции ODBC, поддерживаемые Visual FoxPro драйвера ODBC. Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, отображается Visual FoxPro эквивалент.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(числовое_выражение)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1 float_exp2)*|ATN2 (*float_exp1 float_exp2*)|  
|Верхний ПРЕДЕЛ *(числовое_выражение)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|ГРАДУСЫ *(числовое_выражение)*|RTOD *(числовое_выражение)*|  
|EXP *(float_exp)*||  
|Функция FLOOR *(числовое_выражение)*||  
|ЖУРНАЛ *(float_exp)*||  
|LOG10 *(float_exp)*||  
|Остаток от деления *(integer_exp1 integer_exp2)*||  
|PI *)*||  
|RADIANS *(числовое_выражение)*|DTOR *(числовое_выражение)*|  
|Функция RAND *([целое_выражение])*||  
|ROUND *(числовое_выражение, целое_выражение)*||  
|ЗНАК *(числовое_выражение)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 Следующие числовые функции не поддерживаются:  
  
 POWER *(числовое_выражение, целое_выражение)*  
  
 УСЕЧЕНИЕ *(числовое_выражение, целое_выражение)*
