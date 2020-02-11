---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2cb829f065421a13d3c7df06c670808bc3d9d77c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064436"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLFetch** в библиотеке курсоров. Общие сведения о **SQLFetch**см. в разделе [функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 При использовании библиотеки курсоров вызовы **SQLFetch** не могут смешиваться с вызовами либо **SQLFetchScroll** , либо **SQLExtendedFetch**.  
  
 Если при вызове **SQLFetch** с параметром SQL_ATTR_ROW_ARRAY_SIZE задано значение больше 1, то библиотека курсоров передаст вызов драйвера. Если драйвер является ODBC 2. драйвер *x* , размер набора строк будет проигнорирован, а вызов **SQLFetch** будет возвращать одну строку данных.  
  
 Если библиотека курсоров используется с ODBC 2. драйвер *x* , смещение привязки (как определено атрибутом SQL_ATTR_ROW_BIND_OFFSET_PTR оператора) не используется при вызове **SQLFetch** .  
  
 При загрузке библиотеки курсоров приложение не может вызвать **SQLFetch** для выборки столбцов закладки. Библиотека курсоров передает вызов **SQLFetch** через драйвер, но вызов функции для включения закладок и привязки столбца закладка перехватывается библиотекой курсоров.
