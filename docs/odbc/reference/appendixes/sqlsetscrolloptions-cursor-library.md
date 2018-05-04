---
title: SQLSetScrollOptions (библиотека курсоров) | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f3529788d2fb8e0b81934473f721cd9bb6ed803
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetScrollOptions** функции в библиотеку курсоров. Общие сведения о **SQLSetScrollOptions**, в разделе [SQLSetScrollOptions функция](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Библиотека курсоров поддерживает **SQLSetScrollOptions** только для обратной совместимости; приложения должны использовать вместо этого атрибуты инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE и SQL_ATTR_ROW_ARRAY_SIZE.
