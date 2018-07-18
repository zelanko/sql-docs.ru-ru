---
title: SQLSetDescField и SQLSetDescRec (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04c3fd1c3c64140b7669cdeeb35937498249ac66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910279"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField и SQLSetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetDescField** и **SQLSetDescRec** функции в библиотеку курсоров. Общие сведения об этих функциях см. в разделе [функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) и [SQLSetDescRec, функция](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Библиотека курсоров выполняет **SQLSetDescField** при вызове для возврата значения полей, задать для столбцов закладок:  
  
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
  
 При работе с ODBC 2. *x* драйвер, библиотеку курсоров возвращает SQLSTATE HY090 (Недопустимая длина строки или буфера) при **SQLSetDescField** или **SQLSetDescRec** вызывается для установки SQL_DESC_OCTET_ Поля ДЛИНЫ записи закладки Отменить значение не равно 4. При работе с ODBC 3 *.x* драйверов, библиотеку курсоров обеспечивает буфера быть любого размера.  
  
 Библиотека курсоров выполняет **SQLSetDescField** при вызове для возврата значения поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут быть возвращены для любой строки, не только строки закладки.  
  
 Библиотека курсоров не выполняет **SQLSetDescField** для изменения любого поля дескриптора, отличных от полей, упомянутых ранее. Если приложение вызывает **SQLSetDescField** Чтобы задать любое другое поле при загрузке библиотеки курсоров, вызов передается через драйвер.  
  
 Библиотека курсоров поддерживает динамически меняется поля SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR любой строки дескриптор строк приложения (после вызова **SQLExtendedFetch**, **SQLFetch**, или **SQLFetchScroll**). SQL_DESC_OCTET_LENGTH_PTR поле можно изменить на указатель null только в том, чтобы отменить привязку буфер длины для столбца.  
  
 Библиотека курсоров не поддерживает изменения поле SQL_DESC_BIND_TYPE в APD или Отменить при открытом курсоре. Поле SQL_DESC_BIND_TYPE можно изменить только в том случае, если курсор закрыт, и перед открытием нового курсора. Только поля дескриптора, что библиотека курсоров поддерживает изменения, когда курсор открыт, SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 Библиотека курсоров не поддерживает изменение поля SQL_DESC_COUNT Отменить после **SQLExtendedFetch** или **SQLFetchScroll** был вызван до закрытия курсора.
