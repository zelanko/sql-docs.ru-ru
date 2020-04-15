---
title: СЗЛКолобы (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7031e9eebbb1ffae045598863d22399147503c88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307905"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Возвращается путь к файлу базы данных.|  
|TABLE_OWNER|NULL возвращается в этой колонке, поскольку имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, участвующих в основном ключевом или уникальном индексе.|
