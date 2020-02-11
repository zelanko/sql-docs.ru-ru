---
title: SQLColumns (Драйвер Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColumns
ms.assetid: d7831c7d-8be9-40a7-bc70-8d89db8fe8c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1738e17742e61a285a4d2d070b179d2832aaf40f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132514"
---
# <a name="sqlcolumns-paradox-driver"></a>SQLColumns (драйвер для Paradox)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Paradox. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Возвращается путь к каталогу.|  
|TABLE_OWNER|Значение NULL возвращается в этом столбце, так как имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, которые участвуют в первичном ключе или уникальном индексе.|
