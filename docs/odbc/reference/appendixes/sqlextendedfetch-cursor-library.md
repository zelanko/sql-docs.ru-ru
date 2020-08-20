---
description: SQLExtendedFetch (библиотека курсоров)
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
ms.openlocfilehash: ab7d091dc6cee3630b5ed9b8bf3a3a479c0613e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466016"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLExtendedFetch** в библиотеке курсоров. Общие сведения о **SQLExtendedFetch**см. в разделе [функция SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Библиотека курсоров реализует **SQLExtendedFetch** путем многократного вызова **SQLFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов **SQLExtendedFetch** с *фетчориентатион* SQL_FETCH_BOOKMARK.  
  
 При использовании библиотеки курсоров вызовы **SQLExtendedFetch** не могут смешиваться с вызовами либо **SQLFetchScroll** , либо **SQLFetch**.
