---
title: Прокрутка и выборка строк | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c31b5a4d086fec3ac3db6e3eb1bfbd6bf54c8cb3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087356"
---
# <a name="scrolling-and-fetching-rows"></a>Прокрутка и выборка строк
  Чтобы можно было использовать прокручиваемый курсор в приложение ODBC, необходимо выполнить следующие действия.  
  
-   Задать возможности курсора с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Открытие курсора с помощью **SQLExecute** или **SQLExecDirect**.  
  
-   Выполнить прокрутку и выборку строк с помощью **SQLFetch** или [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 Оба **SQLFetch** и **SQLFetchSroll** можно извлекать блоки строк за один раз. Число строк, возвращенных задается с помощью **SQLSetStmtAttr** для параметра SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Приложения ODBC могут использовать **SQLFetch** производить выборку однонаправленный курсор.  
  
 **SQLFetchScroll** используется для прокрутки по курсору. **SQLFetchScroll** поддерживает выборку следующего, предыдущего, первого и последнего набора строк помимо относительной (набора строк, *n* строк от начала текущего набора строк) и абсолютной (набора строк выборки начиная со строки *n*). Если *n* имеет отрицательное значение при абсолютной выборке, то строки отсчитываются с конца результирующего набора. Абсолютная выборка строки -1 означает, что будет возвращен набор строк, начинающийся с последней строки результирующего набора.  
  
 Приложения, использующие **SQLFetchScroll** только для своего блока возможности курсора, таких как отчеты, обычно просматривают результирующий набор только один раз, используя только параметр для получения следующего набора строк. На экране приложений, с другой стороны, можно воспользоваться преимуществами все возможности **SQLFetchScroll**. Если приложение задает размер набора строк на число строк, отображаемых на экране и привязывает буферы экранов к результирующему набору, оно может преобразовывать операции полосы прокрутки непосредственно в вызовы **SQLFetchScroll**.  
  
|Операция полосы прокрутки|Параметр прокрутки SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|На страницу вверх|SQL_FETCH_PRIOR|  
|На страницу вниз|SQL_FETCH_NEXT|  
|На строку вверх|SQL_FETCH_RELATIVE с FetchOffset, равным -1|  
|На строку вниз|SQL_FETCH_RELATIVE с FetchOffset, равным 1|  
|Ползунок вверх|SQL_FETCH_FIRST|  
|Ползунок вниз|SQL_FETCH_LAST|  
|Случайное положение ползунка|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание закладок строк в ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  