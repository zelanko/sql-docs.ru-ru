---
title: СЗЛУТ (Библиотека Курзора) Документы Майкрософт
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
ms.openlocfilehash: bee83ccb5497888b57a45673599af6b92931a704
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298724"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LFetch** в библиотеке курсоров. Для получения общей информации о **S'LFetch,** [см.](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
 При использовании библиотеки курсоров, вызовы в **S'LFetch** не могут быть смешаны с вызовами либо на **S'LFetchScroll,** либо **на S'LExtendedFetch.**  
  
 Если **s'LFetch** вызывается с SQL_ATTR_ROW_ARRAY_SIZE установлен на значение, превышающее 1, библиотека курсора передаст вызов водителю. Если водитель ЯВЛЯЕТСЯ ODBC 2. *x* драйвер, размер рядового набора будет проигнорирован, и вызов в **S'LFetch** вернет одну строку данных.  
  
 Если библиотека курсора используется с ODBC 2. *x* драйвер, смещение связывания (как это определено атрибутом SQL_ATTR_ROW_BIND_OFFSET_PTR оператора) не используется при вызове **S'LFetch.**  
  
 При загрузке библиотеки курсоров приложение не может вызвать **S'LFetch** для получения столбцов закладок. Библиотека курсора передает вызов **в S'LFetch** водителю, но функция вызывает возможность включения закладок и связывания столбца закладок, перехватываемой библиотекой курсора.
