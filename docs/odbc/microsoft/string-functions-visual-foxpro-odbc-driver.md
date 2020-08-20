---
description: Строковые функции (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ab2ecefb604183b0387a561f72494028c62d15f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471546"
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
