---
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
ms.openlocfilehash: f5c487bd8b60a83c709399cb9673dc0b015bd79d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306795"
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка блочных курсоров встроена в ODBC 3. *x*. **SQLFetch** можно использовать только для выборки многострочные при вызове в ODBC 3. *x*; Если ODBC 2. Приложение *x* вызывает **SQLFetch**, при этом будет открыт только однострочный курсор. При использовании ODBC 3. Приложение *x* вызывает **SQLFetch** в ODBC 2. драйвер *x* , он возвращает одну строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочные курсоры, прокручиваемые курсоры и обратная совместимость](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: рекомендации по драйверам для обеспечения обратной совместимости.  
  
 Чтобы использовать блочные курсоры, приложение задает размер набора строк, привязывает буферы набора строк (как описано в предыдущем разделе), при необходимости задает атрибуты SQL_ATTR_ROWS_FETCHED_PTR и SQL_ATTR_ROW_STATUS_PTR, а также вызывает **SQLFetch** или **SQLFetchScroll** для выборки блока строк. Приложение может изменить размер набора строк и привязать новые буферы наборов строк (путем вызова **SQLBindCol** или указания смещения привязки) даже после выборки строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; блокировать курсо](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
