---
title: SQLSetDescField и SQLSetDescRec (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b390df48e676290696ae8080c8f671fd0e37bad8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298271"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField и SQLSetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLSetDescField** и **SQLSetDescRec** функций в библиотеку курсоров. Общие сведения об этих функциях см. в разделе [функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) и [SQLSetDescRec, функция](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Библиотека курсоров выполняет **SQLSetDescField** при ее вызове для возврата значения полей определение для закладки столбцов:  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 Библиотека курсоров выполняет вызовы **SQLSetDescRec** для столбца закладки.  
  
 При работе с ODBC 2. *x* драйвер, библиотека курсоров возвращает SQLSTATE HY090 (Недопустимая длина строки или буфера) при **SQLSetDescField** или **SQLSetDescRec** вызывается для установки SQL_DESC_OCTET_ Длина поля записи закладки Отменить значение не равно 4. При работе с ODBC 3 *.x* драйвера, библиотека курсоров ODBC позволяет буфера быть любого размера.  
  
 Библиотека курсоров выполняет **SQLSetDescField** при ее вызове для возврата значения поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут быть возвращены для любой строке, а не только строки закладки.  
  
 Библиотека курсоров не выполняет **SQLSetDescField** для изменения любого поля дескриптора, отличных от полей, упомянутых ранее. Если приложение вызывает **SQLSetDescField** Чтобы задать любое другое поле, пока библиотека курсоров загружена, вызов передается через драйвер.  
  
 Библиотека курсоров поддерживает изменение поля SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR любую строку дескриптор строки приложение динамически (после вызова **SQLExtendedFetch**, **SQLFetch**, или **SQLFetchScroll**). Поле SQL_DESC_OCTET_LENGTH_PTR можно изменить на указатель null только в том, чтобы отменить привязку буфер длины для столбца.  
  
 Библиотека курсоров не поддерживает изменение поле SQL_DESC_BIND_TYPE в APD или Отменить при открытом курсоре. Это поле SQL_DESC_BIND_TYPE можно изменить только в том случае, после закрытия курсора, и перед открытием нового курсора. Только поля дескриптора, что библиотека курсоров поддерживает изменения при открытом курсоре, SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 Библиотека курсоров не поддерживает изменение поле SQL_DESC_COUNT Отменить после **SQLExtendedFetch** или **SQLFetchScroll** был вызван и закрыть курсор.
