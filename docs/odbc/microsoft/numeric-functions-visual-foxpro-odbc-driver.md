---
title: Числовые функции (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34d2ceb19bce2e466ff5cae7647125e94fdb7c03
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044996"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Числовые функции (драйвер ODBC для Visual FoxPro)
В следующей таблице описаны числовые функции ODBC, поддерживаемых драйвером Visual FoxPro ODBC; Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, Visual FoxPro эквивалентное отображаются.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(выражение «числовое_выражение»)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1 float_exp2)*|ATN2 (*float_exp1 float_exp2*)|  
|CEILING *(выражение «числовое_выражение»)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|ГРАДУСОВ *(выражение «числовое_выражение»)*|RTOD *(выражение «числовое_выражение»)*|  
|EXP *(float_exp)*||  
|Функция FLOOR *(выражение «числовое_выражение»)*||  
|ЖУРНАЛ *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1 integer_exp2)*||  
|PI *)*||  
|RADIANS *(выражение «числовое_выражение»)*|DTOR *(выражение «числовое_выражение»)*|  
|Функция RAND *([целое_выражение])*||  
|ROUND *(выражение «числовое_выражение», целое_выражение)*||  
|ЗНАК *(выражение «числовое_выражение»)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 Следующие числовые функции не поддерживаются:  
  
 POWER *(выражение «числовое_выражение», целое_выражение)*  
  
 УСЕЧЬ *(выражение «числовое_выражение», целое_выражение)*
