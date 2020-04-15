---
title: SLSetScrollOptions (Библиотека курсора) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304915"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LSetScrollOptions** в библиотеке курсоров. Для получения общей информации о [SQLSetScrollOptions Function](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md) **S'LSetScrollOptions**см.  
  
 Библиотека курсоров поддерживает **S'LSetScrollOptions** только для обратной совместимости; вместо этого приложения должны использовать атрибуты SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE и SQL_ATTR_ROW_ARRAY_SIZE оператора.
