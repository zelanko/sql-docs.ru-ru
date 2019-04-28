---
title: Атрибут соответствия | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44f1311d98f37412454ad2352366492a8d5a1768
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62672533"
---
# <a name="attribute-conformance"></a>Соответствие атрибутов
Следующая таблица указывает уровень соответствия каждого атрибута ODBC среде, где это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Основные сведения|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] это является дополнительным компонентом и таким образом не является частью уровни соответствия.  
  
 Следующая таблица указывает уровень соответствия каждого соединения ODBC атрибута, где это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Основные сведения|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/уровня 2 [1]|  
|SQL_ATTR_AUTO_IPD|Уровень 2|  
|SQL_ATTR_AUTOCOMMIT|уровне 1|  
|SQL_ATTR_CONNECTION_DEAD|уровне 1|  
|SQL_ATTR_CONNECTION_TIMEOUT|Уровень 2|  
|SQL_ATTR_CURRENT_CATALOG|Уровень 2|  
|SQL_ATTR_LOGIN_TIMEOUT|Уровень 2|  
|SQL_ATTR_ODBC_CURSORS|Основные сведения|  
|SQL_ATTR_PACKET_SIZE|Уровень 2|  
|SQL_ATTR_QUIET_MODE|Основные сведения|  
|SQL_ATTR_TRACE|Основные сведения|  
|SQL_ATTR_TRACEFILE|Основные сведения|  
|SQL_ATTR_TRANSLATE_LIB|Основные сведения|  
|SQL_ATTR_TRANSLATE_OPTION|Основные сведения|  
|SQL_ATTR_TXN_ISOLATION|Уровень 1/уровня 2 [2]|  
  
 [1] приложения, которые поддерживают асинхронность уровня соединения (требуется для уровня 1) должны поддерживать, установка этого атрибута задано значение SQL_TRUE, вызвав **SQLSetConnectAttr**; атрибута не обязательно устанавливаемое значение, отличное от значения по умолчанию значение через **SQLSetStmtAttr**. Должен поддерживать приложения, которые поддерживают асинхронность уровне инструкций (требуется для уровня 2), установка этого атрибута задано значение SQL_TRUE, с помощью любой из этих функций.  
  
 [2] для соответствие интерфейса уровня 1, драйвер должен поддерживать одно значение в дополнение к значению по умолчанию драйвер (доступных путем вызова **SQLGetInfo** с параметром SQL_DEFAULT_TXN_ISOLATION). Соответствие интерфейса уровня 2 драйвер должен также поддерживать SQL_TXN_SERIALIZABLE.  
  
 Следующая таблица указывает уровень соответствия каждого атрибута инструкции ODBC, где это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Основные сведения|  
|SQL_ATTR_APP_ROW_DESC|Основные сведения|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/уровня 2 [1]|  
|SQL_ATTR_CONCURRENCY|Уровень 1/уровня 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|уровне 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Уровень 2|  
|SQL_ATTR_CURSOR_TYPE|Core/уровень 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Уровень 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Уровень 2|  
|SQL_ATTR_IMP_PARAM_DESC|Основные сведения|  
|SQL_ATTR_IMP_ROW_DESC|Основные сведения|  
|SQL_ATTR_KEYSET_SIZE|Уровень 2|  
|SQL_ATTR_MAX_LENGTH|уровне 1|  
|SQL_ATTR_MAX_ROWS|уровне 1|  
|SQL_ATTR_METADATA_ID|Основные сведения|  
|SQL_ATTR_NOSCAN|Основные сведения|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|Основные сведения|  
|SQL_ATTR_PARAM_BIND_TYPE|Основные сведения|  
|SQL_ATTR_PARAM_OPERATION_PTR|Основные сведения|  
|SQL_ATTR_PARAM_STATUS_PTR|Основные сведения|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|Основные сведения|  
|SQL_ATTR_PARAMSET_SIZE|Основные сведения|  
|SQL_ATTR_QUERY_TIMEOUT|Уровень 2|  
|SQL_ATTR_RETRIEVE_DATA|уровне 1|  
|SQL_ATTR_ROW_ARRAY_SIZE|Основные сведения|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|Основные сведения|  
|SQL_ATTR_ROW_BIND_TYPE|Основные сведения|  
|SQL_ATTR_ROW_NUMBER|уровне 1|  
|SQL_ATTR_ROW_OPERATION_PTR|уровне 1|  
|SQL_ATTR_ROW_STATUS_PTR|Основные сведения|  
|SQL_ATTR_ROWS_FETCHED_PTR|Основные сведения|  
|SQL_ATTR_SIMULATE_CURSOR|Уровень 2|  
|SQL_ATTR_USE_BOOKMARKS|Уровень 2|  
  
 [1] приложения, которые поддерживают асинхронность уровня соединения (требуется для уровня 1) должны поддерживать, установка этого атрибута задано значение SQL_TRUE, вызвав **SQLSetConnectAttr**; атрибута не обязательно устанавливаемое значение, отличное от значения по умолчанию значение через **SQLSetStmtAttr**. Должен поддерживать приложения, которые поддерживают асинхронность уровне инструкций (требуется для уровня 2), установка этого атрибута задано значение SQL_TRUE, с помощью любой из этих функций.  
  
 [2] для соответствие интерфейса уровня 2 драйвер должен поддерживать SQL_CONCUR_READ_ONLY и хотя бы одно значение.  
  
 [3] для соответствие интерфейса уровня 1 драйвер должен поддерживать SQL_CURSOR_FORWARD_ONLY и хотя бы одно значение. Соответствие интерфейса уровня 2 драйвер должны поддерживать все значения, определенные в этом документе.
