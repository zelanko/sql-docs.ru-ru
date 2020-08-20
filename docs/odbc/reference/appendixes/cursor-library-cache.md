---
description: Кэш библиотеки курсоров
title: Кэш библиотеки курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a558ab120d2812e88a4dbbdd8392c997ce423c8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456653"
---
# <a name="cursor-library-cache"></a>Кэш библиотеки курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Для каждой строки данных в результирующем наборе библиотека курсоров кэширует данные для каждого привязанного столбца, длину данных в каждом связанном столбце и состояние строки. Библиотека курсоров использует значения в кэше для возврата через **SQLFetch** и **SQLFetchScroll** и для создания поисковых инструкций для позиционированных операций. Дополнительные сведения см. в разделе [Построение поисковых инструкций](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Столбец данных](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Длина данных столбца](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Статус строки](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Расположение кэша](../../../odbc/reference/appendixes/location-of-cache.md)
