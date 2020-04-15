---
title: Использование блок-курсоров (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306795"
---
# <a name="using-block-cursors"></a>Использование блочных курсоров
Поддержка курсоров блоков встроена в ODBC 3. *x*. **S'LFetch** может быть использован только для многофункциональных извлечений при вызове в ODBC 3. *x*; если ODBC 2. *x* приложение вызывает **S'LFetch**, он откроет только один ряд, вперед только курсор. Когда ODBC 3. *x* приложение вызывает **S'LFetch** в ODBC 2. *x* драйвер, он возвращает один ряд, если драйвер не поддерживает **S'LExtendedFetch.** Для получения дополнительной информации в приложении G: Driver Guidelines for Backward Comatibility можно ознакомиться с [Block Cursors, Scrollable Cursors и обратной совместимости.](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)  
  
 Для использования курсоров блоков приложение устанавливает размер рядового набора, связывает буферы рядов (как описано в предыдущем разделе), дополнительно устанавливает атрибуты SQL_ATTR_ROWS_FETCHED_PTR и SQL_ATTR_ROW_STATUS_PTR оператора, а также вызывает **S'LFetch** или **S'LFetchScroll,** чтобы получить блок строк. Приложение может изменить размер рядового набора и связать новые буферы строк (позвонив в **S'LBindCol** или указав смещение связывания) даже после того, как строки были извлечены.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Размер набора строк](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Число строк в выборке и состояние](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [СЗЛГетДата и блок-курсоры; блок курсо](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
