---
title: Закладка C Тип данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 566f1065d30a47b2db234ba1f11f877725189fb7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292294"
---
# <a name="bookmark-c-data-type"></a>Тип данных C Bookmark
Тип данных закладки C позволяет приложению получить закладку. Типы закладок C используются только для получения значений закладок, которые могут быть переменными по длине; они не должны быть преобразованы в другие типы данных. Приложение получает закладку либо из столбца 0 результатов, установленных с **s'LBulkOperations** (с операцией SQL_ADD), **S'LFetch,** **S'LFetchScroll**, или **S'LGetData**. Для получения дополнительной информации, см [Закладки](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 В следующей таблице перечислены значение *CType* для типа данных закладки C, тип данных ODBC C, который реализует тип данных закладки C, и определение этого типа данных от S'L. H.  
  
> [!NOTE]
>  Тип данных SQL_C_BOOKMARK был унипрачен. Приложения ODBC *3.x* не должны использовать SQL_C_BOOKMARK. Драйверы ODBC *3.x* должны поддерживать SQL_C_BOOKMARK только в том случае, если они хотят работать с приложениями ODBC *2.x,* которые используют его. Менеджер драйвера карты SQL_C_VARBOOKMARK SQL_C_BOOKMARK, когда приложение работает с драйвером ODBC *2.x.*  
  
|Идентификатор типа C|Тип ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Устаревшее)|Закладка|длинное целочисленное число без знака|  
|SQL_C_VARBOOKMARK|СЗЛЧАР|unsigned char *|
