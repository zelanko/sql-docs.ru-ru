---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597abe268979852d754e2e3e86ae81daa8f3fed8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019059"
---
# <a name="cursor-library-cache"></a>Кэш библиотеки курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Для каждой строки данных в результирующем наборе библиотека курсоров кэширует данные для каждого привязанного столбца длину данных в каждого привязанного столбца и строки состояния. Библиотека курсоров используются значения в кэше обоих возвращать данные через **SQLFetch** и **SQLFetchScroll** и для создания поискового инструкций для позиционированных операций. Дополнительные сведения см. в разделе [создав поиск инструкций](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Данные столбца](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Длина данных столбца](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Статус строки](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Расположение кэша](../../../odbc/reference/appendixes/location-of-cache.md)
