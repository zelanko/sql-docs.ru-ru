---
title: Прокрутка по закладке Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304195"
---
# <a name="scrolling-by-bookmark"></a>Прокрутка по закладкам
При получении строк с **помощью S'LFetchScroll**приложение может использовать закладку в качестве основы для выбора стартового ряда. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Чтобы прокрутить строку с закладкой, приложение вызывает **S'LFetchScroll** с *SQL_FETCH_BOOKMARK.* В этой операции используется закладка, на которую указывает атрибут SQL_ATTR_FETCH_BOOKMARK_PTR оператора. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать компенсацию за эту операцию в аргументе *FetchOffset* вызова на **S'LFetchScroll.** При указании смещения первый ряд возвращенного набора строк определяется путем добавления числа в аргументе *FetchOffset* к числу строки, идентифицированной закладкой. Это использование аргумента *FetchOffset* не поддерживается при использовании с ODBC 2. *x* драйверы; когда приложение вызывает **S'LFetchScroll** в ODBC 2. *x* драйвер с *FetchOrientation* установлен SQL_FETCH_BOOKMARK, *Аргумент FetchOffset* должны быть установлены на 0.
