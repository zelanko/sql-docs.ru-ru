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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3fd7d02d74b0e19d91871c5df7c9c5915d028f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064454"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLExtendedFetch** в библиотеке курсоров. Общие сведения о **SQLExtendedFetch**см. в разделе [функция SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Библиотека курсоров реализует **SQLExtendedFetch** путем многократного вызова **SQLFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов **SQLExtendedFetch** с *фетчориентатион* SQL_FETCH_BOOKMARK.  
  
 При использовании библиотеки курсоров вызовы **SQLExtendedFetch** не могут смешиваться с вызовами либо **SQLFetchScroll** , либо **SQLFetch**.
