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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948777"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Строковые функции (драйвер ODBC для Visual FoxPro)
В следующей таблице перечислены функции обработки строк ODBC, поддерживаемых драйвером Visual FoxPro ODBC; Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, Visual FoxPro эквивалентное отображаются.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(строковое_выражение)*|ASC *(строковое_выражение)*|  
|CHAR *(код)*|CHR *(строковое_выражение)*|  
|CONCAT *(строковое_выражение1, строковое_выражение2)*|*строковое_выражение1 + строковое_выражение2*|  
|РАЗЛИЧИЕ *(строковое_выражение1, строковое_выражение2)*||  
|Вставить *(строковое_выражение1, начало, длина, строковое_выражение2)*|STUFF *(строковое_выражение1, начало, длина, строковое_выражение2)*|  
|LCASE *(строковое_выражение)*|НИЖНИЙ *(строковое_выражение)*|  
|СЛЕВА *(строковое_выражение, число)*||  
|Длина *(строковое_выражение)*|LEN *(строковое_выражение)*|  
|LTRIM *(строковое_выражение)*||  
|ПОВТОРИТЕ *(строковое_выражение, число)*|РЕПЛИЦИРОВАТЬ *(строковое_выражение, число)*|  
|ЗАМЕНИТЕ *(строковое_выражение1, строковое_выражение2, string_exp3)*|STRTRAN *(строковое_выражение1, строковое_выражение2, string_exp3)*|  
|СПРАВА *(строковое_выражение, число)*||  
|RTRIM *(строковое_выражение)*||  
|SOUNDEX *(строковое_выражение)*||  
|ПРОСТРАНСТВО *(количество)*||  
|Подстрока *(строковое_выражение, начало, длина)*|SUBSTR *(строковое_выражение, начало, длина)*|  
|UCASE *(строковое_выражение)*|Верхний *(строковое_выражение)*|
