---
title: Тип данных C Bookmark | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: b81acf6c60bd11e03a598e349e145dbf72e174b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026953"
---
# <a name="bookmark-c-data-type"></a>Тип данных C Bookmark
Тип данных C закладки позволяет приложению извлекать закладку. Типы закладок C используются только для извлечения значения закладки, которые могут быть переменную длину; они не должны преобразовываться в другие типы данных. Приложение извлекает из 0 столбец результирующего набора с закладки **SQLBulkOperations** (с помощью операции SQL_ADD), **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**. Дополнительные сведения см. в разделе [закладки](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 В следующей таблице перечислены значения *CType* для типа данных C закладку, введите тип данных ODBC C, который реализует тип данных C закладки и определение этих данных из SQL. З.  
  
> [!NOTE]
>  Тип данных SQL_C_BOOKMARK является устаревшим. ODBC 3 *.x* приложения не должны использовать SQL_C_BOOKMARK. ODBC 3 *.x* драйверы должны поддерживать SQL_C_BOOKMARK только в том случае, если они хотят работать с ODBC 2. *x* приложений, которые ее используют. Диспетчер драйверов сопоставляет SQL_C_VARBOOKMARK SQL_C_BOOKMARK в том случае, когда приложение работает с ODBC 2. *x* драйвера.  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Устаревшее)|ЗАКЛАДКА|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
