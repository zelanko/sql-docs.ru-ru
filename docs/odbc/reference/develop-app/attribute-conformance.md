---
title: Соответствие атрибутов Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2880a35f4bdc997cc037cdd0d60720267ff4a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306405"
---
# <a name="attribute-conformance"></a>Соответствие атрибутов
В следующей таблице указывается уровень соответствия каждого атрибута среды ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Основные сведения|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 Это необязательная функция и как таковая не является частью уровней соответствия.  
  
 В следующей таблице указывается уровень соответствия каждого атрибута соединения ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Основные сведения|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/Уровень 2|  
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
|SQL_ATTR_TXN_ISOLATION|Уровень 1/Уровень 2|  
  
 Приложения, поддерживающие асинхронность уровня соединения (требуется для уровня 1), должны поддерживать настройку этого атрибута на SQL_TRUE, позвонив по **s-LSetConnectAttr;** атрибут не должен быть установлен к значению, за исключением его значения по умолчанию через **S'LSetStmtAttr.** Приложения, поддерживающие асинхронность уровня оператора (требуется для уровня 2), должны поддерживать настройку этого атрибута SQL_TRUE с помощью любой функции.  
  
 Для соответствия интерфейса уровня 1 драйвер должен поддерживать одно значение в дополнение к определенному драйверу значением по умолчанию (доступно, позвонив по **s'LGetInfo** с SQL_DEFAULT_TXN_ISOLATION опцией). Для соответствия интерфейса уровня 2 водитель должен также поддерживать SQL_TXN_SERIALIZABLE.  
  
 В следующей таблице указывается уровень соответствия каждого атрибута оператора ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Основные сведения|  
|SQL_ATTR_APP_ROW_DESC|Основные сведения|  
|SQL_ATTR_ASYNC_ENABLE|Уровень 1/Уровень 2|  
|SQL_ATTR_CONCURRENCY|Уровень 1/Уровень 2|  
|SQL_ATTR_CURSOR_SCROLLABLE|уровне 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Уровень 2|  
|SQL_ATTR_CURSOR_TYPE|Ядро/Уровень 2'3»|  
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
  
 Приложения, поддерживающие асинхронность уровня соединения (требуется для уровня 1), должны поддерживать настройку этого атрибута на SQL_TRUE, позвонив по **s-LSetConnectAttr;** атрибут не должен быть установлен к значению, за исключением его значения по умолчанию через **S'LSetStmtAttr.** Приложения, поддерживающие асинхронность уровня оператора (требуется для уровня 2), должны поддерживать настройку этого атрибута SQL_TRUE с помощью любой функции.  
  
 Для соответствия интерфейса уровня 2 водитель должен поддерживать SQL_CONCUR_READ_ONLY и по крайней мере еще одно значение.  
  
 Для соответствия интерфейса уровня 1 водитель должен поддерживать SQL_CURSOR_FORWARD_ONLY и по крайней мере еще одно значение. Для соответствия интерфейса уровня 2 водитель должен поддерживать все значения, определенные в этом документе.
