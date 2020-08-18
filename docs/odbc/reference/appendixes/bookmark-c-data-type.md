---
description: Тип данных C Bookmark
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4647002d5e57ea20656a4fa2dec03aa8092b9b36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411260"
---
# <a name="bookmark-c-data-type"></a>Тип данных C Bookmark
Тип данных Bookmark C позволяет приложению получить закладку. Типы закладок C используются только для получения значений закладок, которые могут быть переменными длиной. их не следует преобразовывать в другие типы данных. Приложение получает закладку либо из столбца 0 результирующего набора с помощью **SQLBulkOperations** (с операцией SQL_ADD), **SQLFetch**, **SQLFetchScroll**или **SQLGetData**. Дополнительные сведения см. в разделе [закладки](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 В следующей таблице приведено значение *CType* для типа данных Bookmark c, тип данных ODBC c, реализующий тип данных c Bookmark, и определение этого типа данных из SQL. Высоты.  
  
> [!NOTE]
>  Тип данных SQL_C_BOOKMARK не рекомендуется к использованию. Приложения ODBC *3. x* не должны использовать SQL_C_BOOKMARK. Драйверы ODBC *3. x* должны поддерживать SQL_C_BOOKMARK только в том случае, если они хотят работать с приложениями ODBC *2. x* , которые его используют. Диспетчер драйверов сопоставляет SQL_C_VARBOOKMARK SQL_C_BOOKMARK, когда приложение работает с драйвером ODBC *2. x* .  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Устаревшее)|Закладка|длинное целочисленное число без знака|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|
