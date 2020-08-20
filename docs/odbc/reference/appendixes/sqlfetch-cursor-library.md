---
description: SQLFetch (библиотека курсоров)
title: SQLFetch (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce9da3c0c5b95be4336c58896b17b6ba5daf6443
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466006"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLFetch** в библиотеке курсоров. Общие сведения о **SQLFetch**см. в разделе [функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 При использовании библиотеки курсоров вызовы **SQLFetch** не могут смешиваться с вызовами либо **SQLFetchScroll** , либо **SQLExtendedFetch**.  
  
 Если при вызове **SQLFetch** с параметром SQL_ATTR_ROW_ARRAY_SIZE задано значение больше 1, то библиотека курсоров передаст вызов драйвера. Если драйвер является ODBC 2. драйвер *x* , размер набора строк будет проигнорирован, а вызов **SQLFetch** будет возвращать одну строку данных.  
  
 Если библиотека курсоров используется с ODBC 2. драйвер *x* , смещение привязки (как определено атрибутом SQL_ATTR_ROW_BIND_OFFSET_PTR оператора) не используется при вызове **SQLFetch** .  
  
 При загрузке библиотеки курсоров приложение не может вызвать **SQLFetch** для выборки столбцов закладки. Библиотека курсоров передает вызов **SQLFetch** через драйвер, но вызов функции для включения закладок и привязки столбца закладка перехватывается библиотекой курсоров.
