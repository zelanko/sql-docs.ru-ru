---
title: "Поля соответствия дескриптора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 049208450144fdd1c1d3b902093517627486ccf9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-field-conformance"></a>Дескриптор поля соответствия
Следующая таблица указывает уровень соответствия для каждого ODBC поле заголовка дескриптора, где это является правильно определенным.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Основные сведения|  
|SQL_DESC_ARRAY_SIZE|Основные сведения|  
|SQL_DESC_ARRAY_STATUS_PTR|Основные файлы (для APD прав на интеллектуальную собственность и IRD); Уровень 1 (для Отменить)|  
|SQL_DESC_BIND_OFFSET_PTR|Основные сведения|  
|SQL_DESC_BIND_TYPE|Основные сведения|  
|SQL_DESC_COUNT|Основные сведения|  
|SQL_DESC_ROWS_PROCESSED_PTR|Основные сведения|  
  
 Следующая таблица указывает уровень соответствия каждого ODBC дескриптор записи поля, где это является правильно определенным.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Основные сведения|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Основные сведения|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Основные сведения|  
|SQL_DESC_DATA_PTR|Основные сведения|  
|КОД SQL_DESC_DATETIME_INTERVAL_|Основные [1]|  
|ТОЧНОСТЬ SQL_DESC_DATETIME_INTERVAL_|Основные [1]|  
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
|SQL_DESC_PARAMETER_TYPE|Основной или уровне 2 [2]|  
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
  
 [1] требуется поддержка этих полях записи только в том случае, если драйвер поддерживает применимые типы данных.  
  
 [2] на уровне ядра соответствие драйвер должен поддерживать SQL_PARAM_INPUT. Для соответствия интерфейс уровня 2 драйвер должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
