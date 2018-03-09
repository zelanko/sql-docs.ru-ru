---
title: "Типы Прокручиваемый курсор | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85de42e271f937c7a3de1aacba918bb43ea463d4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="scrollable-cursor-types"></a>Типы Прокручиваемый курсор
Существует четыре типа прокрутки курсоров статические, динамические, управляемые набором ключей и смешанного. Статические курсоры обнаружение незначительных изменений, но недорогих относительно реализации. Динамические курсоры обнаруживают все изменения, но высокая стоимость реализации. Курсоры, управляемые набором ключей и смешанного находиться, обнаруживая большинство изменений, но с меньшими затратами, чем динамические курсоры.  
  
 Следующие термины используются для определения характеристик каждого типа Прокручиваемый курсор:  
  
-   **Владельцем обновления, удаления и вставки.** Обновления, удаления и вставки, осуществленные через курсор, либо с помощью вызова **SQLBulkOperations** или **SQLSetPos** или позиционированные с инструкцией обновления или удаления.  
  
-   **Другие обновляет, удаляет и вставляет.** Обновления, удаления и вставки, не выполненные курсора, в том числе и для других операций в той же транзакции, произведенные через другие транзакции и сделанные другими приложениями.  
  
-   **Членство.** Набор строк в результирующем наборе.  
  
-   **Порядок.** Порядок, в котором строки возвращаются курсором.  
  
-   **Значения.** Значения в каждой строке в результирующем наборе.  
  
 Сведения о способах обновления, удаления и вставки данных см. в разделе [Обзор обновления данных](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Статические курсоры (ODBC)](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Динамические курсоры ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Управляемые ключевым набором курсоры](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Смешанные курсоры](../../../odbc/reference/develop-app/mixed-cursors.md)
