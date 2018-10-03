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
manager: craigg
ms.openlocfilehash: 1a9e1c94eec150cc24522cd6e4c57eb35b4a2126
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854832"
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
