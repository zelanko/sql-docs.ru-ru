---
description: Использование блочных курсоров
title: Использование блочных курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67cad7220641e9c3800e89675825cf2c0b1e334d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482867"
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка блочных курсоров встроена в ODBC 3. *x*. **SQLFetch** можно использовать только для выборки многострочные при вызове в ODBC 3. *x*; Если ODBC 2. Приложение *x* вызывает **SQLFetch**, при этом будет открыт только однострочный курсор. При использовании ODBC 3. Приложение *x* вызывает **SQLFetch** в ODBC 2. драйвер *x* , он возвращает одну строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочные курсоры, прокручиваемые курсоры и обратная совместимость](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: рекомендации по драйверам для обеспечения обратной совместимости.  
  
 Чтобы использовать блочные курсоры, приложение задает размер набора строк, привязывает буферы набора строк (как описано в предыдущем разделе), при необходимости задает атрибуты SQL_ATTR_ROWS_FETCHED_PTR и SQL_ATTR_ROW_STATUS_PTR, а также вызывает **SQLFetch** или **SQLFetchScroll** для выборки блока строк. Приложение может изменить размер набора строк и привязать новые буферы наборов строк (путем вызова **SQLBindCol** или указания смещения привязки) даже после выборки строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; блокировать курсо](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
