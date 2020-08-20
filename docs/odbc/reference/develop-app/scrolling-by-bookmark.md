---
description: Прокрутка по закладкам
title: Прокрутка по закладке | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 52ef0813f3f9fd3f2d139a2549000c629943109e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476476"
---
# <a name="scrolling-by-bookmark"></a>Прокрутка по закладкам
При выборке строк с помощью **SQLFetchScroll**приложение может использовать закладку в качестве основы для выбора начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Для прокрутки к строке с закладкой приложение вызывает **SQLFetchScroll** с *фетчориентатион* SQL_FETCH_BOOKMARK. Эта операция использует закладку, на которую указывает атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в аргументе *фетчоффсет* вызова **SQLFetchScroll**. Если указано смещение, первая строка возвращаемого набора строк определяется путем добавления числа в аргументе *фетчоффсет* к номеру строки, определяемой закладкой. При использовании с ODBC 2 использование аргумента *фетчоффсет* не поддерживается. драйверы *x* ; Когда приложение вызывает **SQLFetchScroll** в ODBC 2. драйверу *x* с *фетчориентатион* , для которого задано значение SQL_FETCH_BOOKMARK, аргумент *фетчоффсет* должен иметь значение 0.
