---
title: "Использование блочных курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6d38aa5b7d3aeedd09b18941c69b82b2a835b8f6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка блочные курсоры встроено в ODBC 3. *x*. **SQLFetch** может использоваться только для нескольких строк выборки при вызове в ODBC 3. *x*; Если ODBC 2. *x* приложение вызывает **SQLFetch**, он будет открыт только одной строки и однонаправленный курсор. Когда ODBC 3. *x* приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, он возвращает строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Использование блочных курсоров, приложение задает размер набора строк, привязывает буферы строк (как описано в предыдущем разделе), при необходимости задает атрибуты инструкции SQL_ATTR_ROWS_FETCHED_PTR и значения SQL_ATTR_ROW_STATUS_PTR и вызовы **SQLFetch**  или **SQLFetchScroll** для выборки блока строк. Приложение можно изменить размер набора строк и привязать новый буферы строк (путем вызова **SQLBindCol** или указания смещения bind) даже после выбранных строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; курсор блока](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
