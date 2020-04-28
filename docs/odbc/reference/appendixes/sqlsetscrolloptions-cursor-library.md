---
title: SQLSetScrollOptions (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0099ca5e9bcb3aefdd86e0132f52d110ab64e8a4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304915"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLSetScrollOptions** в библиотеке курсоров. Общие сведения о **SQLSetScrollOptions**см. в разделе [функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Библиотека курсоров поддерживает **SQLSetScrollOptions** только для обеспечения обратной совместимости. приложения должны использовать вместо них атрибуты SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE и SQL_ATTR_ROW_ARRAY_SIZE.
