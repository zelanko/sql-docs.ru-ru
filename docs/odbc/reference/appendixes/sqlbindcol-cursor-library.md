---
title: SQLBindCol (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eeca90b8de3ce65e8da68d6aabac89b2181ed047
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLBindCol** функции в библиотеку курсоров. Общие сведения о **SQLBindCol**, в разделе [SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Приложение выделяет один или несколько буферов для библиотеки курсоров для возврата в текущем наборе строк. Он вызывает **SQLBindCol** один или несколько раз для привязки к результирующему набору эти буферы.  
  
 Приложение может вызвать **SQLBindCol** повторно привязать результирующий набор столбцов после вызова **SQLExtendedFetch**, **SQLFetch**, или **SQLFetchScroll**, при условии, что тип данных C, размер столбца и десятичные цифры из присоединенного столбца остаются неизменными. Приложение не нужно закрыть курсор, чтобы привязать столбцы к различным адресам.  
  
 Библиотека курсоров поддерживает настройку атрибута инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR для использования привязки смещения. (**SQLBindCol** не должен вызываться для этой привязки происходят.) Если использование библиотеки курсоров ODBC 3*.x* драйвера, смещение привязки не используется, когда **SQLFetch** вызывается. Смещение привязки используется в том случае, если **SQLFetch** вызывается при использовании библиотеки курсоров ODBC 2. *x* драйвер из-за **SQLFetch** сопоставляется **SQLExtendedFetch**.  
  
 Библиотека курсоров поддерживает вызов метода **SQLBindCol** для привязки столбца закладки.  
  
 При работе с ODBC 2. *x* драйвер, библиотеку курсоров возвращает SQLSTATE HY090 (Недопустимая длина строки или буфера) при **SQLBindCol** вызывается для настройки размера буфера для столбца закладки значение не равно 4. При работе с ODBC 3*.x* драйверов, библиотеку курсоров обеспечивает буфера быть любого размера.
