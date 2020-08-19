---
description: Соответствие поля дескриптора
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
ms.openlocfilehash: 36687cf456f4fcbbaa3f4b029e51098815dec3f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476746"
---
# <a name="descriptor-field-conformance"></a>Соответствие поля дескриптора
В следующей таблице указывается уровень соответствия для каждого поля заголовка ODBC-дескриптора, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Основные сведения|  
|SQL_DESC_ARRAY_SIZE|Основные сведения|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (для APD, Ипр и IRD); Уровень 1 (для АРД)|  
|SQL_DESC_BIND_OFFSET_PTR|Основные сведения|  
|SQL_DESC_BIND_TYPE|Основные сведения|  
|SQL_DESC_COUNT|Основные сведения|  
|SQL_DESC_ROWS_PROCESSED_PTR|Основные сведения|  
  
 В следующей таблице указывается уровень соответствия для каждого поля записи дескриптора ODBC, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Уровень 2|  
|SQL_DESC_BASE_COLUMN_NAME|Основные сведения|  
|SQL_DESC_BASE_TABLE_NAME|уровне 1|  
|SQL_DESC_CASE_SENSITIVE|Основные сведения|  
|SQL_DESC_CATALOG_NAME|Уровень 2|  
|SQL_DESC_CONCISE_TYPE|Основные сведения|  
|SQL_DESC_DATA_PTR|Основные сведения|  
|КОД SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
|ТОЧНОСТЬ SQL_DESC_DATETIME_INTERVAL_|Ядро [1]|  
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
|SQL_DESC_PARAMETER_TYPE|Ядро или уровень 2 [2]|  
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
  
 [1] Поддержка этих полей записей необходима только в том случае, если драйвер поддерживает применимые типы данных.  
  
 [2] для обеспечения соответствия уровня ядра драйвер должен поддерживать SQL_PARAM_INPUT. Для соответствия интерфейсу уровня 2 драйвер должен также поддерживать SQL_PARAM_INPUT_OUTPUT и SQL_PARAM_OUTPUT.
