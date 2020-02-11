---
title: Строковые функции (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db1fbaffbee0f74625f4a11cad3b961f194e3829
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948777"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Строковые функции (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены функции обработки строк ODBC, поддерживаемые драйвером ODBC для Visual FoxPro. Если грамматика Visual FoxPro для той же функции отличается от синтаксиса ODBC, в списке отображается эквивалент Visual FoxPro.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(код)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|Разница *(string_exp1, string_exp2)*||  
|INSERT *(string_exp1, начало, длина, string_exp2)*|МАТЕРИАЛЫ *(string_exp1, начало, длина, string_exp2)*|  
|ЛКАСЕ *(string_exp)*|НИЖЕ *(string_exp)*|  
|LEFT *(string_exp, количество)*||  
|Длина *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|Повтор *(string_exp, количество)*|РЕПЛИКАЦИя *(string_exp, количество)*|  
|Replace *(string_exp1, string_exp2, string_exp3)*|СТРТРАН *(string_exp1, string_exp2, string_exp3)*|  
|RIGHT *(string_exp, количество)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|ПРОБЕЛ *(количество)*||  
|Подстрока *(string_exp, начало, длина)*|SUBSTR *(string_exp, начало, длина)*|  
|УКАСЕ *(string_exp)*|UPPER *(string_exp)*|
