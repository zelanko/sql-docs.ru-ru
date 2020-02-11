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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952349"
---
# <a name="descriptor-field-conformance"></a>Соответствие поля дескриптора
В следующей таблице указывается уровень соответствия для каждого поля заголовка ODBC-дескриптора, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Core|  
|SQL_DESC_ARRAY_SIZE|Core|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (для APD, Ипр и IRD); Уровень 1 (для АРД)|  
|SQL_DESC_BIND_OFFSET_PTR|Core|  
|SQL_DESC_BIND_TYPE|Core|  
|SQL_DESC_COUNT|Core|  
|SQL_DESC_ROWS_PROCESSED_PTR|Core|  
  
 В следующей таблице указывается уровень соответствия для каждого поля записи дескриптора ODBC, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Core|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Core|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Core|  
|SQL_DESC_DATA_PTR|Core|  
|КОД SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
|ТОЧНОСТЬ SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
|SQL_DESC_DISPLAY_SIZE|Core|  
|SQL_DESC_FIXED_PREC_SCALE|Core|  
|SQL_DESC_INDICATOR_PTR|Core|  
|SQL_DESC_LABEL|Уровень 2|  
|SQL_DESC_LENGTH|Core|  
|SQL_DESC_LITERAL_PREFIX|Core|  
|SQL_DESC_LITERAL_SUFFIX|Core|  
|SQL_DESC_LOCAL_TYPE_NAME|Core|  
|SQL_DESC_NAME|Core|  
|SQL_DESC_NULLABLE|Core|  
|SQL_DESC_OCTET_LENGTH|Core|  
|SQL_DESC_OCTET_LENGTH_PTR|Core|  
|SQL_DESC_PARAMETER_TYPE|Ядро или уровень 2 [2]|  
|SQL_DESC_PRECISION|Core|  
|SQL_DESC_ROWVER|уровне 1|  
|SQL_DESC_SCALE|Core|  
|SQL_DESC_SCHEMA_NAME|уровне 1|  
|SQL_DESC_SEARCHABLE|Core|  
|SQL_DESC_TABLE_NAME|уровне 1|  
|SQL_DESC_TYPE|Core|  
|SQL_DESC_TYPE_NAME|Core|  
|SQL_DESC_UNNAMED|Core|  
|SQL_DESC_UNSIGNED|Core|  
|SQL_DESC_UPDATABLE|Core|  
  
 [1] Поддержка этих полей записей необходима только в том случае, если драйвер поддерживает применимые типы данных.  
  
 [2] для обеспечения соответствия уровня ядра драйвер должен поддерживать SQL_PARAM_INPUT. Для соответствия интерфейсу уровня 2 драйвер должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
