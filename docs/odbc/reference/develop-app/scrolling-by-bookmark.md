---
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
ms.openlocfilehash: 454e29abdf848fdf4f4eaae090e7cc326f0048df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304195"
---
# <a name="scrolling-by-bookmark"></a>Прокрутка по закладкам
При выборке строк с помощью **SQLFetchScroll**приложение может использовать закладку в качестве основы для выбора начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Для прокрутки к строке с закладкой приложение вызывает **SQLFetchScroll** с *фетчориентатион* SQL_FETCH_BOOKMARK. Эта операция использует закладку, на которую указывает атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в аргументе *фетчоффсет* вызова **SQLFetchScroll**. Если указано смещение, первая строка возвращаемого набора строк определяется путем добавления числа в аргументе *фетчоффсет* к номеру строки, определяемой закладкой. При использовании с ODBC 2 использование аргумента *фетчоффсет* не поддерживается. драйверы *x* ; Когда приложение вызывает **SQLFetchScroll** в ODBC 2. драйверу *x* с *фетчориентатион* , для которого задано значение SQL_FETCH_BOOKMARK, аргумент *фетчоффсет* должен иметь значение 0.
