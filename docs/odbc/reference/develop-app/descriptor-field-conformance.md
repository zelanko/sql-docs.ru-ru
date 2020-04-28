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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce33adfdbfceef56936b22c549b6762521b4798
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305935"
---
# <a name="descriptor-field-conformance"></a>Соответствие поля дескриптора
В следующей таблице указывается уровень соответствия для каждого поля заголовка ODBC-дескриптора, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Ядро|  
|SQL_DESC_ARRAY_SIZE|Ядро|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (для APD, Ипр и IRD); Уровень 1 (для АРД)|  
|SQL_DESC_BIND_OFFSET_PTR|Ядро|  
|SQL_DESC_BIND_TYPE|Ядро|  
|SQL_DESC_COUNT|Ядро|  
|SQL_DESC_ROWS_PROCESSED_PTR|Ядро|  
  
 В следующей таблице указывается уровень соответствия для каждого поля записи дескриптора ODBC, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Ядро|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Ядро|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Ядро|  
|SQL_DESC_DATA_PTR|Ядро|  
|КОД SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
|ТОЧНОСТЬ SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
|SQL_DESC_DISPLAY_SIZE|Ядро|  
|SQL_DESC_FIXED_PREC_SCALE|Ядро|  
|SQL_DESC_INDICATOR_PTR|Ядро|  
|SQL_DESC_LABEL|Уровень 2|  
|SQL_DESC_LENGTH|Ядро|  
|SQL_DESC_LITERAL_PREFIX|Ядро|  
|SQL_DESC_LITERAL_SUFFIX|Ядро|  
|SQL_DESC_LOCAL_TYPE_NAME|Ядро|  
|SQL_DESC_NAME|Ядро|  
|SQL_DESC_NULLABLE|Ядро|  
|SQL_DESC_OCTET_LENGTH|Ядро|  
|SQL_DESC_OCTET_LENGTH_PTR|Ядро|  
|SQL_DESC_PARAMETER_TYPE|Ядро или уровень 2 [2]|  
|SQL_DESC_PRECISION|Ядро|  
|SQL_DESC_ROWVER|уровне 1|  
|SQL_DESC_SCALE|Ядро|  
|SQL_DESC_SCHEMA_NAME|уровне 1|  
|SQL_DESC_SEARCHABLE|Ядро|  
|SQL_DESC_TABLE_NAME|уровне 1|  
|SQL_DESC_TYPE|Ядро|  
|SQL_DESC_TYPE_NAME|Ядро|  
|SQL_DESC_UNNAMED|Ядро|  
|SQL_DESC_UNSIGNED|Ядро|  
|SQL_DESC_UPDATABLE|Ядро|  
  
 [1] Поддержка этих полей записей необходима только в том случае, если драйвер поддерживает применимые типы данных.  
  
 [2] для обеспечения соответствия уровня ядра драйвер должен поддерживать SQL_PARAM_INPUT. Для соответствия интерфейсу уровня 2 драйвер должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
