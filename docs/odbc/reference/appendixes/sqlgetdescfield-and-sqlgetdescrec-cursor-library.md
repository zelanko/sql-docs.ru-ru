---
title: Функция SQLGetDescField и SQLGetDescRec (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b41e938cc178e2a26499f9ce18cc461a9388802
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>Функция SQLGetDescField и SQLGetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLGetDescField** и **SQLGetDescRec** функции в библиотеку курсоров. Общие сведения об этих функциях см. в разделе [SQLGetDescField, функция](../../../odbc/reference/syntax/sqlgetdescfield-function.md) и [SQLGetDescRec, функция](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 Библиотека курсоров выполняет **SQLGetDescRec** возвращать метаданные для столбцов закладок. Выполняет библиотеку курсоров **SQLGetDescField** для получения того же поля, возвращаемые **SQLGetDescRec**, которые являются SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ Длина, SQL_DESC_PRECISION, SQL_DESC_SCALE и SQL_DESC_NULLABLE. Для обеспечения согласованности **SQLGetDescField** также возвращает SQL_DESC_UNNAMED.  
  
 Библиотека курсоров выполняет **SQLGetDescField** при вызове для возврата значения из следующих полей, заданных для привязки столбцов закладок: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR, и SQL_DESC_LENGTH.  
  
 Библиотека курсоров выполняет **SQLGetDescField** при вызове для возврата значения поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут быть возвращены для любой строки, не только строки закладки.  
  
 Если приложение вызывает **SQLGetDescField** для возврата всех полей, кроме упомянутых ранее, библиотеку курсоров передает этот вызов к драйверу.
