---
title: СЗЛСетДескФилд и СЗЛСетДескРе (Библиотека Курзора) Документы Майкрософт
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
ms.openlocfilehash: b85eb84cdf48a1c2a441b8994076a9023d254f2d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300554"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField и SQLSetDescRec (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается вопрос об использовании функций **S'LSetDescfield** и **S'LSetDescCRec** в библиотеке курсоров. Для получения общей информации об этих функциях, [SQLSetDescRec Function](../../../odbc/reference/syntax/sqlsetdescrec-function.md) [см.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Библиотека курсора выполняет **S'LSetDescField,** когда она называется для возврата значения полей, установленных для столбцов закладок:  
  
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
  
 Библиотека курсора выполняет вызовы в **s'LSetDescRec** для столбца закладок.  
  
 При работе с драйвером ODBC *2.x* библиотека курсоров возвращает S'LSTATE HY090 (недействительная длина строки или буфера), когда **S'LSetDesccField** или **S'LSetDescRec** призваны установить SQL_DESC_OCTET_LENGTH поле для записи закладок ARD к значению, не равному 4. При работе с драйвером ODBC *3.x* библиотека курсора позволяет буферу быть любого размера.  
  
 Библиотека курсора выполняет **S'LSetDescField,** когда она призвана вернуть значение SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE или SQL_DESC_ROW_STATUS_PTR поля. Эти поля могут быть возвращены для любой строки, а не только для строки закладок.  
  
 Библиотека курсоров не выполняет **S'LSetDescField** для изменения любого поля дескриптора, кроме полей, упомянутых ранее. Если приложение вызывает **S'LSetDesccField,** чтобы установить любое другое поле во время загрузки библиотеки курсоров, вызов передается водителю.  
  
 Библиотека курсора поддерживает изменение SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR полей любого ряда дескриптора строки приложения динамически (после звонка в **S'LExtendedFetch,** **S'LFetch**, или **S'LFetchScroll**). Поле SQL_DESC_OCTET_LENGTH_PTR может быть изменено на нулевой указатель только для того, чтобы развязать буфер длины для столбца.  
  
 Библиотека курсора не поддерживает изменение SQL_DESC_BIND_TYPE поля в APD или ARD при открытии курсора. Поле SQL_DESC_BIND_TYPE может быть изменено только после закрытия курсора и до открытия нового курсора. Единственными полями дескриптора, которые поддерживает библиотека курсора, когда курсор открыт, являются SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR и SQL_DESC_ROWS_PROCESSED_PTR.  
  
 Библиотека курсоров не поддерживает изменение SQL_DESC_COUNT поля ARD после вызова **S'LExtendedFetch** или **S'LFetchScroll** и до того, как курсор был закрыт.
