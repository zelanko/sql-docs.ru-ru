---
title: Тип данных закладки C | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86488da93470a61a54638e9c60e6e1795a9da4dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125747"
---
# <a name="bookmark-c-data-type"></a>Тип данных C Bookmark
Тип данных Bookmark C позволяет приложению получить закладку. Типы закладок C используются только для получения значений закладок, которые могут быть переменными длиной. их не следует преобразовывать в другие типы данных. Приложение получает закладку либо из столбца 0 результирующего набора с помощью **SQLBulkOperations** (с операцией SQL_ADD), **SQLFetch**, **SQLFetchScroll**или **SQLGetData**. Дополнительные сведения см. в разделе [закладки](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 В следующей таблице приведено значение *CType* для типа данных Bookmark c, тип данных ODBC c, реализующий тип данных c Bookmark, и определение этого типа данных из SQL. Высоты.  
  
> [!NOTE]
>  Тип данных SQL_C_BOOKMARK не рекомендуется к использованию. Приложения ODBC *3. x* не должны использовать SQL_C_BOOKMARK. Драйверы ODBC *3. x* должны поддерживать SQL_C_BOOKMARK только в том случае, если они хотят работать с приложениями ODBC *2. x* , которые его используют. Диспетчер драйверов сопоставляет SQL_C_VARBOOKMARK SQL_C_BOOKMARK, когда приложение работает с драйвером ODBC *2. x* .  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(не рекомендуется)|Закладка|длинное целое без знака|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|
