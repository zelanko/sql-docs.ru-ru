---
title: SQLFetch (библиотека курсоров) | Документы Microsoft
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
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55ccc293855328690e654dfce0ac789e9c8ed3ae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLFetch** функции в библиотеку курсоров. Общие сведения о **SQLFetch**, в разделе [SQLFetch, функция](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 При использовании библиотеки курсоров вызовы **SQLFetch** невозможно комбинировать с вызовами либо **SQLFetchScroll** или **SQLExtendedFetch**.  
  
 Если **SQLFetch** вызывается с SQL_ATTR_ROW_ARRAY_SIZE присвоено значение больше 1, библиотеку курсоров передаст вызов к драйверу. Если драйвер ODBC 2. *x* драйвера, размер набора строк будут игнорироваться и вызов **SQLFetch** возвращает одну строку данных.  
  
 Если используется библиотека курсоров ODBC 2. *x* драйвер, привязка смещения (как определено атрибутом инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR) не используется, когда **SQLFetch** вызывается.  
  
 При загрузке библиотеки курсоров, приложение не может вызвать **SQLFetch** для выборки столбцов закладок. Библиотека курсоров вызов передается **SQLFetch** через драйвер, но функция вызовы для включения закладки и привязать столбец закладки перехватываются библиотеку курсоров.
