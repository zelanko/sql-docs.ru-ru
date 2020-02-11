---
title: Соответствие атрибутов | Документация Майкрософт
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
ms.openlocfilehash: 71f0da7bbd7ef1a37a1f48539c7230bff0ceda15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909915"
---
# <a name="attribute-conformance"></a>Соответствие атрибутов
В следующей таблице указывается уровень соответствия для каждого атрибута среды ODBC, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] это необязательный компонент, который не является частью уровней соответствия.  
  
 В следующей таблице указывается уровень соответствия для каждого атрибута соединения ODBC, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Core|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/уровень 2 [1]|  
|SQL_ATTR_AUTO_IPD|Уровень 2|  
|SQL_ATTR_AUTOCOMMIT|уровне 1|  
|SQL_ATTR_CONNECTION_DEAD|уровне 1|  
|SQL_ATTR_CONNECTION_TIMEOUT|Уровень 2|  
|SQL_ATTR_CURRENT_CATALOG|Уровень 2|  
|SQL_ATTR_LOGIN_TIMEOUT|Уровень 2|  
|SQL_ATTR_ODBC_CURSORS|Core|  
|SQL_ATTR_PACKET_SIZE|Уровень 2|  
|SQL_ATTR_QUIET_MODE|Core|  
|SQL_ATTR_TRACE|Core|  
|SQL_ATTR_TRACEFILE|Core|  
|SQL_ATTR_TRANSLATE_LIB|Core|  
|SQL_ATTR_TRANSLATE_OPTION|Core|  
|SQL_ATTR_TXN_ISOLATION|Уровень 1/уровень 2 [2]|  
  
 [1] приложения, поддерживающие асинхронность уровня соединения (обязательно для уровня 1), должны поддерживать присвоение этому атрибуту значения SQL_TRUE путем вызова **SQLSetConnectAttr**; атрибут не может быть установлен для значения, отличного от значения по умолчанию, через **SQLSetStmtAttr**. Приложения, поддерживающие асинхронность уровня инструкции (обязательный для уровня 2), должны поддерживать присвоение этому атрибуту значения SQL_TRUE помощью любой из функций.  
  
 [2] для обеспечения соответствия интерфейса уровня 1 драйвер должен поддерживать одно значение в дополнение к значению, заданному драйвером по умолчанию (доступно путем вызова **SQLGetInfo** с параметром SQL_DEFAULT_TXN_ISOLATION). Для соответствия интерфейсу уровня 2 драйвер также должен поддерживать SQL_TXN_SERIALIZABLE.  
  
 В следующей таблице указывается уровень соответствия для каждого атрибута инструкции ODBC, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/уровень 2 [1]|  
|SQL_ATTR_CONCURRENCY|Уровень 1/уровень 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|уровне 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Уровень 2|  
|SQL_ATTR_CURSOR_TYPE|Ядро или уровень 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Уровень 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Уровень 2|  
|SQL_ATTR_IMP_PARAM_DESC|Core|  
|SQL_ATTR_IMP_ROW_DESC|Core|  
|SQL_ATTR_KEYSET_SIZE|Уровень 2|  
|SQL_ATTR_MAX_LENGTH|уровне 1|  
|SQL_ATTR_MAX_ROWS|уровне 1|  
|SQL_ATTR_METADATA_ID|Core|  
|SQL_ATTR_NOSCAN|Core|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_PARAM_BIND_TYPE|Core|  
|SQL_ATTR_PARAM_OPERATION_PTR|Core|  
|SQL_ATTR_PARAM_STATUS_PTR|Core|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|Core|  
|SQL_ATTR_PARAMSET_SIZE|Core|  
|SQL_ATTR_QUERY_TIMEOUT|Уровень 2|  
|SQL_ATTR_RETRIEVE_DATA|уровне 1|  
|SQL_ATTR_ROW_ARRAY_SIZE|Core|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_ROW_BIND_TYPE|Core|  
|SQL_ATTR_ROW_NUMBER|уровне 1|  
|SQL_ATTR_ROW_OPERATION_PTR|уровне 1|  
|SQL_ATTR_ROW_STATUS_PTR|Core|  
|SQL_ATTR_ROWS_FETCHED_PTR|Core|  
|SQL_ATTR_SIMULATE_CURSOR|Уровень 2|  
|SQL_ATTR_USE_BOOKMARKS|Уровень 2|  
  
 [1] приложения, поддерживающие асинхронность уровня соединения (обязательно для уровня 1), должны поддерживать присвоение этому атрибуту значения SQL_TRUE путем вызова **SQLSetConnectAttr**; атрибут не может быть установлен для значения, отличного от значения по умолчанию, через **SQLSetStmtAttr**. Приложения, поддерживающие асинхронность уровня инструкции (обязательный для уровня 2), должны поддерживать присвоение этому атрибуту значения SQL_TRUE помощью любой из функций.  
  
 [2] для обеспечения соответствия интерфейса уровня 2 драйвер должен поддерживать SQL_CONCUR_READ_ONLY и хотя бы одно другое значение.  
  
 [3] для обеспечения соответствия интерфейса уровня 1 драйвер должен поддерживать SQL_CURSOR_FORWARD_ONLY и хотя бы одно другое значение. Для соответствия интерфейсу уровня 2 драйвер должен поддерживать все значения, определенные в этом документе.
