---
title: Оскверненное поле Соответствие (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce33adfdbfceef56936b22c549b6762521b4798
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305935"
---
# <a name="descriptor-field-conformance"></a>Соответствие поля дескриптора
В следующей таблице указывается уровень соответствия каждого поля заголовка дескриптора ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Основные сведения|  
|SQL_DESC_ARRAY_SIZE|Основные сведения|  
|SQL_DESC_ARRAY_STATUS_PTR|Ядро (для APD, ПИС и IRD); Уровень 1 (для ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Основные сведения|  
|SQL_DESC_BIND_TYPE|Основные сведения|  
|SQL_DESC_COUNT|Основные сведения|  
|SQL_DESC_ROWS_PROCESSED_PTR|Основные сведения|  
  
 В следующей таблице указывается уровень соответствия каждого поля записи дескриптора ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Основные сведения|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Основные сведения|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Основные сведения|  
|SQL_DESC_DATA_PTR|Основные сведения|  
|SQL_DESC_DATETIME_INTERVAL_ КОД|Ядро|  
|SQL_DESC_DATETIME_INTERVAL_ PRECISION|Ядро|  
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
|SQL_DESC_PARAMETER_TYPE|Ядро/Уровень 2'2|  
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
  
 Поддержка этих полей записи требуется только в том случае, если драйвер поддерживает применимые типы данных.  
  
 Для соответствия уровня Core водитель должен поддерживать SQL_PARAM_INPUT. Для соответствия интерфейса уровня 2 водитель должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
