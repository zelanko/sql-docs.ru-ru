---
title: "Использование блочных курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51f02b5b243286a650897fecdcac5d8778bd3f40
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка блочные курсоры встроено в ODBC 3. *x*. **SQLFetch** может использоваться только для нескольких строк выборки при вызове в ODBC 3.* x*; Если ODBC 2.* x* приложение вызывает **SQLFetch**, он будет открыт только одной строки и однонаправленный курсор. Когда ODBC 3. *x* приложение вызывает **SQLFetch** в ODBC 2.* x* драйвера, он возвращает строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Использование блочных курсоров, приложение задает размер набора строк, привязывает буферы строк (как описано в предыдущем разделе), при необходимости задает атрибуты инструкции SQL_ATTR_ROWS_FETCHED_PTR и значения SQL_ATTR_ROW_STATUS_PTR и вызовы **SQLFetch ** или **SQLFetchScroll** для выборки блока строк. Приложение можно изменить размер набора строк и привязать новый буферы строк (путем вызова **SQLBindCol** или указания смещения bind) даже после выбранных строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк, загружаемых и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; курсор блока](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
