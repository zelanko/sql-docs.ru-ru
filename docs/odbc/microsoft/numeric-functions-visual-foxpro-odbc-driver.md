---
title: Числовые функции (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f577938577be95c7e2c506dbb542a2224f5929e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902099"
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
