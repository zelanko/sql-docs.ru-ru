---
title: Функции струнных (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 988ba23b95f6b138148b1fa17ad303d7aa2dc895
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299194"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Строковые функции (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены функции манипуляции строками ODBC ODBC Visual FoxPro; когда грамматика Visual FoxPro для той же функции отличается от синтаксиса ODBC, в списке указан эквивалент Visual FoxPro.  
  
|Грамматика ODBC|Визуальная грамматика FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(код)*|CHR *(string_exp)*|  
|КОНКАТ *(string_exp1, string_exp2)*|*string_exp1 и string_exp2*|  
|СИразница *(string_exp1, string_exp2)*||  
|INSERT *(string_exp1, старт, длина, string_exp2)*|STUFF *(string_exp1, старт, длина, string_exp2)*|  
|LCASE *(string_exp)*|LOWER *(string_exp)*|  
|LEFT *(string_exp, кол)*||  
|ДЛИНА *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|REPEAT *(string_exp, кол)*|КОПТЕС *(string_exp, кол)*|  
|REPLACE *(string_exp1, string_exp2, string_exp3)*|СтрТРАН *(string_exp1, string_exp2, string_exp3)*|  
|RIGHT *(string_exp, кол)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|SPACE *(счет)*||  
|SUBSTRING *(string_exp, старт, длина)*|SUBSTR *(string_exp, старт, длина)*|  
|UCASE *(string_exp)*|Upper *(string_exp)*|
