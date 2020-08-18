---
description: SQLSetScrollOptions (библиотека курсоров)
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
ms.openlocfilehash: f40e5cd3b62b91b1b0b832b9b8fcf36101487c10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386560"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLSetScrollOptions** в библиотеке курсоров. Общие сведения о **SQLSetScrollOptions**см. в разделе [функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Библиотека курсоров поддерживает **SQLSetScrollOptions** только для обеспечения обратной совместимости. приложения должны использовать вместо них атрибуты SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE и SQL_ATTR_ROW_ARRAY_SIZE.
