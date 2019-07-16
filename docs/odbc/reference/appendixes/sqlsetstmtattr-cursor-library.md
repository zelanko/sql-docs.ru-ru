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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc222c1c8669769060de4fc0a1390a9bf02e3f31
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091694"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLSetStmtAttr** функции в библиотеку курсоров. Общие сведения о **SQLSetStmtAttr**, см. в разделе [функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Библиотека курсоров поддерживает следующие атрибуты инструкций с **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Библиотека курсоров поддерживает только SQL_CURSOR_FORWARD_ONLY и SQL_CURSOR_STATIC значения атрибута SQL_ATTR_CURSOR_TYPE инструкции.  
  
 Для курсоров библиотека курсоров поддерживает SQL_CONCUR_READ_ONLY значение атрибута инструкции SQL_ATTR_CONCURRENCY. Для описания статических курсоров библиотеку курсоров поддерживает SQL_CONCUR_READ_ONLY и SQL_CONCUR_VALUES значения атрибута инструкции SQL_ATTR_CONCURRENCY.  
  
 Библиотека курсоров поддерживает только значение атрибута инструкции SQL_ATTR_SIMULATE_CURSOR SQL_SC_NON_UNIQUE.  
  
 Несмотря на то, что в спецификации ODBC поддерживает вызовы **SQLSetStmtAttr** с атрибутами SQL_ATTR_PARAM_BIND_TYPE или SQL_ATTR_ROW_BIND_TYPE после **SQLFetch** или **SQLFetchScroll**  был вызван, курсор не поддерживает библиотеки. Прежде чем его можно изменить тип привязки в библиотеку курсоров, приложение должно закрыть курсор. Библиотека курсоров поддерживает изменение SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR и атрибуты инструкции SQL_ATTR_PARAMS_PROCESSED_PTR, когда курсор открыт.  
  
 Приложение может вызвать **SQLSetStmtAttr** с **атрибут** из SQL_ATTR_ROW_ARRAY_SIZE, чтобы изменить размер набора строк при открытом курсоре. Новый размер набора строк вступят в силу очередном **SQLFetchScroll** или **SQLFetch** вызывается.  
  
 Библиотека курсоров поддерживает задание SQL_ATTR_PARAM_BIND_OFFSET_PTR или SQL_ATTR_ROW_BIND_OFFSET_PTR атрибут инструкции для включения смещения привязки. Смещение привязки не будет использоваться для вызовов **SQLFetch** при использовании библиотеки курсоров с ODBC 2. *x* драйвера.  
  
 Библиотека курсоров поддерживает присвоение атрибуту инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.
