---
title: Прокрутка по закладке | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823929a98b3fc7b016f8bc1dc3fa1c2ed982b9c0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="scrolling-by-bookmark"></a>Прокрутка по закладке
При выборке строк через **SQLFetchScroll**, приложение может использовать закладку в качестве основы для выборки начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Для прокрутки в строке с закладкой, приложение вызывает **SQLFetchScroll** с *FetchOrientation* из SQL_FETCH_BOOKMARK. Эта операция использует закладку, на который указывает атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в *FetchOffset* аргумент при вызове для **SQLFetchScroll**. Если указано смещение первой строки возвращенного набора строк определяется путем добавления номера в *FetchOffset* аргумента номер строки, определяемой закладкой. Такое использование *FetchOffset* аргумент не поддерживается при использовании ODBC 2. *x* драйверы; Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера с *FetchOrientation* значение SQL_FETCH_BOOKMARK, *FetchOffset* аргумента должно быть равно 0.
