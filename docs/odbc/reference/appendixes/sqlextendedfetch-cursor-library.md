---
title: SQLExtendedFetch (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe39b2d2cbbaf72ce3844c35187040589d1dac58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302065"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLExtendedFetch** в библиотеке курсоров. Общие сведения о **SQLExtendedFetch**см. в разделе [функция SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Библиотека курсоров реализует **SQLExtendedFetch** путем многократного вызова **SQLFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов **SQLExtendedFetch** с *фетчориентатион* SQL_FETCH_BOOKMARK.  
  
 При использовании библиотеки курсоров вызовы **SQLExtendedFetch** не могут смешиваться с вызовами либо **SQLFetchScroll** , либо **SQLFetch**.
