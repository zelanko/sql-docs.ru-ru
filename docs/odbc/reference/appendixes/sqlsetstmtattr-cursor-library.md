---
title: СЗЛСетСтмттр (Библиотека Курсора) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300494"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LSetStmtAttr** в библиотеке курсоров. Для получения общей информации о **функции S'LsetStmtattr** [см.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
 Библиотека курсора поддерживает следующие атрибуты оператора с **помощью S'LSetStmtAttr:**  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Библиотека курсора поддерживает только SQL_CURSOR_FORWARD_ONLY и SQL_CURSOR_STATIC значения атрибута SQL_ATTR_CURSOR_TYPE оператора.  
  
 Для курсоров только для форварда библиотека курсоров поддерживает SQL_CONCUR_READ_ONLY значение атрибута SQL_ATTR_CONCURRENCY оператора. Для статических курсоров библиотека курсора поддерживает SQL_CONCUR_READ_ONLY и SQL_CONCUR_VALUES значения атрибута SQL_ATTR_CONCURRENCY оператора.  
  
 Библиотека курсора поддерживает только SQL_SC_NON_UNIQUE значение атрибута SQL_ATTR_SIMULATE_CURSOR оператора.  
  
 Несмотря на то, что спецификация ODBC поддерживает вызовы на **S'LSetStmtAttr** с SQL_ATTR_PARAM_BIND_TYPE или SQL_ATTR_ROW_BIND_TYPE атрибутами после вызова **S'LFetch** или **S'LFetchScroll,** библиотека курсоров — нет. Прежде чем изменить тип связывания в библиотеке курсора, приложение должно закрыть курсор. Библиотека курсора поддерживает изменение атрибутов SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR и SQL_ATTR_PARAMS_PROCESSED_PTR оператора при открытии курсора.  
  
 Приложение может **вызыватьSLSetStmtAttr** с **атрибутом** SQL_ATTR_ROW_ARRAY_SIZE, чтобы изменить размер рядового набора, пока курсор открыт. Новый размер набора строк вступит в силу при следующем вызове **S'LFetchScroll** или **S'LFetch.**  
  
 Библиотека курсора поддерживает настройку атрибута SQL_ATTR_PARAM_BIND_OFFSET_PTR или SQL_ATTR_ROW_BIND_OFFSET_PTR оператора для включения обязательных смещений. Привязка смещения не будет использоваться для вызовов в **S'LFetch,** когда библиотека курсора используется с ODBC 2. *x* драйвер.  
  
 Библиотека курсора поддерживает установку атрибута SQL_ATTR_USE_BOOKMARKS оператора на SQL_UB_VARIABLE.
