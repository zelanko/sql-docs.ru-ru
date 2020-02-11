---
title: SQLColumns (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 893ffa40f346a878b4cdde87a9a0a55fbb9e1c7a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132520"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Возвращается путь к каталогу.|  
|TABLE_OWNER|Значение NULL возвращается в этом столбце, так как имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, которые участвуют в первичном ключе или уникальном индексе.|
