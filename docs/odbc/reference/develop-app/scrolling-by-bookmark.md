---
title: Прокрутка по закладкам | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90ba6ed3a6feb163fbe1eaf39cce14ae501c232e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468380"
---
# <a name="scrolling-by-bookmark"></a>Прокрутка по закладкам
При выборке строк через **SQLFetchScroll**, приложение может использовать закладку в качестве основы для выборки начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Выполнять прокрутку в строке с закладкой, приложение вызывает **SQLFetchScroll** с *FetchOrientation* sql_fetch_bookmark аргумента. Эта операция использует закладку, на которые указывают атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в *FetchOffset* аргумент при вызове для **SQLFetchScroll**. При указании смещения первой строки возвращенного набора строк определяется сложением номер в *FetchOffset* аргумента с номером строки, определяемой закладкой. Такое использование *FetchOffset* аргумент не поддерживается при использовании ODBC 2. *x* драйверы; Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера с *FetchOrientation* присвоено sql_fetch_bookmark аргумента, *FetchOffset* аргумент должен быть задан равным 0.
