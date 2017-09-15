---
title: "SQLFetch (библиотека курсоров) | Документы Microsoft"
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
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1e5cabca53c503e2cd0c12147248b11da84ed157
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLFetch** функции в библиотеку курсоров. Общие сведения о **SQLFetch**, в разделе [SQLFetch, функция](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 При использовании библиотеки курсоров вызовы **SQLFetch** невозможно комбинировать с вызовами либо **SQLFetchScroll** или **SQLExtendedFetch**.  
  
 Если **SQLFetch** вызывается с SQL_ATTR_ROW_ARRAY_SIZE присвоено значение больше 1, библиотеку курсоров передаст вызов к драйверу. Если драйвер ODBC 2. *x* драйвера, размер набора строк будут игнорироваться и вызов **SQLFetch** возвращает одну строку данных.  
  
 Если используется библиотека курсоров ODBC 2. *x* драйвер, привязка смещения (как определено атрибутом инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR) не используется, когда **SQLFetch** вызывается.  
  
 При загрузке библиотеки курсоров, приложение не может вызвать **SQLFetch** для выборки столбцов закладок. Библиотека курсоров вызов передается **SQLFetch** через драйвер, но функция вызовы для включения закладки и привязать столбец закладки перехватываются библиотеку курсоров.
