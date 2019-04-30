---
title: SQLGetDescField и SQLGetDescRec (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66361572427c3264a1b25fe1c851685a07b2e029
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188754"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField и SQLGetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLGetDescField** и **SQLGetDescRec** функций в библиотеку курсоров. Общие сведения об этих функциях см. в разделе [функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) и [SQLGetDescRec, функция](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 Библиотека курсоров выполняет **SQLGetDescRec** вернуть метаданные для столбцов закладок. Библиотека курсоров выполняет **SQLGetDescField** возвращать те же поля, возвращаемые **SQLGetDescRec**, которые являются SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ Длина, SQL_DESC_PRECISION, SQL_DESC_SCALE и SQL_DESC_NULLABLE. Для обеспечения согласованности **SQLGetDescField** также возвращает SQL_DESC_UNNAMED.  
  
 Библиотека курсоров выполняет **SQLGetDescField** при ее вызове для возврата значения следующих полей, заданные для привязки столбцов закладок: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_LENGTH.  
  
 Библиотека курсоров выполняет **SQLGetDescField** при ее вызове для возврата значения поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут быть возвращены для любой строке, а не только строки закладки.  
  
 Если приложение вызывает **SQLGetDescField** для возврата значения любого поля, кроме упомянутых ранее, библиотека курсоров передает этот вызов к драйверу.
