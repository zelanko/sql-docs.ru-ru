---
description: SQLSetDescField и SQLSetDescRec (библиотека курсоров)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cef4967a81a78e08dee733072359459c864b9627
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476946"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField и SQLSetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функций **SQLSetDescField** и **SQLSetDescRec** в библиотеке курсоров. Общие сведения об этих функциях см. в разделе [функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) и [Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Библиотека курсоров выполняет **SQLSetDescField** при вызове для возвращения значений полей, заданных для столбцов закладок:  
  
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
  
 Библиотека курсоров выполняет вызовы **SQLSetDescRec** для столбца Bookmark.  
  
 При работе с драйвером ODBC *2. x* библиотека курсоров ВОЗВРАЩАЕТ значение SQLSTATE HY090 (Недопустимая строка или длина буфера), когда вызывается **SQLSetDescField** или **SQLSetDescRec** , чтобы задать поле SQL_DESC_OCTET_LENGTH для записи закладки АРД, не равное 4. При работе с драйвером ODBC *3. x* библиотека курсоров позволяет буферу иметь любой размер.  
  
 Библиотека курсоров выполняет **SQLSetDescField** при вызове для возврата значения поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут возвращаться для любой строки, а не только для строки закладки.  
  
 Библиотека курсоров не выполняет **SQLSetDescField** для изменения любого поля дескриптора, Кроме упомянутых ранее полей. Если приложение вызывает **SQLSetDescField** для установки любого другого поля во время загрузки библиотеки курсора, вызов передается в драйвер.  
  
 Библиотека курсоров поддерживает изменение полей SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR в любой строке дескриптора строки приложения динамически (после вызова **SQLExtendedFetch**, **SQLFetch**или **SQLFetchScroll**). Поле SQL_DESC_OCTET_LENGTH_PTR может быть изменено на указатель null только для отмены привязки буфера длины для столбца.  
  
 Библиотека курсоров не поддерживает изменение поля SQL_DESC_BIND_TYPE в APD или АРД при открытом курсоре. Поле SQL_DESC_BIND_TYPE можно изменить только после закрытия курсора и до открытия нового курсора. Единственными полями дескриптора, которые библиотека курсоров поддерживает для изменения при открытом курсоре, являются SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_ROWS_PROCESSED_PTR.  
  
 Библиотека курсоров не поддерживает изменение SQL_DESC_COUNT поля АРД после вызова **SQLExtendedFetch** или **SQLFetchScroll** и перед закрытием курсора.
