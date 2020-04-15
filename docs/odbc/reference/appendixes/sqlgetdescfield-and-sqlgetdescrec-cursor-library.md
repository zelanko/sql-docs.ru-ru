---
title: СЗЛГетДескФилд и СЗЛГетДескРес (Библиотека Курзора) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ceea6b6180e1b51f2f103f74412c3e2b4cbe02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307835"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField и SQLGetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается вопрос об использовании функций **S'LGetDescfield** и **S'LGetDescRec** в библиотеке курсоров. Для получения общей информации об этих функциях, [SQLGetDescRec Function](../../../odbc/reference/syntax/sqlgetdescrec-function.md) [см.](../../../odbc/reference/syntax/sqlgetdescfield-function.md)  
  
 Библиотека курсора выполняет **S'LGetDescRec,** чтобы вернуть метаданные для столбцов закладок. Библиотека курсоров, выполняющая **s'LGetDescField,** возвращает те же поля, которые возвращаются **S'LGetDescRec**, которые являются SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE и SQL_DESC_NULLABLE. Для обеспечения **согласованности, S'LGetDescfield** также возвращает SQL_DESC_UNNAMED.  
  
 Библиотека курсора выполняет **S'LGetDescField,** когда она призвана вернуть значение следующих полей, которые установлены для обязательных столбцов закладки: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_LENGTH.  
  
 Библиотека курсора выполняет **S'LGetDescField,** когда она призвана вернуть значение поля SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR. Эти поля могут быть возвращены для любой строки, а не только для строки закладок.  
  
 Если приложение вызывает **S'LGetDescField,** чтобы вернуть значение любого поля, кроме упомянутых ранее, библиотека курсора передает вызов водителю.
