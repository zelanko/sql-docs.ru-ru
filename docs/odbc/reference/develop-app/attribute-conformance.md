---
title: "Атрибут соответствия | Документы Microsoft"
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
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d615371a5bcf305158cb5f29c22a087110f95ac
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="attribute-conformance"></a>Соответствие атрибутов
Следующая таблица указывает уровень соответствия каждого атрибута среды ODBC, это не определен правильно.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Основные сведения|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] это необязательный компонент и таким образом не является частью уровни соответствия.  
  
 Следующая таблица указывает уровень соответствия каждого атрибута соединения ODBC, где это является правильно определенным.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Основные сведения|  
|АТРИБУТУ SQL_ATTR_ASYNC_ENABLE|Уровень 1 и уровень 2 [1]|  
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
|ПОМОЩЬЮ НАСТРОЙКИ SQL_ATTR_TRANSLATE_LIB|Основные сведения|  
|SQL_ATTR_TRANSLATE_OPTION|Основные сведения|  
|SQL_ATTR_TXN_ISOLATION|Уровень 1 и уровень 2 [2]|  
  
 [1] приложения, поддерживающие асинхронности уровня соединения (требуется для уровня 1) должны поддерживать, задав этому атрибуту значение SQL_TRUE, вызвав **SQLSetConnectAttr**; атрибута не обязательно можно задать значение, отличное от значения по умолчанию значение через **SQLSetStmtAttr**. Приложения, поддерживающие асинхронности уровня инструкций (требуется для уровня 2) должен поддерживать, задав этому атрибуту значение SQL_TRUE, используя либо функции.  
  
 [2] на соответствие интерфейс уровня 1, драйвер должен поддерживать одно значение в дополнение к определяемым драйвером по умолчанию (доступных путем вызова **SQLGetInfo** с параметром SQL_DEFAULT_TXN_ISOLATION). Для соответствия интерфейс уровня 2 драйвер должен также поддерживать SQL_TXN_SERIALIZABLE.  
  
 Следующая таблица указывает уровень соответствия каждого атрибута инструкции ODBC, где это является правильно определенным.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Основные сведения|  
|SQL_ATTR_APP_ROW_DESC|Основные сведения|  
|АТРИБУТУ SQL_ATTR_ASYNC_ENABLE|Уровень 1 и уровень 2 [1]|  
|SQL_ATTR_CONCURRENCY|Уровень 1 и уровень 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|уровне 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Уровень 2|  
|SQL_ATTR_CURSOR_TYPE|Основной или уровне 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Уровень 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Уровень 2|  
|SQL_ATTR_IMP_PARAM_DESC|Основные сведения|  
|SQL_ATTR_IMP_ROW_DESC|Основные сведения|  
|АТРИБУТА SQL_ATTR_KEYSET_SIZE|Уровень 2|  
|ЗНАЧЕНИЯ SQL_ATTR_MAX_LENGTH|уровне 1|  
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
|ЗНАЧЕНИЯ SQL_ATTR_ROW_STATUS_PTR|Основные сведения|  
|SQL_ATTR_ROWS_FETCHED_PTR|Основные сведения|  
|SQL_ATTR_SIMULATE_CURSOR|Уровень 2|  
|SQL_ATTR_USE_BOOKMARKS|Уровень 2|  
  
 [1] приложения, поддерживающие асинхронности уровня соединения (требуется для уровня 1) должны поддерживать, задав этому атрибуту значение SQL_TRUE, вызвав **SQLSetConnectAttr**; атрибута не обязательно можно задать значение, отличное от значения по умолчанию значение через **SQLSetStmtAttr**. Приложения, поддерживающие асинхронности уровня инструкций (требуется для уровня 2) должен поддерживать, задав этому атрибуту значение SQL_TRUE, используя либо функции.  
  
 [2] на соответствие интерфейс уровня 2 драйвер должен поддерживать SQL_CONCUR_READ_ONLY и хотя бы одно значение.  
  
 [3] на соответствие интерфейс уровня 1 драйвер должен поддерживать SQL_CURSOR_FORWARD_ONLY и хотя бы одно значение. Для соответствия интерфейс уровня 2 драйвер должен поддерживать все значения, определенные в этом документе.
