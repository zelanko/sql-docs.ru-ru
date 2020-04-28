---
title: SQLSetStmtAttr (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bdd9b3b559d5cc78a0d44f5280aae347bc8996a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300494"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLSetStmtAttr** в библиотеке курсоров. Общие сведения о **SQLSetStmtAttr**см. в разделе [функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Библиотека курсоров поддерживает следующие атрибуты инструкции с **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Библиотека курсоров поддерживает только значения SQL_CURSOR_FORWARD_ONLY и SQL_CURSOR_STATIC атрибута инструкции SQL_ATTR_CURSOR_TYPE.  
  
 Для однонаправленных курсоров библиотека курсоров поддерживает SQL_CONCUR_READ_ONLY значение атрибута инструкции SQL_ATTR_CONCURRENCY. Для статических курсоров библиотека курсоров поддерживает SQL_CONCUR_READ_ONLY и SQL_CONCUR_VALUES значения атрибута SQL_ATTR_CONCURRENCY инструкции.  
  
 Библиотека курсоров поддерживает только SQL_SC_NON_UNIQUE значение атрибута инструкции SQL_ATTR_SIMULATE_CURSOR.  
  
 Хотя Спецификация ODBC поддерживает вызовы **SQLSetStmtAttr** с атрибутами SQL_ATTR_PARAM_BIND_TYPE или SQL_ATTR_ROW_BIND_TYPE после вызова **SQLFetch** или **SQLFetchScroll** , Библиотека курсоров не имеет. Прежде чем он сможет изменить тип привязки в библиотеке курсоров, приложение должно закрыть курсор. Библиотека курсоров поддерживает изменение атрибутов SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR и SQL_ATTR_PARAMS_PROCESSED_PTR, когда курсор открыт.  
  
 Приложение может вызвать **SQLSetStmtAttr** с **атрибутом** SQL_ATTR_ROW_ARRAY_SIZE, чтобы изменить размер набора строк, пока курсор открыт. Новый размер набора строк вступит в силу при следующем вызове **SQLFetchScroll** или **SQLFetch** .  
  
 Библиотека курсоров поддерживает задание SQL_ATTR_PARAM_BIND_OFFSET_PTR или SQL_ATTR_ROW_BIND_OFFSET_PTR атрибута инструкции для включения смещений привязок. Смещение привязки не будет использоваться для вызовов **SQLFetch** , если библиотека курсоров используется с ODBC 2. драйвер *x* .  
  
 Библиотека курсоров поддерживает задание для атрибута SQL_ATTR_USE_BOOKMARKS инструкции значения SQL_UB_VARIABLE.
