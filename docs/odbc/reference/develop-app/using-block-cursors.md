---
title: Использование блочных курсоров | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bca1bc96ac1c2582bab592a80d65639944e0766
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915241"
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка блочные курсоры встроено в ODBC 3. *x*. **SQLFetch** может использоваться только для нескольких строк выборки при вызове в ODBC 3. *x*; Если ODBC 2. *x* приложение вызывает **SQLFetch**, он будет открыт только одной строки и однонаправленный курсор. Когда ODBC 3. *x* приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, он возвращает строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Использование блочных курсоров, приложение задает размер набора строк, привязывает буферы строк (как описано в предыдущем разделе), при необходимости задает атрибуты инструкции SQL_ATTR_ROWS_FETCHED_PTR и значения SQL_ATTR_ROW_STATUS_PTR и вызовы **SQLFetch**  или **SQLFetchScroll** для выборки блока строк. Приложение можно изменить размер набора строк и привязать новый буферы строк (путем вызова **SQLBindCol** или указания смещения bind) даже после выбранных строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; курсор блока](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
