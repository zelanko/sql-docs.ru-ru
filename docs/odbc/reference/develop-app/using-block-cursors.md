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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 388995cd5cb8a711d72533685c14088a7e908475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758942"
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка для блочных курсоров встроена в ODBC 3. *x*. **SQLFetch** может использоваться только для нескольких строк выборки, при вызове в ODBC 3. *x*; Если ODBC 2. *x* приложение вызывает **SQLFetch**, он будет открыт только одной строкой и однопроходный курсор. Когда ODBC 3. *x* приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, он возвращает строку, если драйвер не поддерживает **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочные курсоры, Прокручиваемые курсоры и обратная совместимость](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Использование блочных курсоров, приложение задает размер набора строк, привязывает буферы строк (как описано в предыдущем разделе), при необходимости задает атрибуты инструкции SQL_ATTR_ROWS_FETCHED_PTR и значения SQL_ATTR_ROW_STATUS_PTR и вызовы **SQLFetch**  или **SQLFetchScroll** для получения блока строк. Приложения можно изменить размер набора строк и привязать новый буферы строк (путем вызова **SQLBindCol** или указания смещения привязки) даже в том случае, после выбранных строк.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData и блочные курсоры; блокировать курсор](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
