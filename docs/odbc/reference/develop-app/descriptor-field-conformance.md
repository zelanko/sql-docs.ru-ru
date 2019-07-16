---
title: Соответствие поля дескриптора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afdb1f18ad641224d13373436dd58f1919a3d280
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952349"
---
# <a name="descriptor-field-conformance"></a>Соответствие поля дескриптора
Следующая таблица указывает уровень соответствия каждого ODBC поле заголовка дескриптора, где это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Основные сведения|  
|SQL_DESC_ARRAY_SIZE|Основные сведения|  
|SQL_DESC_ARRAY_STATUS_PTR|Основные файлы (для APD Сетевом и IRD); Уровень 1 (Отменить)|  
|SQL_DESC_BIND_OFFSET_PTR|Основные сведения|  
|SQL_DESC_BIND_TYPE|Основные сведения|  
|SQL_DESC_COUNT|Основные сведения|  
|SQL_DESC_ROWS_PROCESSED_PTR|Основные сведения|  
  
 Следующая таблица указывает уровень соответствия каждого ODBC дескриптор записи поля, где это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Основные сведения|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Основные сведения|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Основные сведения|  
|SQL_DESC_DATA_PTR|Основные сведения|  
|КОД SQL_DESC_DATETIME_INTERVAL_|Core [1]|  
|ТОЧНОСТЬ SQL_DESC_DATETIME_INTERVAL_|Core [1]|  
|SQL_DESC_DISPLAY_SIZE|Основные сведения|  
|SQL_DESC_FIXED_PREC_SCALE|Основные сведения|  
|SQL_DESC_INDICATOR_PTR|Основные сведения|  
|SQL_DESC_LABEL|Уровень 2|  
|SQL_DESC_LENGTH|Основные сведения|  
|SQL_DESC_LITERAL_PREFIX|Основные сведения|  
|SQL_DESC_LITERAL_SUFFIX|Основные сведения|  
|SQL_DESC_LOCAL_TYPE_NAME|Основные сведения|  
|SQL_DESC_NAME|Основные сведения|  
|SQL_DESC_NULLABLE|Основные сведения|  
|SQL_DESC_OCTET_LENGTH|Основные сведения|  
|SQL_DESC_OCTET_LENGTH_PTR|Основные сведения|  
|SQL_DESC_PARAMETER_TYPE|Core/уровень 2 [2]|  
|SQL_DESC_PRECISION|Основные сведения|  
|SQL_DESC_ROWVER|уровне 1|  
|SQL_DESC_SCALE|Основные сведения|  
|SQL_DESC_SCHEMA_NAME|уровне 1|  
|SQL_DESC_SEARCHABLE|Основные сведения|  
|SQL_DESC_TABLE_NAME|уровне 1|  
|SQL_DESC_TYPE|Основные сведения|  
|SQL_DESC_TYPE_NAME|Основные сведения|  
|SQL_DESC_UNNAMED|Основные сведения|  
|SQL_DESC_UNSIGNED|Основные сведения|  
|SQL_DESC_UPDATABLE|Основные сведения|  
  
 [1] поддержка эти поля записи является обязательным только в том случае, если драйвер поддерживает применимые типы данных.  
  
 [2] для соответствия требованиям уровня ядра драйвер должен поддерживать SQL_PARAM_INPUT. Соответствие интерфейса уровня 2 драйвер должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
